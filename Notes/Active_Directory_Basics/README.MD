# Active Directory Basics - TryHackMe Lab

This repository contains my notes and write-up for the **Active Directory Basics** TryHackMe room.  
As I use Active Directory in my day-to-day role as a Service Desk Analyst, I already have familiarity with its concepts. This lab will help reinforce the fundamentals and view AD from both administrative and security perspectives.  

---

## Task 1 - Introduction
Notes:  

- Active Directory is the backbone of corporate networks.  
- Simplifies management of devices and users in an organization.  
- This room will take a deep dive into the essentials of AD.

Screenshots:  

---

## Task 2 - Windows Domains
Notes:  

- In a small network, each computer can be configured individually, manually creating users and settings.  
- In larger organizations, this approach becomes unmanageable. Active Directory solves this problem.  
- A **Windows Domain** is a group of users and computers under centralized administration.  
- The server that runs this service is called a **Domain Controller (DC)**.  
- **Advantages**:
  - **Centralized Identity Management:** Users can be managed from a single location.  
  - **Security Policies:** Policies can be applied network-wide from AD.

Screenshots:  

---

## Task 3 - Active Directory
Notes:  

- The core of a Windows Domain is **Active Directory Domain Services (AD DS)**.  
- AD is a catalog of all "objects" in the network (users, groups, machines, printers, etc.).  

**Users**  
- Security principals that can be authenticated and assigned privileges.  
- Two types:  
  - **People:** Human employees.  
  - **Services:** Programs like IIS or MSSQL. Each service runs under a **service user account** with only the privileges needed to run that service.  

**Machines**  
- Each computer joining the domain gets a **machine object**.  
- Machines are security principals with automatic passwords (rotated regularly).  
- Machine accounts are named `<ComputerName>$`, e.g., `DC01$`.  

**Security Groups**  
- Used to assign permissions across the network.  
- Can contain users, machines, and even other groups.  
- Important default groups:  
  - **Domain Admins:** Full domain control  
  - **Service Operators:** Manage DCs, cannot change admin memberships  
  - **Backup Operators:** Access files for backup  
  - **Account Operators:** Manage user accounts  
  - **Domain Users:** All domain users  
  - **Domain Computers:** All computers in the domain  
  - **Domain Controllers:** All DCs  

**Security Groups vs OUs**  
- **OUs (Organisational Units):** Used to apply policies depending on role or department. One user per OU.  
- **Security Groups:** Used to grant permissions, e.g., access to shared folders or printers. Users can belong to multiple security groups.

Screenshots:  

---

## Task 4 - Managing Users in AD
Notes:  

# Deleting OUs
- To delete OUs, need to enable advanced features
- Once enabled, it gives you option to disable accidental deletion protection
- Once unticked, you can delete.

Screenshots:  
![Insufficient Privileges](https://github.com/adengfx/cybersecurity-refresh/blob/main/Notes/Active_Directory_Basics/screenshots/deletion_warning.png?raw=true)

![Advanced Features](https://github.com/adengfx/cybersecurity-refresh/blob/main/Notes/Active_Directory_Basics/screenshots/advanced_features.png?raw=true)

![Accidental Deletion](https://github.com/adengfx/cybersecurity-refresh/blob/main/Notes/Active_Directory_Basics/screenshots/accidental_deletion.png?raw=true)

# Delegation
- In AD you can give specific users control over some OUs. This is called delegation.
- Allows you to grant users specific privileges to perform advanced tasks without need of domain admin.
- This is used in IT Support. For example, giving access to reset passwords, add/remove users from groups.
- Below screenshots show the Delegation wizard.

Screenshots:  
![Delegate Control](https://github.com/adengfx/cybersecurity-refresh/blob/main/Notes/Active_Directory_Basics/screenshots/delegate_control.png?raw=true)

- After this, we are going to test Phillips' new control
- RDP via Attackbox using 'xfreerdp'
- Doesn't have privileges to open AD, so resetting via powershell, the command resets the password, Prompts you to change it and the second command is to ensure the password is changed on logon

Screenshots:  
![Delegate Control](https://github.com/adengfx/cybersecurity-refresh/blob/main/Notes/Active_Directory_Basics/screenshots/delegate_control.png?raw=true)

![Delegate Control Wizard](https://github.com/adengfx/cybersecurity-refresh/blob/main/Notes/Active_Directory_Basics/screenshots/delegate_control_wizard.png?raw=true)

![Adding User](https://github.com/adengfx/cybersecurity-refresh/blob/main/Notes/Active_Directory_Basics/screenshots/adding_user.png?raw=true)

![Adding Tasks](https://github.com/adengfx/cybersecurity-refresh/blob/main/Notes/Active_Directory_Basics/screenshots/delegate_tasks.png?raw=true)

![Delegation Wizard Completed](https://github.com/adengfx/cybersecurity-refresh/blob/main/Notes/Active_Directory_Basics/screenshots/complete_delegation.png?raw=true)

![Attackbox xfreerdp](https://github.com/adengfx/cybersecurity-refresh/blob/main/Notes/Active_Directory_Basics/screenshots/attackbox_rdp.png?raw=true)

![Phillip RDP](https://github.com/adengfx/cybersecurity-refresh/blob/main/Notes/Active_Directory_Basics/screenshots/phillip_rdp.png?raw=true)

![Resetting Password](https://github.com/adengfx/cybersecurity-refresh/blob/main/Notes/Active_Directory_Basics/screenshots/resetting_password_powershell.png?raw=true)

- After this, we were able to successfully log into sophies account and we get the change password prompt.

---

## Task 5 - Managing Computers in AD
Notes:  
Screenshots:  

---

## Task 6 - Group Policies
Notes:  
Screenshots:  

---

## Task 7 - Authentication Methods
Notes:  
Screenshots:  

---

## Task 8 - Trees, Forests and Trusts
Notes:  
Screenshots:  

---

## Task 9 - Conclusion
Notes:  
Screenshots:  
