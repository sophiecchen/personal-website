---
layout:
  title:
    visible: true
  description:
    visible: false
  tableOfContents:
    visible: false
  outline:
    visible: true
  pagination:
    visible: false
---

# Windows Fundamentals

[Hack The Box Walkthroughs](./) ⋅ [Academy](../) ⋅ Windows Fundamentals

***

## Introduction

### Introduction to Windows

These are the major Windows OSs and their associated version numbers:

|Operating System Names|Version Number|
|---|---|
|Windows NT 4|4.0|
|Windows 2000|5.0|
|Windows XP|5.1|
|Windows Server 2003, 2003 R2|5.2|
|Windows Vista, Server 2008|6.0|
|Windows 7, Server 2008 R2|6.1|
|Windows 8, Server 2012|6.2|
|Windows 8.1, Server 2012 R2|6.3|
|Windows 10, Server 2016, Server 2019|10.0|

```PowerShell
# Get version and build number
Get-WmiObject -Class win32_OperatingSystem | select Version,BuildNumber

# Get process listing
Get-WmiObject -Class win32_OperatingSystem (WIP)
Get-WmiObject -Class win32_OperatingSystem
Get-WmiObject -Class win32_OperatingSystem
```

Remote Access is accessing a computer over a network:
- Virtual Private Networks (VPN)
- Secure Shell (SSH)
- File Transfer Protocol (FTP)
- Virtual Network Computing (VNC)
- Windows Remote Management (or PowerShell Remoting) (WinRM)
- Remote Desktop Protocol (RDP)
- xfreerdp

<details>

<summary>What is the Build Number of the target workstation?</summary>

19041

Use the `Get-WmiObject -Class win32_OperatingSystem | select Version,BuildNumber` command to view the build number.

</details>

<details>

<summary>Which Windows NT version is installed on the workstation? (i.e. Windows X - case sensitive)</summary>

Windows 10

Use the `Get-WmiObject -Class win32_OperatingSystem | select Version,BuildNumber` command to view the version.

</details>

## Core of the Operating System

### Operating System Structure

In Windows operating systems, the root directory is <drive_letter>:\\ (commonly C drive). The root directory (also known as the boot partition) is where the operating system is installed. Other physical and virtual drives are assigned other letters.

The directory structure of the boot partition is as follows:

| Directory                  | Function                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| -------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Perflogs                   | Can hold Windows performance logs but is empty by default.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| Program Files              | On 32-bit systems, all 16-bit and 32-bit programs are installed here. On 64-bit systems, only 64-bit programs are installed here.                                                                                                                                                                                                                                                                                                                                                                                                                              |
| Program Files (x86)        | 32-bit and 16-bit programs are installed here on 64-bit editions of Windows.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| ProgramData                | This is a hidden folder that contains data that is essential for certain installed programs to run. This data is accessible by the program no matter what user is running it.                                                                                                                                                                                                                                                                                                                                                                                  |
| Users                      | This folder contains user profiles for each user that logs onto the system and contains the two folders Public and Default.                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| Default                    | This is the default user profile template for all created users. Whenever a new user is added to the system, their profile is based on the Default profile.                                                                                                                                                                                                                                                                                                                                                                                                    |
| Public                     | This folder is intended for computer users to share files and is accessible to all users by default. This folder is shared over the network by default but requires a valid network account to access.                                                                                                                                                                                                                                                                                                                                                         |
| AppData                    | Per user application data and settings are stored in a hidden user subfolder (i.e., cliff.moore\AppData). Each of these folders contains three subfolders. The Roaming folder contains machine-independent data that should follow the user's profile, such as custom dictionaries. The Local folder is specific to the computer itself and is never synchronized across the network. LocalLow is similar to the Local folder, but it has a lower data integrity level. Therefore it can be used, for example, by a web browser set to protected or safe mode. |
| Windows                    | The majority of the files required for the Windows operating system are contained here.                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| System, System32, SysWOW64 | Contains all DLLs required for the core features of Windows and the Windows API. The operating system searches these folders any time a program asks to load a DLL without specifying an absolute path.                                                                                                                                                                                                                                                                                                                                                        |
| WinSxS                     | The Windows Component Store contains a copy of all Windows components, updates, and service packs.                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
The Windows equivalent of `cd` is `dir`. Use the `tree` utility to see the directory structure of a path or disk.

