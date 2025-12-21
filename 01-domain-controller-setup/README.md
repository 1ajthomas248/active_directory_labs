# Lab 01: Active Directory Domain Controller Setup (Azure)

### Objective

The objective of this lab is to deploy and configure a **Windows Server–based Active Directory Domain Controller** in Microsoft Azure. This domain controller serves as the foundational identity infrastructure for all subsequent Active Directory labs in this repository.

This lab emphasizes correct networking configuration, Active Directory Domain Services (AD DS) installation, DNS integration, and real-world troubleshooting encountered during domain controller promotion.

---

### Environment Overview

- **Cloud Platform:** Microsoft Azure  
- **Operating System:** Windows Server 2022 Datacenter  
- **Server Role:** Active Directory Domain Services (AD DS)  
- **Domain Name:** `corp.local`  
- **Domain Controller:** `DC-01`  
- **Administrator Account:** `corp\dc-admin`  
- **Networking:** Azure Virtual Network with static private IP  

---

## Step 1: Create Resource Group

Create a dedicated resource group to isolate all Active Directory lab resources.

Name:
- rg-active-directory-labs

<img width="512" height="288" alt="image" src="https://github.com/user-attachments/assets/2cc9a6d7-fcef-4dfa-8ea3-657fc80654ce" />

---

## Step 2: Create Virtual Network and Subnet

Create a virtual network to simulate an internal corporate network.

My Configuration:

- VNet: vnet-ad-labs

- Address space: 10.0.0.0/16

- Subnet: subnet-ad

- Subnet range: 10.0.0.0/24

<img width="512" height="288" alt="image" src="https://github.com/user-attachments/assets/19f9c7d9-7a25-42e9-bc46-22a597515d86" />

---

## Step 3: Deploy Windows Server VM

Create a Windows Server 2022 virtual machine that will be promoted to a Domain Controller.

Settings:

- VM Name: domain-controller-01

- Image: Windows Server 2022 Datacenter

- Size: A small D sized VM

- Public IP: Enabled (for RDP)

- Virtual Network: vnet-ad-labs

- Subnet: subnet-ad

<img width="512" height="288" alt="image" src="https://github.com/user-attachments/assets/dead7654-9745-4fc9-b963-d1335701126d" />
<img width="512" height="288" alt="image" src="https://github.com/user-attachments/assets/f580b5ba-18cf-489b-b5ba-96ac6f1bd9dd" />

---

## Step 4: Configure Static Private IP

Active Directory requires a stable IP address for DNS reliability:

- Navigate to the VM’s network interface

- Change the private IP assignment from Dynamic to Static

<img width="512" height="288" alt="image" src="https://github.com/user-attachments/assets/63d57bd0-cf86-4577-a88f-0e9de82c841c" />

---

## Step 5: Install Active Directory Domain Services

Connect to the VM via RDP and install the AD DS role:

- Open Server Manager

- Add Roles and Features

- Select Active Directory Domain Services

- Complete the installation (do not promote yet)

<img width="512" height="288" alt="image" src="https://github.com/user-attachments/assets/86a1fe4c-fe55-4e66-9d9a-7b82ad024c61" />

---

## Step 6: Promote Server to Domain Controller

Promote the server to a Domain Controller and create a new forest.

Configuration:

- Deployment type: New forest

- Root domain name: corp.local

- DNS Server: Enabled

- Global Catalog: Enabled

- Directory Services Restore Mode (DSRM) password: Secure and documented

<img width="512" height="288" alt="image" src="https://github.com/user-attachments/assets/585c039e-e0db-4883-b3d6-20db538734c4" />

---

## Step 7: Verify Domain Controller Functionality

After reboot, validate the installation:

- Log in using domain credentials (corp\administrator)

- Confirm Active Directory Users and Computers opens successfully

- Verify server status in Server Manager

<img width="512" height="288" alt="image" src="https://github.com/user-attachments/assets/038d58ab-c412-42ab-afe9-e2f4769748c4" />
<img width="512" height="288" alt="image" src="https://github.com/user-attachments/assets/c5af9c6f-cc8d-4b58-ad62-578daa8872de" />

---

### Conclusion and Key Takeways

This lab successfully established a fully functional Active Directory Domain Controller in a Microsoft Azure environment, providing a stable and realistic foundation for future identity and access management labs. By configuring proper networking, installing Active Directory Domain Services with integrated DNS, and validating domain authentication, this environment now mirrors a common enterprise on-premises directory deployment. This will serve as a great foundation to build off of for the future AD labs I will be conducting.
