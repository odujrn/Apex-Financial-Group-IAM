# Phase 1: Identity Foundation

## 📌 Objective
Build the company's on-premises Active Directory infrastructure to serve as the foundation for all identity management.

## 🎯 Goals
1. Set up Windows Server 2022 VM
2. Install Active Directory Domain Services
3. Configure DNS for the domain
4. Create Organizational Units (OUs)
5. Create test users
6. Verify AD functionality

## 🧠 What I Will Learn
- Active Directory Domain Services (AD DS)
- DNS configuration
- Organizational Unit design
- User provisioning
- Group Policy basics

## 🔧 Implementation Steps

### Step 1: Create Virtual Machine
- Platform: VMware Workstation Player / VirtualBox
- OS: Windows Server 2022 Standard (Desktop Experience)
- RAM: 4GB
- Storage: 50GB
- Network: NAT (for internet access)

### Step 2: Install Windows Server 2022
- Boot from ISO
- Select: Windows Server 2022 Standard (Desktop Experience)
- Set Administrator password

### Step 3: Promote to Domain Controller
- Install Active Directory Domain Services
- Promote to Domain Controller
- New forest: `corp.apexfinancial.local`
- Set DSRM password

### Step 4: Create Organizational Units
corp.apexfinancial.local
├── HR
├── Finance
├── IT
├── Sales
├── Operations
├── Executives
├── Contractors
└── Disabled Users

### Step 5: Create Test Users
| Username | Department | Role |
|:---|:---|:---|
| john.hr | HR | Employee |
| mary.hr | HR | Manager |
| alex.finance | Finance | Employee |
| sarah.finance | Finance | Manager |
| mike.it | IT | Administrator |
| tom.it | IT | Help Desk |
| david.sales | Sales | Employee |
| lisa.exec | Executives | Director |

## 📸 Screenshots to Capture
- [ ] VM configuration in VMware/VirtualBox
- [ ] Windows Server installation progress
- [ ] Network configuration (static IP)
- [ ] Server renamed to DC01
- [ ] AD DS installation
- [ ] Domain promotion wizard
- [ ] AD Users & Computers showing OUs
- [ ] Users in each OU

## 🚧 Challenges & Solutions
| Challenge | Solution |
|:---|:---|
| DNS not resolving | Set DNS to 127.0.0.1 |
| Password complexity | Use complex passwords like `Contoso@2026!` |

## ✅ Checklist
- [ ] VM created
- [ ] Windows Server installed
- [ ] Domain controller promoted
- [ ] DNS configured
- [ ] OUs created
- [ ] Test users created
- [ ] Screenshots captured
- [ ] Phase README updated

---

*Phase 1 Version: 1.0 | Status: Not Started*