```shell
tree c:\ /f | more
```

<details>

<summary>Find the non-standard directory in the C drive. Submit the contents of the flag file saved in this directory.</summary>

c8fe8d977d3a0c655ed7cf81e4d13c75

Use `cd` to navigate to the C drive. Go into the Academy directory (the non-standard directory).

</details>

### File System

FAT32 (File Allocation Table) is widely used across many types of storage devices such as USB memory sticks and SD cards but can also be used to format hard drives.

NTFS (New Technology File System) is the default Windows file system since Windows NT 3.1. In addition to making up for the shortcomings of FAT32, NTFS also has better support for metadata and better performance due to improved data structuring.

| Permission Type      | Description                                                                                                                                                                                                                                                                                                                                                                                |
| -------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Full Control         | Allows reading, writing, changing, deleting of files/folders.                                                                                                                                                                                                                                                                                                                              |
| Modify               | Allows reading, writing, and deleting of files/folders.                                                                                                                                                                                                                                                                                                                                    |
| List Folder Contents | Allows for viewing and listing folders and subfolders as well as executing files. Folders only inherit this permission.                                                                                                                                                                                                                                                                    |
| Read and Execute     | Allows for viewing and listing files and subfolders as well as executing files. Files and folders inherit this permission.                                                                                                                                                                                                                                                                 |
| Write                | Allows for adding files to folders and subfolders and writing to a file.                                                                                                                                                                                                                                                                                                                   |
| Read                 | Allows for viewing and listing of folders and subfolders and viewing a file's contents.                                                                                                                                                                                                                                                                                                    |
| Traverse Folder      | This allows or denies the ability to move through folders to reach other files or folders. For example, a user may not have permission to list the directory contents or view files in the documents or web apps directory in this example c:\users\bsmith\documents\webapps\backups\backup_02042020.zip but with Traverse Folder permissions applied, they can access the backup archive. |

The `icacls` can be used to view and set permissions.

Inherit permissions:
- `(CI)`: container inherit
- `(OI)`: object inherit
- `(IO)`: inherit only
- `(NP)`: do not propagate inherit
- `(I)`: permission inherited from parent container

Access permissions
- `F` : full access
- `D` :  delete access
- `N` :  no access
- `M` :  modify access
- `RX` :  read and execute access
- `R` :  read-only access
- `W` :  write-only access

<details>

<summary>What system user has full control over the c:\users directory?</summary>

bob.smith

</details>

### NTFS vs. Share Permissions

The `Server Message Block protocol` (`SMB`) is used in Windows to connect shared resources like files and printers.

