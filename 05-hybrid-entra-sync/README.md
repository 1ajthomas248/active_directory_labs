# Lab 05: Hybrid Identity with Azure Entra ID

### Overview
This lab demonstrates the implementation of a **hybrid identity architecture** by synchronizing an on-premises Active Directory environment with Microsoft Entra ID. Using Microsoft Entra Connect Sync, on-prem user identities are synchronized to the cloud, enabling centralized identity management and cloud-based authentication while retaining Active Directory as the source of authority.

This lab represents the capstone of the Active Directory series, bridging traditional domain infrastructure with modern cloud identity services.

---

### Objectives
- Extend an on-premises Active Directory domain to Microsoft Entra ID
- Configure directory synchronization using Microsoft Entra Connect Sync
- Validate successful synchronization of users and attributes
- Demonstrate hybrid identity sign-in behavior
- Understand UPN and domain considerations in hybrid environments

---

### Environment
- **On-Premises Domain:** `corp.local`
- **Domain Controller:** Windows Server (AD DS installed)
- **Azure Tenant:** Microsoft Entra ID
- **Synchronization Method:** Password Hash Synchronization (PHS)
- **Synchronization Tool:** Microsoft Entra Connect Sync

---

### Prerequisites
- Functional on-premises Active Directory domain
- At least one on-prem AD user account
- Azure subscription with an active Entra ID tenant
- Global Administrator account created *within* the Entra tenant
- Internet connectivity from the Domain Controller

---

### Architecture Overview
- Active Directory remains the **source of authority**
- Microsoft Entra ID acts as the **cloud identity provider**
- Microsoft Entra Connect Sync synchronizes identities from on-prem AD to Entra ID
- Users authenticate to cloud services using synchronized credentials

---

## Step 1 - Verify On-Prem Active Directory
- Confirm users exist in Active Directory
- Validate domain health and connectivity
- Ensure administrative credentials are available

<img width="512" height="288" alt="image" src="https://github.com/user-attachments/assets/c0cd0ee0-5697-43f2-8a3a-1ac3da6f0783" />

---

## Step 2 - Prepare Microsoft Entra ID
- Access Microsoft Entra ID in the Azure Portal
- Verify tenant is active
- Confirm Global Administrator permissions

<img width="512" height="288" alt="image" src="https://github.com/user-attachments/assets/0468ff4f-a3aa-47e9-bae3-a3cf8a5b1086" />

---

## Step 3 - Install Microsoft Entra Connect Sync
- Download Entra Connect directly on the Domain Controller
- Launch the installer
- Select **Express Settings**
- Choose **Password Hash Synchronization**

<img width="512" height="288" alt="image" src="https://github.com/user-attachments/assets/d6657349-39ed-4b61-af4a-5108907eed54" />

---

## Step 4 - Authentication Configuration
- Sign in using a **tenant-native Global Administrator account** (I created one for this step since I didn't have one prior to this)
- Authenticate to on-prem AD using Domain Admin credentials

<img width="512" height="288" alt="image" src="https://github.com/user-attachments/assets/e4138456-e4b9-492f-8fdc-3efc023e10ce" />

---

## Step 5 - Complete Configuration
The on-prem domain uses a non-routable UPN suffix (`corp.local`), which cannot be verified in Entra ID.

- Configuration was completed by selecting:
  **“Continue without matching all UPN suffixes to verified domains”**
- Users authenticate using the tenant `onmicrosoft.com` domain in the cloud

<img width="512" height="288" alt="image" src="https://github.com/user-attachments/assets/dd6280fb-e569-4fa8-930a-ea1d25182e9c" />

---

## Step 6 - Verify Synchronization
- Confirm on-prem users appear in Microsoft Entra ID
- Validate synchronization source shows **Windows Server AD**
- Review sync status and health

<img width="512" height="288" alt="image" src="https://github.com/user-attachments/assets/6c99c479-25ec-46e4-9625-18e29b05275f" />
<img width="512" height="288" alt="image" src="https://github.com/user-attachments/assets/255119d3-253d-4e8e-9eb9-d4c52bd39551" />

---

## Step 7 - Validate Hybrid Sign-In
- Sign in to a Microsoft cloud service using synced credentials
- Confirm authentication succeeds

<img width="512" height="288" alt="image" src="https://github.com/user-attachments/assets/1a371092-0a47-4031-81f8-67b47fb7eeb9" />

---

### Key Takeaways and Conclusion
This lab demonstrates how traditional on-premises Active Directory environments integrate with modern cloud identity platforms. By implementing Microsoft Entra Connect Sync, identities remain centrally managed on-prem while being extended to the cloud for authentication and access control. The lab also highlights common real-world considerations such as UPN suffix mismatches and the distinction between tenant-native and external identities, reinforcing the importance of architectural decisions in hybrid identity deployments. Completing this lab establishes a full hybrid identity foundation, combining on-prem Active Directory with Microsoft Entra ID. This architecture mirrors real enterprise environments and enables advanced identity scenarios such as Conditional Access, MFA enforcement, Azure RBAC, and Zero Trust security models. With this integration in place, the environment is prepared for further cloud identity and security-focused implementations.

