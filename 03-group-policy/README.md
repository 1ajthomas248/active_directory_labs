# Lab 03 – Group Policy Objects

### Overview
This lab focuses on creating, linking, and validating Group Policy Objects (GPOs) within an Active Directory environment. The goal was to enforce centralized configuration and security settings using OU-scoped GPOs and verify proper policy application in a realistic enterprise-style setup.

This lab builds directly on the Domain Controller and Organizational Unit structure created in Labs 1 and 2.

---

### Objectives
- Understand how Group Policy Objects work in Active Directory
- Create and link a custom GPO to a specific OU
- Configure computer-based and user-based policy settings
- Validate GPO application and scope
- Troubleshoot common GPO deployment issues

---

## Environment
- **Cloud Platform:** Microsoft Azure  
- **Domain Controller:** Windows Server 2022  
- **Client Machine:** Windows Server 2022 (used as a workstation)  
- **Domain:** `corp.local`  
- **Tools Used:**  
  - Group Policy Management Console (GPMC)  
  - Active Directory Users and Computers

---

## Step 1: Open Group Policy Management

Log into the Domain Controller

Open Group Policy Management

```
Forest
└── Domains
    └── yourdomain.local
```

<img width="512" height="288" alt="image" src="https://github.com/user-attachments/assets/8fd6d233-6da0-4cd6-afba-ea83da98f7a6" />

## Step 2: Create a Test GPO

Right-click Group Policy Objects

Select New and give it a name

<img width="512" height="288" alt="image" src="https://github.com/user-attachments/assets/d2f79dfe-6da0-4e8c-b3ab-43a4449927e0" />

## Step 3: Link the GPO to an OU

Right-click your Workstations OU

Select Link an Existing GPO

Choose the GPO you just created

## Step 4: Configure Computer and US Policies

Edit the GPO and navigate to these two directories:

```
Computer Configuration
└── Policies
    └── Windows Settings
        └── Security Settings
```

```
User Configuration
└── Policies
    └── Administrative Templates
```

The policies I chose to configure were:

- Minimum password length

- Disable guest account

- Prohibit access to Control Panel

<img width="512" height="288" alt="image" src="https://github.com/user-attachments/assets/388f6f5b-17c3-45bb-b744-73b53e1a649e" />
<img width="512" height="288" alt="image" src="https://github.com/user-attachments/assets/26755baf-e8c9-45f4-b713-7ca8fb719ddd" />
<img width="512" height="288" alt="image" src="https://github.com/user-attachments/assets/401db03b-c000-4c67-a8cb-464262630945" />

---

### Key Takeaways and Conclusion

Group Policy Objects provide a centralized mechanism for managing configuration and security settings across an Active Directory domain. Effective GPO deployment depends heavily on proper OU design, as policies only apply within their linked scope. Separating computer-based and user-based settings within a GPO helps maintain clarity and ensures policies target the appropriate objects. GPOs can be linked at various levels of the domain hierarchy to support organizational requirements, while security filtering allows administrators to precisely control which users or computers are affected. Enforced GPOs should be used selectively, as most department-level policies are intended to inherit normally without overriding OU structure.
