# Phase 3: Hybrid Identity

## 📌 Objective
Connect on-premises Active Directory to Microsoft Entra ID (Azure AD) for hybrid identity.

## 🎯 Goals
1. Create Microsoft Entra ID tenant
2. Install Azure AD Connect
3. Configure synchronization
4. Verify users sync to cloud
5. Test password hash sync

## 🧠 What I Will Learn
- Microsoft Entra ID (Azure AD)
- Azure AD Connect
- Password Hash Sync (PHS)
- Hybrid identity architecture
- Directory synchronization

## 🔧 Implementation Steps

### Step 1: Create Microsoft Entra ID Tenant
- Go to portal.azure.com
- Create new tenant: `apexfinancial.onmicrosoft.com`
- Verify custom domain: `apexfinancial.local`

### Step 2: Install Azure AD Connect
- Download from Microsoft Download Center
- Install on DC01
- Select Express Settings

### Step 3: Configure Sync
- Use Password Hash Sync
- Sync all OUs
- Enable seamless SSO

### Step 4: Verify Sync
- Check Entra ID → Users
- Confirm "Synced from on-premises" label
- Test password change sync

## 📸 Screenshots to Capture
- [ ] Entra ID tenant creation
- [ ] Azure AD Connect installation
- [ ] Sync configuration screen
- [ ] Sync success status
- [ ] Entra ID users synced
- [ ] Password hash sync verified

## 🚧 Challenges & Solutions
| Challenge | Solution |
|:---|:---|
| Duplicate UPN | Delete cloud user, re-sync |
| Sync errors | Check OU filtering |

## ✅ Checklist
- [ ] Entra ID tenant created
- [ ] Azure AD Connect installed
- [ ] Users synced to cloud
- [ ] Password sync verified
- [ ] Screenshots captured

---

*Phase 3 Version: 1.0 | Status: Not Started*
