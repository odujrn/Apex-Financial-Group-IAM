# Phase 4 — Authentication and Group Policy Hardening

**Status:** Planned

**Estimated effort:** 3–5 hours

## Objective

Strengthen domain authentication and endpoint policy through controlled Group Policy changes.

## Planned controls

- Domain password policy appropriate for the lab scenario
- Account lockout threshold and reset duration
- Advanced audit policy for account management and logon activity
- Screen-lock policy for domain workstations
- Restricted local administrative membership where feasible
- A documented rollback plan for each GPO

## Validation

- Use `gpresult` or Resultant Set of Policy to prove application.
- Test one controlled lockout and recovery scenario.
- Confirm required events appear in Event Viewer.
- Verify the policy does not unintentionally affect administrative recovery access.

The phase should explain the tradeoff between stronger controls and account lockout or operational risk rather than presenting a single setting as universally correct.