![smb diagram](https://academy.hackthebox.com/storage/modules/49/smb_diagram.png)

NTFS and Share permissions are different. NTFS also includes special permissions. NTFS permissions apply to the system where the folder and files are hosted. Share permissions apply when the folder is being accessed through SMB, typically from a different system over the network. Note that Windows Defender Firewall could potentially block access to the SMB share.

*See HTB Windows Fundamentals for creating, managing, and viewing shares*.

<details>

<summary>What protocol discussed in this section is used to share resources on the network using Windows? (Format: case sensitive)</summary>

SMB

SMB stands for Server Message Block protocol.

</details>

<details>

<summary>What is the name of the utility that can be used to view logs made by a Windows system? (Format: 2 words, 1 space, not case sensitive)</summary>

Event Viewer

</details>

<details>

<summary>What is the full directory path to the Company Data share we created?</summary>

C:\Users\htb-student\Desktop\Company Data

</details>

## Working with Services & Processes

### Windows Services & Processes

Services allow for the creation and management of long-running processes. Windows services are managed via the Service Control Manager (SCM) system, accessible via the `services.msc` MMC add-in.

Windows has three categories of services: Local Services, Network Services, and System Services. Services can usually only be created, modified, and deleted by users with administrative privileges.

Critical services:

|Service|Description|
|---|---|
|smss.exe|Session Manager SubSystem. Responsible for handling sessions on the system.|
|csrss.exe|Client Server Runtime Process. The user-mode portion of the Windows subsystem.|
|wininit.exe|Starts the Wininit file .ini file that lists all of the changes to be made to Windows when the computer is restarted after installing a program.|
|logonui.exe|Used for facilitating user login into a PC|
|lsass.exe|The Local Security Authentication Server verifies the validity of user logons to a PC or server. It generates the process responsible for authenticating users for the Winlogon service.|
|services.exe|Manages the operation of starting and stopping services.|
|winlogon.exe|Responsible for handling the secure attention sequence, loading a user profile on logon, and locking the computer when a screensaver is running.|
|System|A background system process that runs the Windows kernel.|
|svchost.exe with RPCSS|Manages system services that run from dynamic-link libraries (files with the extension .dll) such as "Automatic Updates," "Windows Firewall," and "Plug and Play." Uses the Remote Procedure Call (RPC) Service (RPCSS).|
|svchost.exe with Dcom/PnP|Manages system services that run from dynamic-link libraries (files with the extension .dll) such as "Automatic Updates," "Windows Firewall," and "Plug and Play." Uses the Distributed Component Object Model (DCOM) and Plug and Play (PnP) services.|
These are critical processes: Windows Logon Application, System, System Idle Process, Windows Start-Up Application, Client Server Runtime, Windows Session Manager, Service Host, and Local Security Authority Subsystem Service (LSASS) process.

`lsass.exe` is the process that is responsible for enforcing the security policy on Windows systems and is thus a high value target.

The SysInternals Tools suite is a set of portable Windows applications that can be used to administer Windows systems (for the most part without requiring installation). Processes Explorer, in particular, can show which handles and DLL processes are loaded when a program runs. 

Task Manager provides information about running processes, system performance, running services, startup programs, logged-in users/logged in user processes, and services.

<details>

<summary>Identify one of the non-standard update services running on the host. Submit the full name of the service executable (not the DisplayName) as your answer.</summary>

FoxitReaderUpdateService.exe

I looked through the Task Manger's Services tab to find the name of the service. Right click and press "Go to Details" to see the name of the service executable.

</details>

### Service Permissions

It is highly recommended to create an individual user account to run critical network services. These are referred to as service accounts.

Most services run with LocalSystem privileges by default which is the highest level of access allowed on an individual Windows OS. Not all applications need Local System account-level permissions, so it is beneficial to perform research on a case-by-case basis when considering installing new applications in a Windows environment.

*See module to learn how to examine service permissions using services.msc, the sc command in Windows command line, and Get-Acl in PowerShell*.


## Interacting with Windows

### Windows Sessions

There are two types of sessions.
- Interactive (local logon): initiated by a user authenticating to a local or domain system by entering their credentials
- Non-interactive: initiated by three non-interactive accounts (listed below) by the Windows operating system to automatically start services and applications without requiring user interaction

|Account|Description|
|---|---|
|Local System Account|Also known as the `NT AUTHORITY\SYSTEM` account, this is the most powerful account in Windows systems. It is used for a variety of OS-related tasks, such as starting Windows services. This account is more powerful than accounts in the local administrators group.|
|Local Service Account|Known as the `NT AUTHORITY\LocalService` account, this is a less privileged version of the SYSTEM account and has similar privileges to a local user account. It is granted limited functionality and can start some services.|
|Network Service Account|This is known as the `NT AUTHORITY\NetworkService` account and is similar to a standard domain user account. It has similar privileges to the Local Service Account on the local machine. It can establish authenticated sessions for certain network services.|

### Interacting with the Windows Operating System

You can use GUI, RDP (remote desktop protocol), Windows command line, or PowerShell.

Execution policies may need to be changed for certain scripts to run:

|**Policy**|**Description**|
|---|---|
|`AllSigned`|All scripts can run, but a trusted publisher must sign scripts and configuration files. This includes both remote and local scripts. We receive a prompt before running scripts signed by publishers that we have not yet listed as either trusted or untrusted.|
|`Bypass`|No scripts or configuration files are blocked, and the user receives no warnings or prompts.|
|`Default`|This sets the default execution policy, `Restricted` for Windows desktop machines and `RemoteSigned` for Windows servers.|
|`RemoteSigned`|Scripts can run but requires a digital signature on scripts that are downloaded from the internet. Digital signatures are not required for scripts that are written locally.|
|`Restricted`|This allows individual commands but does not allow scripts to be run. All script file types, including configuration files (`.ps1xml`), module script files (`.psm1`), and PowerShell profiles (`.ps1`) are blocked.|
|`Undefined`|No execution policy is set for the current scope. If the execution policy for ALL scopes is set to undefined, then the default execution policy of `Restricted` will be used.|
|`Unrestricted`|This is the default execution policy for non-Windows computers, and it cannot be changed. This policy allows for unsigned scripts to be run but warns the user before running scripts that are not from the local intranet zone.|

<details>

<summary>What is the alias set for the ipconfig.exe command?</summary>

ifconfig

</details>

<details>

<summary>Find the Execution Policy set for the LocalMachine scope.</summary>

Unrestricted

</details>

### Windows Management Instrumentation (WMI)

WMI is a subsystem of PowerShell that provides system administrators with powerful tools for system monitoring. WMI can be used through PowerShell.

|**Component Name**|**Description**|
|---|---|
|WMI service|The Windows Management Instrumentation process, which runs automatically at boot and acts as an intermediary between WMI providers, the WMI repository, and managing applications.|
|Managed objects|Any logical or physical components that can be managed by WMI.|
|WMI providers|Objects that monitor events/data related to a specific object.|
|Classes|These are used by the WMI providers to pass data to the WMI service.|
|Methods|These are attached to classes and allow actions to be performed. For example, methods can be used to start/stop processes on remote machines.|
|WMI repository|A database that stores all static data related to WMI.|
|CIM Object Manager|The system that requests data from WMI providers and returns it to the application requesting it.|
|WMI API|Enables applications to access the WMI infrastructure.|
|WMI Consumer|Sends queries to objects via the CIM Object Manager.|

<details>

<summary>Use WMI to find the serial number of the system.</summary>

00329-10280-00000-AA938

Use the `Get-WmiObject -Class Win32_OperatingSystem | select SerialNumber | ft` command in PowerShell.

</details>

## Further Windows Usage

### Microsoft Management Console (MMC)

The MMC can be used to group snap-ins, or administrative tools, to manage hardware, software, and network components within a Windows host, and to create and distribute custom tools.

Type `mmc` in the Start Menu. Browse to File --> Add or Remove Snap-ins, and add the snap-ins you wish. Then, save your snap-ins as a .msc file.

### Windows Subsystem for Linux (WSL)

## Diving Deeper & Close Out

### Desktop Experience vs. Server Core

Windows Server Core is minimalistic Server environment only containing key Server functionality. Server Core has lower management requirements, a smaller attack surface, and uses less disk space and memory than its Desktop Experience (GUI) counterpart. All configuration and maintenance tasks are performed via the command-line, PowerShell, or remote management.

|**Application**|**Server Core**|**Desktop Experience**|
|---|---|---|
|Command prompt|Available|Available|
|Windows PowerShell/ Microsoft .NET|Available|Available|
|Regedit|Available|Available|
|Diskmgmt.msc|Not Available|Available|
|Server Manager|Not Available|Available|
|Mmc.exe|Not Available|Available|
|Eventvwr|Not Available|Available|
|Services.msc|Not Available|Available|
|Control Panel|Not Available|Available|
|Windows Explorer|Not Available|Available|
|Taskmgr|Available|Available|
|Internet Explorer or Edge|Not Available|Available|
|Remote Desktop Services|Available|Available|

### Windows Security

Each of the security principals on the system has a unique security identifier (SID). The system automatically generates SIDs

Each SID has a pattern:

(SID)-(revision level)-(identifier-authority)-(subauthority1)-(subauthority2)-(etc)

| **Example Number**              | **Meaning**          | **Description**                                                                                                                                                                                    |
| ------------------------------- | -------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| S                               | SID                  | Identifies the string as a SID.                                                                                                                                                                    |
| 1                               | Revision Level       | To date, this has never changed and has always been `1`.                                                                                                                                           |
| 5                               | Identifier-authority | A 48-bit string that identifies the authority (the computer or network) that created the SID.                                                                                                      |
| 21                              | Subauthority1        | This is a variable number that identifies the user's relation or group described by the SID to the authority that created it. It tells us in what order this authority created the user's account. |
| 674899381-4069889467-2080702030 | Subauthority2        | Tells us which computer (or domain) created the number                                                                                                                                             |
| 1002                            | Subauthority3        | The RID that distinguishes one account from another. Tells us whether this user is a normal user, a guest, an administrator, or part of some other group                                           |
The Registry is a hierarchical database in Windows critical for the operating system. It stores low-level settings for the Windows operating system and applications that choose to use it. It is divided into computer-specific and user-specific data. We can open the Registry Editor by typing `regedit` from the command line or Windows search bar.

*See the module for details on Security Accounts Manager (SAM), Access Control Entries (ACE), User Account Control (UAC), registry keys, whitelisting applications, AppLocker, Local Group Policy, and Windows Defender Antivirus.*

<details>

<summary>Find the SID of the bob.smith user.</summary>

S-1-5-21-2614195641-1726409526-3792725429-1003

Use the `get-localuser | Select name,sid` command.

</details>

<details>

<summary>What 3rd party security application is disabled at startup for the current user? (The answer is case sensitive).</summary>

NordVPN

</details>

### Skills Assessment - Windows Fundamentals

<details>

<summary>What is the name of the group that is present in the Company Data Share Permissions ACL by default?</summary>

Everyone

</details>

<details>

<summary>What is the name of the tab that allows you to configure NTFS permissions?</summary>

Security

</details>

<details>

<summary>What is the name of the service associated with Windows Update?</summary>

wuauserv

</details>

<details>

<summary>List the SID associated with the user account Jim you created.</summary>

S-1-5-21-2614195641-1726409526-3792725429-1006

Create Jim using Computer Management's Local Users and Groups tab. Then, use the `get-localuser | Select name,sid` command in PowerShell.

</details>

<details>

<summary>List the SID associated with the HR security group you created.</summary>

S-1-5-21-2614195641-1726409526-3792725429-1007

Create HR using Computer Management's Local Users and Groups tab. Then, use the `get-localgroup | Select name,sid` command in PowerShell.

</details>

***

[Home](https://app.gitbook.com/o/0kO27okC5uVB9ALX3rho/s/036xtfEIzcEdGegONXWM/) ⋅ [Work](https://app.gitbook.com/o/0kO27okC5uVB9ALX3rho/s/WaFS755Q4sf02CxLcghQ/) ⋅ [Thoughts](https://app.gitbook.com/o/0kO27okC5uVB9ALX3rho/s/s4QQPMntQ25hmJToKSOu/)
