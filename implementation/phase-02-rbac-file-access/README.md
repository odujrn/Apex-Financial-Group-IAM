# Phase 2 — RBAC and Departmental File Access

**Status:** Implemented — validation refinement in progress

**Estimated effort:** 3–5 hours

## Objective

Implement least-privilege access to departmental folders using an AGDLP-style group model, then prove both allowed and denied access.

## Security problem

Directly assigning permissions to users creates inconsistent, difficult-to-audit access. Department employees and managers also need different access levels.

## Implemented design

The current lab uses `C:\Shares\SalesData`, published as `\\DC01\SalesData`, and maps it as drive `S:` through the `Sales_Drive_Mapping` GPO.

```text
SalesData
├── HR
│   ├── General
│   └── Management
├── Finance
│   ├── General
│   └── Management
├── Sales
├── IT-Admin
└── Executives
```

The name `SalesData` is retained because it reflects the implemented configuration and screenshots. A neutral name such as `DepartmentData` would better describe a share containing HR, Finance, Sales, IT, and Executive data. Renaming it is a future improvement because it requires coordinated changes to the share, GPO, and validation evidence.

### Recommended resource groups

| Domain-local group | Resource access | Nested global group |
|---|---|---|
| `DL_FS_SalesData_Access` | Share-level Change/Read | All approved department role groups |
| `DL_FS_HR_Modify` | HR General — Modify | `GG_HR_Employee` |
| `DL_FS_HR_Management_Modify` | HR Management — Modify | `GG_HR_Manager` |
| `DL_FS_Finance_Modify` | Finance General — Modify | `GG_Finance_Employee` |
| `DL_FS_Finance_Management_Modify` | Finance Management — Modify | `GG_Finance_Manager` |
| `DL_FS_Sales_Modify` | Sales — Modify | `GG_Sales_Employee` |
| `DL_FS_IT_Admin_Modify` | IT-Admin — Modify | `GG_IT_Admin` |
| `DL_FS_Executive_Modify` | Executives — Modify | `GG_Executive` |

### Permission approach

- Share permissions: Administrators — Full Control; `DL_FS_DepartmentData_Access` — Change and Read.
- NTFS permissions: grant each resource group Modify only on its assigned folder.
- Remove broad inherited access where safe, while retaining SYSTEM and Administrators.
- Do not grant permissions directly to users.

> Lab note: using a domain controller as a file server reduces VM requirements but is not recommended for production.

## Work completed

1. Created and exposed the `SalesData` file share on `DC01`.
2. Created the `Sales_Drive_Mapping` Group Policy Object.
3. Applied security filtering to `GG_Sales_Employee`.
4. Mapped `\\DC01\SalesData` as the `S:` drive.
5. Validated that John Smith could open the HR folder.
6. Validated that John Smith could not modify the share root.
7. Validated that Alex Williams was denied access to the HR folder.
8. Captured the Finance folder on the server; this test requires repetition from `CLIENT-01` while authenticated as Alex Williams.

## Current validation matrix

| Test identity | Resource | Expected |
|---|---|---|
| Identity | Test | Expected | Evidence status |
|---|---|---|---|
| `john.smith` | Open `S:\HR` | Allowed | Validated |
| `john.smith` | Modify share root | Denied | Validated |
| `alex.williams` | Open `\\DC01\SalesData\HR` | Denied | Validated |
| `alex.williams` | Open Finance through mapped drive or UNC | Allowed | **Repeat required** |
| `mary.johnson` | Open HR management folder | Allowed | Not yet captured |
| `john.smith` | Open HR management folder | Denied | Not yet captured |
| `david.miller` | Open Sales folder | Allowed | Not yet captured |

Each allowed test should create, modify, and delete a harmless text file. Each denied test should show that the user cannot open or modify the protected location.

## Evidence gallery

- [SalesData share accessible](../../evidence/phase-02/01-salesdata-share-access.png)
- [Drive-mapping GPO created](../../evidence/phase-02/02-sales-drive-mapping-gpo.png)
- [GPO scope and security filter](../../evidence/phase-02/03-gpo-security-filter.png)
- [S drive mapped successfully](../../evidence/phase-02/04-salesdata-drive-mapped.png)
- [John Smith HR access allowed](../../evidence/phase-02/05-john-hr-access-allowed.png)
- [John Smith share-root modification denied](../../evidence/phase-02/06-john-share-root-denied.png)
- [Finance folder local-path evidence](../../evidence/phase-02/07-finance-folder-local-path.png)
- [Alex Williams HR access denied](../../evidence/phase-02/08-alex-hr-access-denied.png)

## Evidence assessment

The GPO screenshot shows `GG_Sales_Employee` as the security filter, while the mapped-drive and access tests focus on HR and Finance identities. This may mean that additional item-level targeting or group membership exists but is not visible in the evidence. Capture the drive-mapping preference configuration and targeting rules so the authorization path is unambiguous.

The existing Finance screenshot shows `C:\Shares\SalesData\Finance`, which is a local server path. It proves that the folder exists, but it does not prove Alex Williams received authorized network access. Repeat this test from `CLIENT-01`, run `whoami`, and open either `S:\Finance` or `\\DC01\SalesData\Finance` in the same session.

## Remaining evidence needed

1. Share permissions for `SalesData`.
2. NTFS permissions for the HR and Finance folders.
3. Drive Maps preference configuration and any item-level targeting.
4. `whoami` plus Alex Williams accessing Finance from `CLIENT-01`.
5. A manager-versus-employee test for a protected management folder.
6. Completed [access-test matrix](../../templates/access-test-matrix.md).

## Completion criteria

Phase 2 is complete when the remaining evidence is captured, the GPO scope is reconciled with the intended users, all required tests match their expected outcomes, no user has a direct ACL entry, and the access matrix records the results.
