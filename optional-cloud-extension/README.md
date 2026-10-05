# Optional Microsoft Entra Hybrid Extension

**Status:** Optional and not started

This extension is intentionally outside the six-phase core project. Begin it only when the required tenant access and licensing are confirmed.

## Possible scope

- Synchronize selected lab identities to Microsoft Entra ID
- Validate source anchors and UPN design
- Configure test application SSO
- Require MFA for selected cloud users
- Evaluate Conditional Access using report-only mode before enforcement
- Document rollback and break-glass access

## Prerequisites

- Authorized Microsoft Entra tenant
- Appropriate administrator role
- Licensing for the selected features
- Working and stable DNS
- Tested time synchronization
- A backup and rollback plan
- No real organizational identities in the lab scope

Cloud features must not be marked complete unless the repository contains configuration and validation evidence.

