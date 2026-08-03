# Lab Requirements - Apex Financial Group IAM Transformation

## 📋 Executive Summary

This document outlines the hardware, software, and network requirements for building the **Apex Financial Group** IAM Transformation lab environment. The lab will simulate a 500-employee financial services organization with hybrid identity infrastructure spanning on-premises Active Directory and Microsoft Entra ID (Azure AD).

---

## 🖥️ Host Machine Requirements

### Minimum Specifications
| Component | Requirement |
|:---|:---|
| **Operating System** | Windows 10/11 Pro/Education, macOS, or Linux |
| **CPU** | Intel i5 or AMD Ryzen 5 (4+ cores) |
| **RAM** | 16 GB (absolute minimum) |
| **Storage** | 100 GB free SSD space |
| **Virtualization** | VT-x/AMD-V enabled in BIOS |

### Recommended Specifications
| Component | Requirement |
|:---|:---|
| **Operating System** | Windows 11 Pro/Education |
| **CPU** | Intel i7 or AMD Ryzen 7 (8+ cores) |
| **RAM** | 32 GB |
| **Storage** | 200 GB free NVMe SSD space |
| **Virtualization** | VT-x/AMD-V enabled in BIOS |

---

## 🧩 Virtualization Platform

Choose ONE of the following:

| Platform | Type | Cost | Notes |
|:---|:---|:---|:---|
| **VMware Workstation Pro** | Type 2 Hypervisor | Paid ($199) | Most stable, best for Windows |
| **VMware Workstation Player** | Type 2 Hypervisor | Free | Limited features but sufficient |
| **VirtualBox** | Type 2 Hypervisor | Free | Open source, cross-platform |
| **Hyper-V** | Type 1 Hypervisor | Free (Windows Pro/Education) | Built into Windows, requires Pro/Education |

**Recommendation:** VMware Workstation Player (free) or Hyper-V (if you have Windows Pro/Education).

---

## 💻 Virtual Machines

### VM01: Domain Controller (DC01)

| Configuration | Value |
|:---|:---|
| **VM Name** | DC01 |
| **Operating System** | Windows Server 2022 Standard (Desktop Experience) |
| **ISO** | Windows Server 2022 Evaluation (180-day trial) |
| **RAM** | 4 GB |
| **vCPUs** | 2 |
| **Storage** | 50 GB (Dynamic) |
| **Network Adapter 1** | NAT (for internet access) |
| **Network Adapter 2** | Host-Only (for internal network) |
| **Roles** | Active Directory Domain Services, DNS, DHCP, Group Policy Management |
| **Domain** | corp.apexfinancial.local |
| **IP Address** | 192.168.1.10 (static) |
| **DNS** | 127.0.0.1 |

**Purpose:** Primary domain controller, identity source for all on-premises users and computers.

---

### VM02: Client Workstation (CLIENT01)

| Configuration | Value |
|:---|:---|
| **VM Name** | CLIENT01 |
| **Operating System** | Windows 11 Enterprise |
| **ISO** | Windows 11 Enterprise Evaluation (90-day trial) |
| **RAM** | 4 GB |
| **vCPUs** | 2 |
| **Storage** | 40 GB (Dynamic) |
| **Network Adapter** | Host-Only (internal network) |
| **Domain** | corp.apexfinancial.local |
| **Purpose** | Domain-joined client for testing RBAC, MFA, and SSO |

**Purpose:** End-user workstation for testing access controls, group policies, and authentication flows.

---

### VM03: Optional File Server (FS01)

| Configuration | Value |
|:---|:---|
| **VM Name** | FS01 |
| **Operating System** | Windows Server 2022 Standard (Desktop Experience) |
| **RAM** | 2 GB |
| **vCPUs** | 1 |
| **Storage** | 40 GB (Dynamic) |
| **Network Adapter** | Host-Only |
| **Domain** | corp.apexfinancial.local |
| **Purpose** | File server for testing RBAC folder permissions |

**Purpose:** Simulates departmental file shares with granular permissions.

---

## ☁️ Cloud Requirements

### Microsoft Entra ID (Azure AD)

| Configuration | Value |
|:---|:---|
| **Tenant Type** | Microsoft Entra ID (Free) |
| **Tenant Name** | apexfinancial.onmicrosoft.com |
| **Custom Domain** | apexfinancial.local (verify ownership) |
| **Licenses** | Free tier (includes MFA, Conditional Access, SSO) |
| **Usage** | Hybrid identity, MFA, Conditional Access, SSO |

**Note:** You can create a free Microsoft Entra ID tenant with your personal Microsoft account.

---

### Azure AD Connect

| Configuration | Value |
|:---|:---|
| **Version** | Latest (v2.x) |
| **Install Location** | DC01 (domain controller) |
| **Sync Mode** | Password Hash Sync (PHS) |
| **Sync Scope** | All OUs (corp.apexfinancial.local) |
| **Sync Frequency** | Every 30 minutes (default) |

---

## 🧪 SSO Application Requirements

Choose 3 applications to integrate with SSO:

| Application | Type | Cost | Purpose |
|:---|:---|:---|:---|
| **GitHub** | SAML | Free | Code repository SSO |
| **Google Workspace** | SAML | Free Trial | Email/Calendar SSO |
| **ServiceNow** | SAML | Free (Developer Instance) | IT Service Management SSO |
| **Salesforce** | SAML | Free (Developer Edition) | CRM SSO |
| **Okta** | OIDC | Free (Developer) | Alternative identity provider |

**Recommendation:** GitHub + Google Workspace + ServiceNow (Developer).

---

## 🔐 PAM Tool Requirements (Optional)

Choose ONE for Privileged Access Management demonstration:

| Tool | Type | Cost | Notes |
|:---|:---|:---|:---|
| **Active Directory Built-in** | Native | Free | Use AD for PAM demonstration |
| **Delinea Secret Server** | Commercial | Free Trial | 30-day trial |
| **CyberArk** | Commercial | Free Trial | Vendor approval required |
| **BeyondTrust** | Commercial | Free Trial | Vendor approval required |

**Recommendation:** Use Active Directory built-in features for PAM demonstration (free, no trial limitations).

---

## 📋 Software Download Checklist

### Week 1 Downloads
- [ ] **Windows Server 2022 Evaluation ISO** (~5 GB)
  - Download: Microsoft Evaluation Center
  - File: `WindowsServer2022-Evaluation.iso`

- [ ] **Windows 11 Enterprise Evaluation ISO** (~5 GB)
  - Download: Microsoft Evaluation Center
  - File: `Win11_Enterprise_Eval.iso`

### Week 2 Downloads
- [ ] **Azure AD Connect** (~150 MB)
  - Download: Microsoft Download Center
  - File: `AzureADConnect.msi`

- [ ] **Visual Studio Code** (for editing scripts)
  - Download: code.visualstudio.com
  - File: `VSCodeSetup.exe`

- [ ] **Git** (for GitHub operations)
  - Download: git-scm.com
  - File: `Git-2.x.x-64-bit.exe`

### Week 3 Downloads
- [ ] **Draw.io Desktop** (for architecture diagrams)
  - Download: draw.io
  - File: `draw.io-x.x.x-windows-installer.exe`

- [ ] **Microsoft Graph PowerShell SDK**
  - Run: `Install-Module Microsoft.Graph -Scope CurrentUser`

---

## 🌐 Network Architecture

### Host-Only Network (Internal)
