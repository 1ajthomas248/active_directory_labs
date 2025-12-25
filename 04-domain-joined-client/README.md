# Lab 04 – Domain-Joined Client Management

## Overview
This lab focuses on validating and managing a Windows client that has been joined to an Active Directory domain. The objective is to confirm proper domain authentication, Group Policy application, and centralized management from the domain controller. This lab builds on the foundational Active Directory configuration established in previous labs.

---

### Objectives
- Verify successful domain join of a client workstation
- Confirm domain user authentication on the client
- Validate computer and user object placement within Active Directory OUs
- Apply and verify Group Policy from the domain controller
- Troubleshoot and resolve Remote Desktop authorization issues
- Demonstrate centralized management using Active Directory tools

---

### Environment
- **Domain Controller:** Windows Server (AD DS + DNS installed)
- **Client Machine:** Windows domain-joined workstation
- **Domain Name:** `corp.local`
- **User OU:** IT
- **Computer OU:** IT
- **Tools Used:**  
  - Active Directory Users and Computers  
  - Group Policy Management  
  - PowerShell  
  - Remote Desktop (RDP)

---

## Step 1: Verify Domain Join on Client

On the client VM, confirm that the client is part of the "corp.local" doamin

I ran a PowerShell command to verify this

``` powershell
systeminfo | findstr /B /C:"Domain"
```

<img width="512" height="288" alt="image" src="https://github.com/user-attachments/assets/e34941d0-8837-4003-afb2-5f1777d6cf0a" />

## Step 2: Verify Client Object in Active Directory

On the Domain Controller, open Active Directory Users and Computers

Navigate to corp.local → OUs

Confirm that the client VM exists as a computer object

<img width="512" height="288" alt="image" src="https://github.com/user-attachments/assets/e1e0d26b-6d05-45e0-a09d-5ac379b506c7" />

## Step 3: Test Domain User Login

On the client VM, Sign out of the local account

Log in using one of the users you created in the earlier parts of the lab. In this case I chose IT user "Alex Johnson"

Then confirm:

- Login succeeds

- Desktop profile is created for the domain user

During this process, I got an error saying that the Alex Johnson user didn't have permission for Remote Desktop. I had to add that user to the RDP Users to finsih out the verification process. 

## Step 4: Apply Group Policy

From client VM use these PowerShell commands to apply and check the policies:

```
gpupdate /force
gpresult /r
```

Confirm:

- Computer policies applied

- User policies applied

- Domain name listed correctly

<img width="512" height="288" alt="image" src="https://github.com/user-attachments/assets/1da8e122-db67-4faa-ac90-7753aa324c95" />

---

### Key Takeaways and Conclusions

This lab demonstrated the full lifecycle of managing a domain-joined client within an Active Directory environment, from domain authentication to centralized policy enforcement. Through validating domain membership, confirming user authentication, and verifying Group Policy application, this lab reinforced the separation between authentication and authorization, particularly in the context of Remote Desktop access. Proper OU placement proved essential for effective Group Policy targeting and scalability, while Azure-specific RDP behavior highlighted real-world considerations when administering cloud-hosted Windows systems. Overall, this lab strengthened foundational Active Directory administration skills and provided practical troubleshooting experience that mirrors enterprise environments.
