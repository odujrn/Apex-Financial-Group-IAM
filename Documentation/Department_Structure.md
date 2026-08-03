# Apex Financial Group
## Department Structure

## 📋 Purpose

This document defines the organizational structure of Apex Financial Group. This structure serves as the foundation for:

- **Active Directory OUs** — Each department becomes an Organizational Unit
- **Security Groups** — Each role maps to a security group (e.g., GG_HR_Employee)
- **RBAC Permissions** — Access controls are based on department and role
- **User Provisioning** — Automation scripts use this structure to assign correct permissions

---

## Executive Leadership

```
Chief Executive Officer (CEO)
└── Executive Assistant
```

## Human Resources (HR)

```
HR Director
└── HR Manager
    ├── HR Specialist 01
    ├── HR Specialist 02
    └── HR Specialist 03
```

## Finance

```
Finance Director
└── Finance Manager
    ├── Financial Analyst 01
    ├── Financial Analyst 02
    └── Financial Analyst 03
```

## Information Technology (IT)

```
IT Director
├── IAM Engineer
├── Systems Administrator
└── Help Desk
    ├── Help Desk Technician 01
    └── Help Desk Technician 02
```

## Sales

```
Sales Director
└── Sales Manager
    ├── Sales Representative 01
    ├── Sales Representative 02
    ├── Sales Representative 03
    ├── Sales Representative 04
    └── Sales Representative 05
```

## Contractors

```
Contractor 01
Contractor 02
Contractor 03
```

## User Account Mapping

| Username | Department | Role | Location |
|:---|:---|:---|:---|
| jane.hr | HR | HR Specialist | Los Angeles |
| john.hr | HR | HR Specialist | Los Angeles |
| mary.hr | HR | HR Manager | Los Angeles |
| alex.finance | Finance | Financial Analyst | Dallas |
| sarah.finance | Finance | Finance Manager | Dallas |
| mike.it | IT | Systems Administrator | Los Angeles |
| tom.it | IT | Help Desk | Los Angeles |
| lisa.it | IT | IAM Engineer | New York |
| dave.sales | Sales | Sales Representative | Los Angeles |
| anna.sales | Sales | Sales Manager | New York |
| contractor01 | Contractors | Contractor | Remote |
| contractor02 | Contractors | Contractor | Remote |