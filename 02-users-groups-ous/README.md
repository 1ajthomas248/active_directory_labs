# Lab 02: Active Directory – Users, Groups, and Organizational Units

## Overview
This lab focuses on managing **users, security groups, and organizational units (OUs)** within an Active Directory domain. These objects form the foundation of identity management, access control, and policy enforcement in enterprise Windows environments.

The goal of this lab is to gain hands-on experience with core administrative tasks that system administrators perform daily when managing a Windows domain.

---

### Objectives
By completing this lab, I was able to:

- Create and organize Organizational Units (OUs)
- Create Active Directory user accounts
- Create and configure security groups
- Assign users to groups for role-based access
- Understand the functional differences between OUs and groups
- Verify Active Directory changes using built-in tools and PowerShell

---

### Prerequisites
- Windows Server installed
- Active Directory Domain Services (AD DS) installed
- Server promoted to a Domain Controller
- Logged in as a domain administrator account

---

### Lab Environment
- **Server OS**: Windows Server
- **Directory Service**: Active Directory Domain Services
- **Domain**: `corp.local`
- **Administrative Tool**: Active Directory Users and Computers (ADUC)

---

## Step 1: Open Active Directory Users and Computers

Log into the Domain Controller

Open Server Manager

Navigate to:
- Tools → Active Directory Users and Computers

<img width="512" height="288" alt="image" src="https://github.com/user-attachments/assets/8831889b-24ab-4193-825a-0134a897bbfd" />

## Step 2: Create Organizational Units (OUs)

Right-click the domain → New → Organizational Unit

Name the OU (e.g., IT)

Repeat for each OU listed above

<img width="512" height="288" alt="image" src="https://github.com/user-attachments/assets/a7c0d61a-aa08-46d2-8810-222d11d42616" />
<img width="512" height="288" alt="image" src="https://github.com/user-attachments/assets/6802ce77-1f78-4f37-b477-3fbbcd8abf83" />

## Step 3: Create User Accounts

Right-click the appropriate OU → New → User

Fill in:

- Full name

- User logon name

Set a password

<img width="512" height="288" alt="image" src="https://github.com/user-attachments/assets/10a0b417-bb72-444a-ac05-86d4372d9250" />

## Step 4: Create Security Groups

Right-click the OU → New → Group

Enter group name

Select:

- Group scope: Global

- Group type: Security

<img width="512" height="288" alt="image" src="https://github.com/user-attachments/assets/6f4907bd-cb58-49f6-9578-b480ed804385" />

## Step 5: Add Users to Groups

Right-click a group → Properties

Go to the Members tab

Click Add

Select the appropriate user

<img width="512" height="288" alt="image" src="https://github.com/user-attachments/assets/df9224e9-2a43-4948-b7e7-dcbf48d11e42" />

## Step 6: Verify Configuration

Confirm:

- Users are in the correct OUs

- Groups contain the correct members

- No users remain in the default Users container unintentionally

I was able to do so by running these PowerShell commands:
```
Get-ADUser -Filter * | Select Name, DistinguishedName
Get-ADGroupMember IT-Users
```

<img width="512" height="288" alt="image" src="https://github.com/user-attachments/assets/22648dea-965a-4a58-a596-67c1bedb321c" />

---

### Key takeways and Conclusion

This lab reinforced the importance of structured Active Directory design. Separating users into OUs and assigning access through security groups creates a scalable, secure, and manageable directory environment. These principles are critical in enterprise IT environments and serve as the foundation for applying Group Policy and delegated administration.
