# Phase 3 — Identity Lifecycle Automation

**Status:** Planned

**Estimated effort:** 4–6 hours

## Objective

Create repeatable PowerShell workflows for joiners, movers, and leavers while preserving approval and audit information.

## Planned deliverables

- A CSV schema for approved identity requests
- A provisioning script that validates input before creating an account
- A mover workflow that changes department OU and role-group membership
- A leaver workflow that disables the account, removes access groups, records the action, and moves the account to a disabled-users OU
- Error handling, `-WhatIf` support where practical, and transaction logging
- Positive and failure-path tests using fictional identities

## Security controls

- No plaintext passwords in scripts or CSV files.
- Scripts must not infer privileged access from department alone.
- Every group change must be logged.
- Leaver processing must disable sign-in before cleanup.
- A script is not considered complete until it has been tested in the lab.

## Evidence standard

Capture the approved input, safe execution output, before/after directory state, and the generated log. Redact credentials and personal identifiers.

