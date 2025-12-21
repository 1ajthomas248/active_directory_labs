# Active Directory Labs (Azure)

## Overview

This repository documents a series of hands-on labs focused on deploying, managing, and extending on-premises Active Directory in a Microsoft Azure environment.

While cloud identity platforms are increasingly common, traditional Active Directory Domain Services (AD DS) remain foundational in many enterprise environments. These labs are designed to mirror real-world IT operations by starting with a core domain infrastructure and progressively layering administrative, security, and hybrid identity capabilities on top.

The environment built in the early labs is intentionally reused and expanded throughout the repository to reflect how Active Directory is managed in production systems.

## Lab Objectives

By completing these labs, the following skills are demonstrated:

- Deployment of Windows Server–based Active Directory in Azure

- Core identity and access management using AD DS

- Organizational unit (OU) design and group-based access control

- Group Policy creation and enforcement

- Domain-joined client configuration and validation

- Hybrid identity integration with Azure Entra ID

- Practical troubleshooting and validation techniques used in enterprise IT environments

## Lab Breakdown

### Lab 01: Domain Controller Setup

Establishes the foundational environment by deploying a Windows Server virtual machine in Azure and promoting it to a Domain Controller. This lab covers AD DS installation, DNS configuration, and domain creation.

### Lab 02: Users, Groups, and Organizational Units

Introduces identity management fundamentals by creating users, security groups, and a logical OU structure aligned with common enterprise practices.

### Lab 03: Group Policy Management

Focuses on enforcing security and configuration standards through Group Policy Objects (GPOs), including password policies and user/device restrictions.

### Lab 04: Domain-Joined Client

Validates the Active Directory environment by joining a Windows client VM to the domain and confirming authentication, policy application, and user access behavior.

### Lab 05: Hybrid Identity with Azure Entra ID

Extends the on-premises Active Directory environment into Azure using directory synchronization, demonstrating a hybrid identity model commonly found in modern organizations.
