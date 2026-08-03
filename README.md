# Apex Financial Group - IAM Transformation

## 📋 Overview

This project simulates a real-world Identity and Access Management (IAM) transformation program for **Apex Financial Group**, a fictional financial services organization with 500 employees across Los Angeles, Dallas, and New York.

The objective is to design, implement, and document an enterprise IAM environment using:
- Active Directory
- Microsoft Entra ID
- Role-Based Access Control (RBAC)
- Multi-Factor Authentication (MFA)
- Single Sign-On (SSO)
- Privileged Access Management (PAM)
- Identity Governance
- Zero Trust Principles

---

## 🏗️ Target Architecture

The final solution will implement a hybrid identity architecture consisting of:

- **Active Directory Domain Services (AD DS)** - On-premises identity source
- **Microsoft Entra ID** - Cloud identity and access management
- **Microsoft Entra Connect** - Hybrid identity synchronization
- **Multi-Factor Authentication (MFA)** - Strong authentication
- **Conditional Access** - Zero Trust policy enforcement
- **Single Sign-On (SSO)** - Seamless application access
- **Privileged Access Management (PAM)** - Secure administrative accounts
- **Identity Governance** - Access reviews and compliance controls

### Conceptual Architecture

```text
                    ┌─────────────────────────┐
                    │   Microsoft Entra ID    │
                    │   (Cloud Identity)      │
                    └────────────┬────────────┘
                                 │
                          Entra Connect
                                 │
                    ┌────────────▼────────────┐
                    │  Active Directory (AD)   │
                    │  corp.apexfg.local│
                    └────────────┬────────────┘
                                 │
                    ┌────────────┴────────────┐
                    │                         │
              ┌─────▼─────┐            ┌──────▼──────┐
              │   HR      │            │   Finance   │
              │  Users    │            │   Users     │
              └───────────┘            └─────────────┘
```

Detailed architecture diagrams will be added during implementation.

---

## 🎯 Learning Objectives

This project is designed to develop practical experience in:

- Enterprise Active Directory Administration
- Hybrid Identity Architecture
- Microsoft Entra ID Administration
- Role-Based Access Control (RBAC)
- Authentication and Authorization
- SAML, OAuth 2.0, and OpenID Connect
- PowerShell Automation
- Identity Governance
- Privileged Access Management
- Zero Trust Security

---

## 🚧 Current Status

**Project In Progress** - Documentation Phase Complete | Implementation Phase Starting

### ✅ Completed
- [x] Company Profile
- [x] Department Structure
- [x] Lab Design & Requirements
- [x] Project Planning & Roadmap
- [x] GitHub Repository Setup
- [x] Project Documentation Framework

### 🔄 In Progress
- [ ] Phase 1: Identity Foundation (Active Directory)
- [ ] Phase 2: Role-Based Access Control (RBAC)
- [ ] Phase 3: Hybrid Identity (Entra ID)
- [ ] Phase 4: MFA & Conditional Access
- [ ] Phase 5: Enterprise SSO
- [ ] Phase 6: Automated Provisioning
- [ ] Phase 7: Privileged Access Management
- [ ] Phase 8: Identity Governance
- [ ] Phase 9: Zero Trust Architecture

---

## 🛠️ Technologies Used

| Category | Technology |
|:---|:---|
| **Identity Platform** | Active Directory, Microsoft Entra ID |
| **Security** | MFA, Conditional Access, Zero Trust |
| **Integration** | SAML 2.0, OAuth 2.0, OpenID Connect |
| **Automation** | PowerShell, Microsoft Graph API |
| **Governance** | Access Reviews, Risk Assessments, Compliance Controls |

---

## 🏢 Business Objectives

- Centralize identity management across all departments
- Reduce unauthorized access with least privilege
- Improve compliance readiness (SOX, GLBA, GDPR)
- Automate identity lifecycle management
- Secure privileged accounts with PAM
- Implement Zero Trust principles

---

## 📋 Regulatory Requirements Addressed

| Regulation | Requirement |
|:---|:---|
| **SOX** | Separation of duties, access controls, audit trails |
| **GLBA** | Financial privacy and data protection |
| **GDPR** | Right to access, right to deletion, data protection |
| **SEC Regulations** | Investment advisor compliance, recordkeeping |

---

## 📁 Project Structure

```text
Apex-Financial-Group-IAM-Transformation/
├── Documentation/
│   ├── Company_Profile.md          # Company overview
│   ├── Department_Structure.md     # Organizational hierarchy
│   ├── Lab_Requirements.md         # Hardware/software specs
│   ├── Project_Roadmap.md          # 12-month implementation plan
│   └── Phase_Tracker.md            # Current project status
├── Screenshots/                    # Evidence by phase
├── Architecture/                   # Draw.io diagrams
├── PowerShell/                     # Automation scripts
├── Policies/                       # Governance documents
├── Reports/                        # Audit and risk reports
└── README.md                       # This file