# Active Directory Basics - TryHackMe Lab

This repository contains my notes and write-up for the **Active Directory Basics** TryHackMe room.  
As I use Active Directory in my day-to-day role as a Service Desk Analyst, I already have familiarity with its concepts. This lab helps reinforce the fundamentals and view AD from both administrative and security perspectives.

---

## Table of Contents
- [Task 1 - Introduction](#task-1---introduction)  
- [Task 2 - Windows Domains](#task-2---windows-domains)  
- [Task 3 - Active Directory](#task-3---active-directory)  
- [Task 4 - Managing Users in AD](#task-4---managing-users-in-ad)  
- [Task 5 - Managing Computers in AD](#task-5---managing-computers-in-ad)  
- [Task 6 - Group Policies (GPOs)](#task-6---group-policies-gpos)  
- [Task 7 - Authentication Methods](#task-7---authentication-methods)  
- [Task 8 - Trees, Forests, and Trusts](#task-8---trees-forests-and-trusts)  
- [Task 9 - Conclusion](#task-9---conclusion)  

---

## Task 1 - Introduction
- Active Directory (AD) is the backbone of most corporate networks.  
- It simplifies management of devices and users in an organization.  
- This room explores the essentials of AD.

---

## Task 2 - Windows Domains
- Small networks can manage users/computers individually, but this doesn’t scale.  
- A **Windows Domain** centralizes administration across many systems.  
- The server that manages domains is a **Domain Controller (DC)**.  

**Advantages**:
- Centralized identity management  
- Security policies applied network-wide  

<details>
<summary>Screenshots</summary>

<!-- Add any relevant screenshots here if available -->

</details>

---

## Task 3 - Active Directory
- Core service: **Active Directory Domain Services (AD DS)**.  
- AD is a catalog of **objects** (users, groups, machines, printers, etc.).  

**Users**
- Security principals that can authenticate and hold privileges.  
- Types:  
  - People (employees)  
  - Services (run under restricted service accounts)  

**Machines**
- Each device that joins the domain gets a **machine account** (`<ComputerName>$`).  
- Passwords are automatically rotated.  

**Security Groups**
- Assign permissions across the network.  
- Can include users, machines, or other groups.  
- Default groups: Domain Admins, Service Operators, Backup Operators, Account Operators, Domain Users, Domain Computers, Domain Controllers.  

**Security Groups vs OUs**
- **OUs (Organizational Units):** Apply policies, usually one OU per role/department.  
- **Security Groups:** Grant access (e.g., shared folders, printers). Users can belong to many groups.  

<details>
<summary>Screenshots</summary>

<!-- Add relevant screenshots -->

</details>

---

## Task 4 - Managing Users in AD

### Deleting OUs
- Enable advanced features → disable “Protect from accidental deletion” → delete OU.

### Delegation
- Delegation = giving non-admins specific control over OUs.  
- Common in IT Support (e.g., reset passwords, manage group memberships).  
- Tested by delegating control to a user, then verifying via RDP/PowerShell.  

<details>
<summary>Screenshots</summary>

![Insufficient Privileges](https://github.com/adengfx/cybersecurity-refresh/blob/main/Notes/Active_Directory_Basics/screenshots/deletion_warning.png?raw=true)  
![Advanced Features](https://github.com/adengfx/cybersecurity-refresh/blob/main/Notes/Active_Directory_Basics/screenshots/advanced_features.png?raw=true)  
![Accidental Deletion](https://github.com/adengfx/cybersecurity-refresh/blob/main/Notes/Active_Directory_Basics/screenshots/accidental_deletion.png?raw=true)  
![Delegate Control](https://github.com/adengfx/cybersecurity-refresh/blob/main/Notes/Active_Directory_Basics/screenshots/delegate_control.png?raw=true)  
![Delegate Control Wizard](https://github.com/adengfx/cybersecurity-refresh/blob/main/Notes/Active_Directory_Basics/screenshots/delegate_control_wizard.png?raw=true)  
![Adding User](https://github.com/adengfx/cybersecurity-refresh/blob/main/Notes/Active_Directory_Basics/screenshots/adding_user.png?raw=true)  
![Adding Tasks](https://github.com/adengfx/cybersecurity-refresh/blob/main/Notes/Active_Directory_Basics/screenshots/delegate_tasks.png?raw=true)  
![Delegation Wizard Completed](https://github.com/adengfx/cybersecurity-refresh/blob/main/Notes/Active_Directory_Basics/screenshots/complete_delegation.png?raw=true)  
![Attackbox xfreerdp](https://github.com/adengfx/cybersecurity-refresh/blob/main/Notes/Active_Directory_Basics/screenshots/attackbox_rdp.png?raw=true)  
![Phillip RDP](https://github.com/adengfx/cybersecurity-refresh/blob/main/Notes/Active_Directory_Basics/screenshots/phillip_rdp.png?raw=true)  
![Resetting Password](https://github.com/adengfx/cybersecurity-refresh/blob/main/Notes/Active_Directory_Basics/screenshots/resetting_password_powershell.png?raw=true)  

</details>

---

## Task 5 - Managing Computers in AD
- By default, new machines join the **Computers** container.  
- Best practice: organize devices into OUs like **Workstations**, **Servers**, and **Domain Controllers**.  

**Roles**:
- **Workstations:** User devices, should not host privileged accounts.  
- **Servers:** Provide services to users/other systems.  
- **Domain Controllers:** Manage AD itself; contain password hashes for all accounts (most sensitive).  

<details>
<summary>Screenshots</summary>

![Adding New OUs](https://github.com/adengfx/cybersecurity-refresh/blob/main/Notes/Active_Directory_Basics/screenshots/add_new_ou.png?raw=true)  
![New OUs](https://github.com/adengfx/cybersecurity-refresh/blob/main/Notes/Active_Directory_Basics/screenshots/workstations_servers.png?raw=true)  

</details>

---

## Task 6 - Group Policies (GPOs)
- OUs allow tailored policies for users/computers.  
- **Group Policy Objects (GPOs)** = collections of settings applied to OUs.  
- Default policies:  
  - **Default Domain Policy** → whole domain  
  - **Default Domain Controllers Policy** → DCs only  

**Distribution**
- Stored in **SYSVOL** share (`C:\Windows\SYSVOL\sysvol\`).  
- Sync interval: up to 2 hours, or force with `gpupdate /force`.  

**Examples**
- Enforcing password length.  
- Restricting Control Panel access.  

<details>
<summary>Screenshots</summary>

![Group Policy Management](https://github.com/adengfx/cybersecurity-refresh/blob/main/Notes/Active_Directory_Basics/screenshots/gpo_management.png?raw=true)  
![Default Domain Policy](https://github.com/adengfx/cybersecurity-refresh/blob/main/Notes/Active_Directory_Basics/screenshots/default_domain_policy.png?raw=true)  
![Group Policy Management Editor](https://github.com/adengfx/cybersecurity-refresh/blob/main/Notes/Active_Directory_Basics/screenshots/editing_gpo.png?raw=true)  
![Creating a GPO](https://github.com/adengfx/cybersecurity-refresh/blob/main/Notes/Active_Directory_Basics/screenshots/creating_gpo.png?raw=true)  
![Control Panel Restriction](https://github.com/adengfx/cybersecurity-refresh/blob/main/Notes/Active_Directory_Basics/screenshots/gpo_edit.png?raw=true)  
![Applying GPO to OUs](https://github.com/adengfx/cybersecurity-refresh/blob/main/Notes/Active_Directory_Basics/screenshots/gpu_ou.png)  

</details>

---

## Task 7 - Authentication Methods
Windows Domains store credentials in DCs. Two main protocols:  

**Kerberos (default)**  
- Uses encrypted tickets (TGT, TGS) instead of repeatedly sending credentials.  
- Provides secure, efficient authentication.  

**NetNTLM (legacy)**  
- Challenge-response mechanism.  
- Still supported for compatibility but considered obsolete.  

---

## Task 8 - Trees, Forests, and Trusts

**Trees**  
- Multiple domains sharing the same namespace (e.g., `thm.local`, `uk.thm.local`, `us.thm.local`).  

**Forests**  
- Union of multiple domain trees with different namespaces (e.g., company mergers).  

**Trust Relationships**  
- Allow cross-domain/forest access.  
- Types:  
  - One-way trust: users in Domain B can access resources in Domain A.  
  - Two-way trust: access works both directions.  
- Important: trust does **not** automatically grant access—permissions still need to be configured.  

<details>
<summary>Screenshots</summary>

![Trees](https://github.com/adengfx/cybersecurity-refresh/blob/main/Notes/Active_Directory_Basics/screenshots/tree.png?raw=true)  
![Forests](https://github.com/adengfx/cybersecurity-refresh/blob/main/Notes/Active_Directory_Basics/screenshots/forest.png?raw=true)  
![Trust Relationship](https://github.com/adengfx/cybersecurity-refresh/blob/main/Notes/Active_Directory_Basics/screenshots/trust_relationship.png?raw=true)  

</details>

---

## Task 9 - Conclusion
Active Directory is central to enterprise IT, enabling secure, centralized management of users, computers, and resources.  

**Key Takeaways**  
- Domains and DCs form the foundation.  
- AD objects (users, machines, groups) are the building blocks.  
- OUs and GPOs allow scalable, policy-driven administration.  
- Kerberos is the secure authentication standard, with NTLM retained for legacy support.  
- Trees, forests, and trusts provide flexibility for complex, multi-domain organizations.  
- Although I use AD on a daily basis as a Service Desk Analyst, this lab gave me deeper insight into AD’s structure, policies, and security implications. I learned a lot of new concepts and strengthened my foundation.  

This TryHackMe lab reinforced both the administrative structure and the security implications of AD—knowledge essential for IT operations and cybersecurity alike.
