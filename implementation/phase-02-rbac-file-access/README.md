# Phase 2 — RBAC and Departmental File Access

**Status:** Completed

**Estimated effort:** 3–5 hours

## Objective

Implement and validate least-privilege access to departmental folders using Active Directory security groups, share permissions, NTFS permissions, and a security-filtered Group Policy drive mapping.

## Security problem

Assigning file permissions directly to individual users creates inconsistent access that is difficult to maintain and audit. Departmental information must be restricted so employees can access their assigned resources without gaining access to other departments.

## Implemented design

The lab uses the following folder structure on `DC01`:

```text
C:\Shares\SalesData
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

The folder is published as:

```text
\\DC01\SalesData
```

The `Sales_Drive_Mapping` Group Policy Object maps this share as drive `S:` for members of `GG_Sales_Employee`.

The share name `SalesData` is retained because it reflects the implemented configuration and collected evidence. A neutral name such as `DepartmentData` would better describe a share containing HR, Finance, Sales, IT, and Executive information. Renaming it is a future improvement because it would require coordinated changes to the share, GPO, documentation, and validation evidence.

### Access-control model

Department users receive access through security-group membership rather than direct user-level permissions.

| Security group | Intended access |
|---|---|
| `GG_HR_Employee` | HR departmental resources |
| `GG_Finance_Employee` | Finance departmental resources |
| `GG_Sales_Employee` | Sales resources and the Sales drive-mapping GPO |
| `GG_IT_Admin` | IT administrative resources |
| `GG_Executive` | Executive resources |

A more mature implementation can introduce domain-local resource groups following the AGDLP model:

```text
Accounts → Global groups → Domain-local groups → Permissions
```

Example domain-local groups include:

| Domain-local group | Resource access | Nested global group |
|---|---|---|
| `DL_FS_HR_Modify` | HR General — Modify | `GG_HR_Employee` |
| `DL_FS_HR_Management_Modify` | HR Management — Modify | `GG_HR_Manager` |
| `DL_FS_Finance_Modify` | Finance General — Modify | `GG_Finance_Employee` |
| `DL_FS_Finance_Management_Modify` | Finance Management — Modify | `GG_Finance_Manager` |
| `DL_FS_Sales_Modify` | Sales — Modify | `GG_Sales_Employee` |
| `DL_FS_IT_Admin_Modify` | IT-Admin — Modify | `GG_IT_Admin` |
| `DL_FS_Executive_Modify` | Executives — Modify | `GG_Executive` |

> Lab note: DC01 also hosts the file share to reduce the number of required virtual machines. Combining domain-controller and file-server roles is not recommended for a production environment.

## Work completed

1. Created and published the `SalesData` file share on `DC01`.
2. Created the `Sales_Drive_Mapping` Group Policy Object.
3. Linked the GPO at the domain level.
4. Restricted GPO application to `GG_Sales_Employee`.
5. Configured the GPO to create drive `S:` pointing to `\\DC01\SalesData`.
6. Validated successful mapped-drive deployment for the intended Sales scope.
7. Validated that John Smith could access the HR folder.
8. Validated that John Smith could not modify the share root.
9. Confirmed that Alex Williams belonged to `GG_Finance_Employee`.
10. Validated that Alex could create a file through `\\DC01\SalesData\Finance`.
11. Validated that Alex was denied access to `\\DC01\SalesData\HR`.
12. Investigated and resolved an apparently inconsistent persistent drive mapping.

## Validation results

| Test identity | Resource or control | Expected result | Actual result | Status |
|---|---|---|---|---|
| `john.smith` | Open HR folder | Allowed | Access succeeded | Passed |
| `john.smith` | Modify share root | Denied | Modification denied | Passed |
| `GG_Sales_Employee` member | Receive `S:` drive through GPO | Allowed | Drive mapping created | Passed |
| `alex.williams` | Receive Sales drive-mapping GPO | Not applied | GPO did not apply | Passed |
| `alex.williams` | Create a file in `\\DC01\SalesData\Finance` | Allowed | File created and saved | Passed |
| `alex.williams` | Open `\\DC01\SalesData\HR` | Denied | Permission error displayed | Passed |

## Troubleshooting performed

During validation, drive `S:` initially appeared in Alex Williams's session even though the `Sales_Drive_Mapping` GPO was restricted to `GG_Sales_Employee`.

The following investigation was performed:

1. Ran `whoami` to confirm that the session belonged to `CORP\alex.williams`.
2. Ran `gpresult /r /scope:user`.
3. Confirmed that Alex belonged to `GG_Finance_Employee`.
4. Confirmed that no domain GPO was listed under **Applied Group Policy Objects**.
5. Used `net use` to identify the existing `S:` connection.
6. Removed the connection with:

```cmd
net use S: /delete
```

7. Refreshed policy with:

```cmd
gpupdate /force
```

8. Signed out and signed back in as Alex.
9. Confirmed that drive `S:` did not return.

This demonstrated that the original drive was a remembered or persistent connection rather than a GPO assignment. The final behavior matched the intended Sales-only GPO security filter.

## Evidence gallery

### Original implementation evidence

- [SalesData share accessible](../../evidence/phase-02/01-salesdata-share-access.png)
- [Drive-mapping GPO created](../../evidence/phase-02/02-sales-drive-mapping-gpo.png)
- [Original GPO security filter](../../evidence/phase-02/03-gpo-security-filter.png)
- [SalesData drive mapped](../../evidence/phase-02/04-salesdata-drive-mapped.png)
- [John Smith HR access allowed](../../evidence/phase-02/05-john-hr-access-allowed.png)
- [John Smith share-root modification denied](../../evidence/phase-02/06-john-share-root-denied.png)

### Final validation evidence

- [Sales GPO scope and security filter](../../evidence/phase-02/09b-sales-gpo-scope-filter.png)
- [Sales GPO drive-map configuration](../../evidence/phase-02/09c-sales-gpo-drive-map-settings.png)
- [Alex Williams Finance network write access allowed](../../evidence/phase-02/11-alex-finance-network-access-allowed.png)
- [Alex Williams HR network access denied](../../evidence/phase-02/12-alex-hr-network-access-denied.png)

## Security findings

- Group membership controls departmental authorization.
- The Sales drive-mapping GPO applies only to `GG_Sales_Employee`.
- A Finance user can access and modify the authorized Finance folder.
- The same Finance user cannot access the HR folder.
- The share root is protected from unauthorized modification.
- Positive and negative tests confirm that least-privilege restrictions operate as intended.
- Troubleshooting verified that a persistent drive connection should not be mistaken for successful GPO application.

## Future improvements

The following enhancements are outside the completed Phase 2 validation scope:

1. Rename `SalesData` to a neutral name such as `DepartmentData`.
2. Capture detailed share-permission and NTFS-permission screenshots.
3. Complete manager-versus-employee testing for the protected management folders.
4. Implement and document the full AGDLP nesting model.
5. Complete the reusable [access-test matrix](../../templates/access-test-matrix.md).
6. Move the file-server role from the domain controller to a dedicated member server.
7. Review whether the domain-level GPO link must be enforced or whether a narrower OU link would provide cleaner scope control.

## Completion statement

Phase 2 successfully demonstrated group-based authorization, security-filtered Group Policy deployment, departmental network access, cross-department denial, and evidence-based troubleshooting.

The completed tests confirm that approved users can access their assigned departmental resources while unauthorized users are denied access.
