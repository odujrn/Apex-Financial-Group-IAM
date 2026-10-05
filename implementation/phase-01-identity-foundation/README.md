# Phase 1 — Active Directory Identity Foundation

**Status:** Completed

## Objective

Build and validate the on-premises identity foundation required by later IAM controls.

## Security problem

Without centralized identities and consistent administrative boundaries, access is difficult to manage, review, or revoke. The first phase establishes authoritative identities, organizational structure, and role groups.

## Implementation

1. Installed and configured Active Directory Domain Services on `DC01`.
2. Created the `Corp.apexfg.local` forest and domain.
3. Used `DC01` (`192.168.102.10`) as the client's DNS server.
4. Created department OUs for HR, Finance, IT, Sales, and Executives.
5. Created representative users and security groups.
6. Added users to role-aligned groups.
7. Joined `CLIENT-01` (`192.168.102.20`) to the domain.
8. Tested domain sign-in, identity context, hostname, and group membership.

## Validation results

| Test | Expected result | Result |
|---|---|---|
| Query the AD domain | `Corp.apexfg.local` returned | Pass |
| Query the domain controller | `DC01` returned | Pass |
| Review OU structure | Department OUs present | Pass |
| Review users and groups | Planned objects present | Pass |
| Join client to domain | `CLIENT-01` appears in domain | Pass |
| Sign in with domain identity | Domain session established | Pass |
| Check identity context | Domain user returned | Pass |
| Check group membership | Expected security groups returned | Pass |
| Resolve AD records | Required records resolved | Pass with noted DNS warning |

## Evidence

- [AD domain validation](../../evidence/phase-01/01-get-addomain.png)
- [Domain controller validation](../../evidence/phase-01/02-get-addomaincontroller.png)
- [OU structure](../../evidence/phase-01/03-ou-structure.png)
- [Security groups](../../evidence/phase-01/04-security-groups.png)
- [HR users](../../evidence/phase-01/05-hr-users.png)
- [Finance users](../../evidence/phase-01/06-finance-users.png)
- [IT users](../../evidence/phase-01/07-it-users.png)
- [Sales users](../../evidence/phase-01/08-sales-users.png)
- [Executive users](../../evidence/phase-01/09-executive-users.png)
- [Authenticated identity](../../evidence/phase-01/10-whoami.png)
- [Domain-joined client](../../evidence/phase-01/11-domain-join.png)
- [Client hostname](../../evidence/phase-01/12-hostname.png)
- [Domain verification](../../evidence/phase-01/13-domain-verification.png)
- [Final validation](../../evidence/phase-01/14-final-validation.png)
- [Group membership](../../evidence/phase-01/15-group-membership.png)

## Limitation and lesson learned

DNS provided the records needed for domain operations, but the client also showed `Server: Unknown` and intermittent timeouts. The domain join and authentication tests succeeded, so Phase 1 is complete; however, DNS health should be revisited before adding a cloud synchronization dependency.

The primary lesson was that object creation is not enough. A credible identity foundation also needs client-side authentication tests and evidence of group membership.

