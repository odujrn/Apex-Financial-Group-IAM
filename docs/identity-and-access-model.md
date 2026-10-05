# Identity and Access Model

## Organizational-unit structure

```text
Corp
├── Users
│   ├── HR
│   ├── Finance
│   ├── IT
│   ├── Sales
│   └── Executives
├── Groups
├── Servers
└── Workstations
```

The OU structure supports administration and Group Policy targeting. OUs are not used as a substitute for authorization groups.

## Representative identities

| User | Sign-in name | Department | Current groups |
|---|---|---|---|
| John Smith | `john.smith` | HR | `GG_HR_Employee` |
| Mary Johnson | `mary.johnson` | HR | `GG_HR_Employee`, `GG_HR_Manager` |
| Alex Williams | `alex.williams` | Finance | `GG_Finance_Employee` |
| Sarah Davis | `sarah.davis` | Finance | `GG_Finance_Employee`, `GG_Finance_Manager` |
| Michael Brown | `michael.brown` | IT | `GG_IT_Admin` |
| Lisa Wilson | `lisa.wilson` | IT | `GG_IT_Admin` |
| David Miller | `david.miller` | Sales | `GG_Sales_Employee` |
| Robert Taylor | `robert.taylor` | Executives | `GG_Executive` |

## Naming convention

| Object | Pattern | Example |
|---|---|---|
| Global role group | `GG_<Department>_<Role>` | `GG_HR_Manager` |
| Domain-local resource group | `DL_<Resource>_<Access>` | `DL_FS_HR_Modify` |
| Standard username | `first.last` | `john.smith` |
| Administrative username | separate named admin account | `first.last-admin` |

## Authorization model

Phase 2 introduces an AGDLP-style model:

```mermaid
flowchart LR
    A["Accounts"] --> G["Global role groups"]
    G --> DL["Domain-local resource groups"]
    DL --> P["Resource permissions"]
```

This keeps business-role membership separate from resource-specific permissions. A user changes role by moving between global groups; resource ACLs remain stable.

## Control rules

- Do not assign file permissions directly to individual users.
- Do not use ordinary user accounts for administrative work.
- Managers receive access only to the management subfolder for their own department.
- Access changes require a documented reason and validation.
- A denied-access test is required for every sensitive resource test.

