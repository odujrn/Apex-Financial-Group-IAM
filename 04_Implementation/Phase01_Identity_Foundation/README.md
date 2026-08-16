# Phase 1 – Identity Foundation

## Objective

Build the foundational identity infrastructure for Apex Financial Group using Microsoft Active Directory.

---

## Business Scenario

Apex Financial Group is a fictional financial services company with 500 employees across multiple departments.

The organization currently lacks centralized identity management, role-based access controls, and standardized account provisioning.

This phase establishes the Active Directory environment that will support all future IAM initiatives.

---

## Environment

| Component | Value |
|------------|------------|
| Domain Name | corp.apexfg.local |
| Domain Controller | DC01 |
| Client Workstation | CLIENT-01 |
| DC IP Address | 192.168.102.10 |
| Client IP Address | 192.168.102.20 |

---

## OU Structure
```
Corp
├── Users
│ ├── HR
│ ├── Finance
│ ├── IT
│ ├── Sales
│ └── Executives
├── Groups
├── Servers
└── Workstations
```
---

## Users Created

### HR
- John Smith
- Mary Johnson

### Finance
- Alex Williams
- Sarah Davis

### IT
- Michael Brown
- Lisa Wilson

### Executives
- Robert Taylor

---

## Security Groups

- GG_HR_Employee
- GG_HR_Manager
- GG_Finance_Employee
- GG_Finance_Manager
- GG_IT_Admin
- GG_Executive

---

## Validation

Domain functionality validated through:

- Get-ADDomain
- Get-ADDomainController
- User authentication
- Group membership verification
- Domain-joined workstation testing
- DNS resolution testing

---

## Skills Demonstrated

- Active Directory Domain Services
- DNS Administration
- Organizational Unit Design
- Security Group Management
- User Provisioning
- Domain Join Operations
- Windows Server 2025
- Windows 11 Enterprise Administration