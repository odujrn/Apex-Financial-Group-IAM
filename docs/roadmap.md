# Project Roadmap

The roadmap is intentionally limited to six core phases. This makes the project achievable while still showing progression from administration to IAM security engineering.

| Phase | Outcome | Difficulty | Estimated effort | Completion evidence |
|---|---|---:|---:|---|
| 1. Identity Foundation | Working AD domain, OUs, users, groups, domain client | Beginner | 4–6 hours | Domain, user, group, client, and logon validation |
| 2. RBAC and File Access | Department data protected with AGDLP-style groups | Beginner–Intermediate | 3–5 hours | ACLs plus permitted and denied access tests |
| 3. Lifecycle Automation | Repeatable joiner, mover, leaver workflows | Intermediate | 4–6 hours | Tested scripts, before/after evidence, error handling |
| 4. Authentication Hardening | Password, lockout, audit, and workstation policies | Intermediate | 3–5 hours | GPO results and controlled policy tests |
| 5. Privileged Access | Separate admin identity and reduced standing privilege | Intermediate | 3–5 hours | Delegation and privilege validation |
| 6. Governance and Audit | Access review, change records, findings, final audit pack | Intermediate | 3–4 hours | Review matrix, risk register, and final report |

## Completion standard

A phase is complete only when:

- The configuration exists.
- Expected access succeeds.
- Prohibited access fails.
- The result is captured without exposing secrets.
- The README explains the result and any limitation.

## Optional cloud extension

Microsoft Entra integration, synchronization, SSO, MFA, and Conditional Access are kept outside the core roadmap. They should begin only when an appropriate tenant, licensing, administrative permissions, and a rollback plan are available. See [Optional Cloud Extension](../optional-cloud-extension/README.md).

