# Phase 5 — Privileged Access

**Status:** Planned

**Estimated effort:** 3–5 hours

## Objective

Reduce standing privilege and separate daily user activity from administrative work.

## Planned controls

- Create a separate named administrative account for the IAM administrator.
- Keep the ordinary user account out of privileged groups.
- Delegate a limited help-desk task, such as resetting passwords within a selected OU.
- Validate that the delegated account can perform the approved task but cannot perform domain-wide administration.
- Evaluate Windows LAPS for local administrator password management if supported by the lab systems.
- Review privileged group membership and document exceptions.

## Required testing

Test both permitted and prohibited administrative actions. Capture the effective group memberships, delegation scope, and evidence that an ordinary account lacks administrative rights.

