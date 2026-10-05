# Company Profile and Business Problem

## Organization

**Apex Financial Group** is a fictional financial-services organization with approximately 500 employees across Human Resources, Finance, Information Technology, Sales, and Executive functions.

## Business problem

The organization has outgrown informal identity administration. Access decisions are inconsistent, onboarding and offboarding rely on manual steps, privileged access is not sufficiently separated, and audit evidence is difficult to reproduce.

These weaknesses create practical risks:

- Users may receive more access than their role requires.
- Access may remain after a role change or departure.
- Direct permission assignments can become difficult to trace.
- Administrative activity may be performed from ordinary user accounts.
- Security teams may be unable to prove that a control works.

## Target state

The project builds a small but defensible IAM operating model:

- Centralized identities in Active Directory
- Department and role-based security groups
- Group-based resource authorization
- Repeatable joiner, mover, and leaver processes
- Authentication and account-policy controls
- Separate privileged access
- Periodic access reviews and audit evidence

## Scope boundary

This is a portfolio lab, not a production deployment or formal compliance assessment. The design reflects common control themes found in regulated environments, but it does not claim certification or compliance with any specific framework.

