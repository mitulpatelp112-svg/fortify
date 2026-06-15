# Example Run — Fortify against the demo app

This is an annotated, end-to-end walkthrough of running Fortify against the
bundled [`demo-app/`](../demo-app), showing what each phase looks like and what
the outputs contain. Use it to understand the workflow before pointing Fortify
at your own project.

> The demo app is **intentionally vulnerable** and bound to `127.0.0.1`. Run it on
> localhost only; never deploy it.

---

## 0. Start the target and invoke the skill

```bash
cd demo-app
npm install
npm start            # vulnerable app on http://localhost:3000
```

In Claude Code:

```
/fortify
```

## Phase 0 — Authorization

Fortify confirms you own/are authorized to test the project and that live testing
is limited to `localhost`. Because the demo runs on `127.0.0.1:3000`, this passes
immediately. (For a real app it would also ask for any staging URL and confirm
you're authorized to test it.)

## Phase 1 — Discovery & accessibility map (draft)

Fortify detects: **Node.js + Express**, `better-sqlite3`, an in-memory DB, and
enumerates the routes in `src/server.js`. First-draft accessibility map:

| Surface | Exposure | AuthN | AuthZ | Intended? |
|---|---|---|---|---|
| `POST /login` | public | none | n/a | ⚠ no rate limit |
| `GET /search` | public | none | n/a | ⚠ reflects input |
| `GET /notes/:id` | public | **none** | **none** | ❌ should be owner-only |
| `GET /admin/users` | public | **none** | **none** | ❌ should be admin-only |

## Phase 2 — Choose tier

You pick, for example, **Standard** tier, **report-first** fixing, and map to
**OWASP ASVS + Top 10**. (Higher tiers pull in supply-chain, crypto, infra, and
the advanced agent squad.)

## Phase 3–4 — Audit & findings report

Fortify walks `src/server.js` against the attack catalog and produces a report.
Excerpt of `security/report.md`:

```markdown
## Executive summary
Posture: NOT ship-ready (Standard tier). 3 critical, 2 high, 3 medium, 1 low.
Top risks: (1) SQL injection on /login allows auth bypass and data theft.
(2) Any unauthenticated user can read every user's private notes (IDOR) and the
admin user list including password hashes. (3) Passwords are stored as unsalted
SHA1 and a live API key is committed to source.

### F-001 — SQL injection in /login
- Severity: CRITICAL · Confidence: confirmed · Status: open
- Attack class: A. Injection (A03)
- Location: demo-app/src/server.js:34 (login query)
- Description: `username` is concatenated into the SQL string, so
  `' OR '1'='1' --` bypasses authentication entirely.
- Impact: full auth bypass; arbitrary data read/modification.
- Evidence (safe PoC): POST /login {"username":"' OR '1'='1' --","password":"x"}
  returned {"ok":true}.
- Remediation: use a parameterized query (`WHERE username = ?`) and verify the
  password hash separately.
- Compliance: OWASP A03 (gap); ASVS V5.3 (gap); NIST SI-10 (gap).

### F-002 — Broken access control / IDOR on /notes/:id and /admin/users
- Severity: CRITICAL · ... ownership/role checks missing; admin route also
  over-exposes password hashes (A01 / API1 BOLA / API5 BFLA).

### F-003 — Hardcoded secret in source
- Severity: HIGH · location: demo-app/src/server.js:13 (API key). Reported by
  type/location only — value redacted. Remediation: move to env/secret manager
  and ROTATE the key (treat as compromised).

### F-004 — Weak password hashing (SHA1, unsalted)  [HIGH]
### F-005 — Reflected XSS on /search                [HIGH]
### F-006 — No security headers (CSP/HSTS/...)        [MEDIUM]
### F-007 — Verbose error handler leaks stack traces [MEDIUM]
### F-008 — No rate limiting on /login               [MEDIUM]
```

You review and approve the fixes.

## Phase 5 — Harden

Fortify applies the remediations (the result is captured in
[`demo-app/hardened/server.js`](../demo-app/hardened/server.js)): parameterized
queries, argon2id hashing, ownership + role checks, output encoding, `helmet`
security headers, a login rate limiter, generic error handling, and the secret
moved to `process.env`. It then re-runs the build to confirm nothing broke.

## Phase 6 — Red-team swarm (authorized)

Against `localhost:3000` (now the hardened build), Fortify spawns the core squad
in parallel — injection, auth/session, access-control, config/headers, recon —
and records both what they could and **could not** do:

```
[injection]      ' OR '1'='1' on /login  -> BLOCKED (parameterized)         ✅
[access-control] /notes/2 as alice        -> 403 forbidden (ownership check) ✅
[access-control] /admin/users as user      -> 403 forbidden (role check)      ✅
[config]         security headers present  -> CSP/HSTS/nosniff/frame-ancestors ✅
[auth]           6 rapid logins            -> 429 after 5 (rate limited)       ✅
```

Confirmed-blocked attempts become the "what is NOT accessible" evidence in the
final Accessibility Map.

## Phase 7 — Final report

Updated accessibility map (after hardening):

```
### Authenticated only
- GET /notes/:id   — Bearer token required — own notes only (ownership-checked) — OK

### Role-restricted
- GET /admin/users — token + role=admin — no hash exposure — OK

### Correctly NOT accessible
- SQL injection on /login — neutralized by parameterization
- Cross-account note access — blocked by ownership check
- Stack traces — no longer leaked (generic 500)
```

Outputs written: `security/report.md`, `security/findings.json`,
`security/findings.sarif`. If you opted in, the
[`ci-workflow.yml`](../.claude/skills/fortify/templates/ci-workflow.yml) gate is
installed at `.github/workflows/security.yml` so every PR is re-scanned.

**Residual risk (Standard tier):** covers the OWASP Top 10 for this app surface;
does not include supply-chain hardening, infra/IaC review, or advanced/APT
scenarios — choose Hardened/Maximum for those.
