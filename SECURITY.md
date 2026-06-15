# Security & Responsible Use Policy

Fortify is a **defensive** security tool. It exists to help people harden systems
they own or are authorized to test, and to verify that hardening. This document
covers responsible use and how to report issues.

## Acceptable use

Use Fortify (and especially its red-team swarm) **only** against:

- code you own or maintain, and
- running systems on `localhost` / loopback, or a staging environment you have
  explicitly confirmed you own or are authorized to test.

Before any active testing, the skill walks the
[authorization checklist](.claude/skills/fortify/templates/authorization-checklist.md).
Active testing is **non-destructive by default**: no data deletion, no persistent
denial of service, no lockout of real accounts, no irreversible changes.

## Prohibited use

Do **not** use this project to attack, scan, or probe:

- systems, domains, or IP addresses you do not own or are not authorized to test;
- production systems or real user data without explicit written authorization;
- third parties, for social engineering, or for any unlawful purpose.

You are responsible for complying with all applicable laws and for obtaining
authorization. Unauthorized access to computer systems is illegal in most
jurisdictions.

## Handling of secrets and sensitive data

If Fortify discovers credentials, keys, tokens, or PII, it reports only their
**type and location** — never the value — and recommends rotation, treating any
exposed secret as compromised. Generated reports must not be committed with live
secrets or real PII.

## Reporting a vulnerability in this project

If you find a security issue in Fortify itself, please open a private report via
GitHub Security Advisories on this repository, or contact the maintainer rather
than filing a public issue. Include reproduction steps and impact. We aim to
acknowledge reports promptly.

## Disclaimer

Fortify produces advisory evidence and gap analysis toward security frameworks —
it is **not** a certification, and no security tier guarantees invulnerability.
Always interpret results with the stated residual risk in mind.
