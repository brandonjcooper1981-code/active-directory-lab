![Windows Server](https://img.shields.io/badge/Windows_Server-2025-blue)
![Active Directory](https://img.shields.io/badge/Active_Directory-Configured-success)
![VirtualBox](https://img.shields.io/badge/Oracle_VirtualBox-Lab-orange)
![Windows 11](https://img.shields.io/badge/Windows_11-Domain_Joined-success)

# Active Directory & File Server Lab

## Overview

Built a Windows Server 2022 Active Directory environment integrated with file sharing, NTFS permissions, security groups, and Group Policy.

### Technologies

- Windows Server 2022
- Windows 11
- Active Directory
- Group Policy
- SMB Shares
- NTFS Permissions
- Oracle VirtualBox

---

## Lab Architecture

DC01
- Active Directory
- DNS
- File Server

CLIENT01
- Domain Joined Workstation

Domain:
lab.local

---

# Active Directory Deployment

## Domain Controller

![DC01](screenshots/01-dc01-ipconfig.png)

## Domain Join Verification

![Domain Join](screenshots/02-domain-user-login.png)

## Organizational Units

Created:

- HR
- IT
- Sales
- Servers
- Workstations

![OU Structure](screenshots/03-active-directory-ou-structure.png)

## Group Policy

Configured:

- Password Complexity Enabled
- Minimum Password Length = 10

![GPO](screenshots/04-group-policy-configuration.png)

## Policy Verification

![GPResult](screenshots/05-gpo-verification.png)

---

# File Server & NTFS Permissions

## Department Shares

Created:

- HR
- IT
- Sales

![Shares](screenshots/06-file-server-shares.png)

## Security Groups

Created:

- HR_RW
- IT_RW
- Sales_RW

![Groups](screenshots/07-security-groups.png)

## NTFS Permissions

IT_RW assigned Modify access to IT folder.

![NTFS](screenshots/08-ntfs-permissions.png)

## SMB Share Permissions

![Share Permissions](screenshots/09-share-permissions.png)

---

# Access Testing

## Authorized Access

User jsmith successfully accessed:

\\DC01\IT

![Success](screenshots/10-share-access-success.png)

## Unauthorized Access

User denied access to:

\\DC01\HR

![Denied](screenshots/11-share-access-denied.png)

---

# Troubleshooting

## Issue: Domain Join Failed

**Cause:** CLIENT01 pointed to incorrect DNS server.

**Fix:** Configured DNS to:

192.168.56.10

---

## Issue: Group Policy Not Applying

**Cause:** CLIENT01 not located in Workstations OU.

**Fix:** Moved workstation to correct OU and ran:

gpupdate /force

---

## Issue: Access Denied to IT Share

**Cause:** Security group membership not refreshed.

**Fix:** Verified using:

whoami /groups

Logged off and back on.

---

# Skills Demonstrated

- Active Directory Administration
- Group Policy Management
- File Server Administration
- NTFS Permissions
- Security Groups
- Access Control
- Windows Server Administration
- Troubleshooting

---

# Author

Brandon Cooper

Cybersecurity | Active Directory | Windows Server | Networking
