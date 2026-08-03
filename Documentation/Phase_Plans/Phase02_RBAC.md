# Phase 2: Role-Based Access Control (RBAC)

## 📌 Objective
Implement least privilege access controls through security groups and folder permissions.

## 🎯 Goals
1. Create security groups based on department and role
2. Assign users to appropriate groups
3. Create shared folders with granular permissions
4. Test access (allow/deny scenarios)

## 🧠 What I Will Learn
- Security Groups vs Distribution Groups
- Global vs Universal groups
- NTFS permissions
- Share permissions
- Effective Access

## 🔧 Implementation Steps

### Step 1: Create Security Groups
GG_HR_Employee
GG_HR_Manager
GG_Finance_Employee
GG_Finance_Manager
GG_IT_Admin
GG_Sales_Employee
GG_Sales_Manager
GG_Executive

### Step 2: Assign Users to Groups
| User | Groups |
|:---|:---|
| john.hr | GG_HR_Employee |
| mary.hr | GG_HR_Employee, GG_HR_Manager |
| alex.finance | GG_Finance_Employee |
| sarah.finance | GG_Finance_Employee, GG_Finance_Manager |
| mike.it | GG_IT_Admin |

### Step 3: Create Shared Folders with Permissions
C:\Shares
├── HR-Folder
│ ├── GG_HR_Employee → Read
│ └── GG_HR_Manager → Full Control
├── Finance-Folder
│ ├── GG_Finance_Employee → Read
│ └── GG_Finance_Manager → Full Control
├── IT-Admin-Folder
│ └── GG_IT_Admin → Full Control
└── Public-Folder
└── All Users → Read

### Step 4: Test Access
| User | Test | Expected |
|:---|:---|:---|
| john.hr | Access HR-Folder | ✅ Allowed |
| john.hr | Access Finance-Folder | ❌ Denied |
| mike.it | Access IT-Admin-Folder | ✅ Allowed |

## 📸 Screenshots to Capture
- [ ] All security groups in ADUC
- [ ] Group memberships for each user
- [ ] Folder permissions (Security tab)
- [ ] Folder sharing settings
- [ ] Access allowed example
- [ ] Access denied error

## ✅ Checklist
- [ ] Security groups created
- [ ] Users assigned to groups
- [ ] Shared folders created
- [ ] Permissions configured
- [ ] Access tests performed
- [ ] Screenshots captured

---

*Phase 2 Version: 1.0 | Status: Not Started*
