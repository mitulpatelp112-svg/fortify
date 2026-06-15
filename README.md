<div align="center">

# 🛡️ Fortify

**A universal cybersecurity skill for Claude Code that hardens any project — then proves it by attacking it.**

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![OWASP](https://img.shields.io/badge/maps%20to-OWASP%20Top%2010-000000.svg)](.claude/skills/fortify/references/compliance-mapping.md)
[![Frameworks](https://img.shields.io/badge/compliance-NIST%20%7C%20CIS%20%7C%20SOC2%20%7C%20ISO27001%20%7C%20PCI--DSS-blue.svg)](.claude/skills/fortify/references/compliance-mapping.md)
[![Defensive](https://img.shields.io/badge/use-defensive%20%26%20authorized%20only-success.svg)](.claude/skills/fortify/templates/authorization-checklist.md)

</div>

---

## The problem it solves

Most teams ship code without ever asking the two questions an attacker asks first:
**"What's exposed?"** and **"What happens if I poke it?"** Security reviews are
expensive, inconsistent, and usually happen too late — if at all. Findings come
as a PDF nobody actions, with no proof the fix actually closed the hole.

**Fortify** turns security from a one-off audit into a repeatable, project-agnostic
workflow you can run on *any* codebase:

1. It **maps your attack surface** — exactly what is accessible vs. protected, and to whom.
2. It **audits** against a comprehensive attack catalog (OWASP Top 10 and well beyond).
3. It **hardens** the code (report-first, fix-on-approval), mapped to the compliance frameworks you care about.
4. It **proves the hardening holds** by unleashing a swarm of *authorized* attacker agents against your own running app.
5. It **reports** in Markdown + JSON + SARIF, with a before/after and an honest residual-risk statement.

It works on web apps, REST/GraphQL APIs, mobile, and desktop projects — it
detects the stack itself, so there's nothing to configure to get started.

> **Defensive by design.** Active testing only runs against systems you own or are
> explicitly authorized to test (localhost / confirmed staging), is non-destructive
> by default, and never echoes secrets or live PII.

## Table of contents
- [Quick start](#quick-start)
- [Install into your own project](#install-into-your-own-project)
- [How it works](#how-it-works)
- [Security tiers](#security-tiers)
- [Usage examples](#usage-examples)
- [What you get out](#what-you-get-out)
- [Repository layout](#repository-layout)
- [Safety & ethics](#safety--ethics)
- [Repository metadata](#repository-metadata)
- [License](#license)

## Quick start

Try it against the bundled intentionally-vulnerable demo app:

```bash
git clone https://github.com/mitulpatelp112-svg/cybersecurity-.git
cd cybersecurity-/demo-app
npm install
npm start          # vulnerable app on http://localhost:3000 (localhost only!)
```

Then, in Claude Code (this repo already ships the skill), run:

```
/fortify
```

Fortify will confirm authorization, detect the Express app, ask which security
tier you want, audit `demo-app/src/`, show you the findings, harden on your
approval, then attack `localhost:3000` to confirm the fixes hold.

## Install into your own project

```bash
# from a clone of this repo:
.claude/skills/fortify/scripts/install.sh /path/to/your/project
```

This copies the skill to `your-project/.claude/skills/fortify/`. Open that
project in Claude Code and run `/fortify`.

## How it works

Fortify runs as a phased workflow (see [`SKILL.md`](.claude/skills/fortify/SKILL.md)):

| Phase | What happens |
|-------|--------------|
| **0 · Authorize** | Confirms you own the target; locks live testing to localhost / confirmed staging. |
| **1 · Discover** | Detects stack, enumerates entry points, drafts the *Accessibility Map*. |
| **2 · Choose level** | You pick a tier + fix policy + compliance frameworks (asked interactively). |
| **3 · Audit & threat-model** | Walks the code against the [attack catalog](.claude/skills/fortify/references/attack-catalog.md), STRIDE per entry point. |
| **4 · Report (gate)** | Severity-ranked findings + remediation; you decide what to fix. |
| **5 · Harden** | Applies idiomatic fixes on approval, re-runs your tests/build. |
| **6 · Red-team swarm** | Parallel specialized attacker agents safely attack the authorized target. |
| **7 · Final report** | Markdown + JSON + SARIF, updated Accessibility Map, residual risk, optional CI gate. |

## Security tiers

You choose how deep to go per run (full details in
[`security-tiers.md`](.claude/skills/fortify/references/security-tiers.md)):

| Tier | For | Adds |
|------|-----|------|
| **Basic** | prototypes, internal tools | OWASP essentials, parameterized queries, no secrets in source, TLS |
| **Standard** | most public apps/APIs | full OWASP Top 10 + API Top 10, authN/Z hardening, headers, CSRF, rate limits |
| **Hardened** | sensitive/regulated data | threat model, supply-chain & secrets mgmt, crypto review, CIS infra hardening |
| **Maximum** | high-value / defense-grade | zero-trust, assume-breach, DoS resilience, advanced/APT scenarios, detection & response |

> "High-end security that nobody can access" is an **aspiration, not a guarantee**.
> Maximum tier means defense-in-depth that makes attacks expensive, slow, and loud —
> and ensures you detect and recover. Fortify always states residual risk.

## Usage examples

**Audit only, no changes:**
> "Run fortify on this repo at the Standard tier, report-only — don't change anything yet."

**Harden a specific concern:**
> "Use fortify to find and fix all injection and access-control issues, then prove the fixes with the red-team swarm against localhost:8080."

**Ship-readiness check:**
> "Is this safe to ship? Run fortify at Hardened tier, map it to SOC 2 and OWASP ASVS, and tell me what's still exposed."

**Add a CI gate:**
> "Run fortify, then install the security CI workflow so PRs get scanned automatically."

A full annotated walkthrough — including a sample findings report and
accessibility map for the demo app — lives in
[`docs/EXAMPLE-RUN.md`](docs/EXAMPLE-RUN.md).

## What you get out

Each run writes to `security/` in the target project:

- **`report.md`** — executive summary + technical appendix + accessibility map.
- **`findings.json`** — machine-readable, conforming to [`findings.schema.json`](.claude/skills/fortify/templates/findings.schema.json).
- **`findings.sarif`** — SARIF 2.1.0 so findings show inline on GitHub PRs (code scanning).

Plus an **Accessibility Map** answering, for every surface: *who can reach this,
with what auth, and is that intended?*

## Repository layout

```
.
├── .claude/skills/fortify/        # the portable Fortify skill
│   ├── SKILL.md                   # phased orchestrator
│   ├── references/                # attack catalog, tiers, compliance, playbooks, reporting
│   ├── agents/red-team-swarm.md   # authorized attacker-agent orchestration
│   ├── templates/                 # auth checklist, findings schema, report, CI workflow
│   └── scripts/install.sh         # copy Fortify into any project
├── demo-app/                      # intentionally-vulnerable app + hardened version
├── docs/EXAMPLE-RUN.md            # annotated end-to-end walkthrough
├── SECURITY.md                    # responsible-use & disclosure policy
└── LICENSE                        # MIT
```

## Safety & ethics

Fortify is a **defensive** tool. Read and follow
[`authorization-checklist.md`](.claude/skills/fortify/templates/authorization-checklist.md)
before any active testing. In short: only test what you own or are authorized to
test; non-destructive by default; never exfiltrate or log secrets/PII; reports
are advisory evidence and gap analysis, **not** a certification, and no tier
guarantees invulnerability. See [`SECURITY.md`](SECURITY.md).

## Repository metadata

Suggested values to set in **GitHub → repo settings** (the API for these isn't
available to the skill, so set them once by hand):

- **Description:**
  > Universal Claude Code security skill: audits, hardens, and authorized-attack-tests any project (web/API/mobile/desktop) against OWASP, NIST, CIS, SOC 2 & PCI-DSS — then proves the fixes hold with a red-team agent swarm.
- **Topics:**
  `security` · `cybersecurity` · `pentest` · `penetration-testing` · `appsec` ·
  `owasp` · `owasp-top-10` · `security-hardening` · `red-team` · `sast` ·
  `devsecops` · `claude-code` · `ai-security` · `vulnerability-scanner` ·
  `threat-modeling` · `nist` · `compliance`

## License

[MIT](LICENSE) © 2026 Mitul Patel
