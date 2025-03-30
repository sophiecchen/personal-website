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

***

## Introduction

### Introduction to Windows

Windows is an operating system developed and managed by Microsoft. There are many versions of Windows operating systems, which differ by their version number and by their intended use (server vs personal).

We can find out information about our operating system in PowerShell using the `Get-WmiObject` cmdlet. The following command, for example, allows us to view the version and build number of our operating system.

```PowerShell
PS C:\htb> Get-WmiObject -Class win32_OperatingSystem | select Version,BuildNumber
```

We can also view processes with the `win32_Process` class to get a process listing, view services with `win32_Service` and view input-output information with `win32_Bios`.

In addition to accessing a computer running Windows locally, we can remotely access a computer running Windows over a network using the Remote Desktop Protocol (RDP) and the target computer's IP address. Remote access methods include:
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

In Windows operating systems, the root directory is `<drive_letter>:\` (`<drive_letter>` is commonly C). The root directory, or boot partition, is where the operating system is installed. Other physical and virtual drives are assigned other letters.

The directory structure of the root directory is as follows:
* **Perflogs**: Can hold Windows performance logs but is empty by default.
* **Program Files**: On 32-bit systems, all 16-bit and 32-bit programs are installed here. On 64-bit systems, only 64-bit programs are installed here.
* **Program Files (x86)**: 32-bit and 16-bit programs are installed here on 64-bit editions of Windows.                                  
* **ProgramData**: This is a hidden folder that contains data that is essential for certain installed programs to run. This data is accessible by the program no matter what user is running it.
* **Users**: This folder contains user profiles for each user that logs onto the system and contains the two folders Public and Default.
* **Default**: This is the default user profile template for all created users. Whenever a new user is added to the system, their profile is based on the Default profile.
* **Public**: This folder is intended for computer users to share files and is accessible to all users by default. This folder is shared over the network by default but requires a valid network account to access.
* **AppData**: Per user application data and settings are stored in a hidden user subfolder (i.e., cliff.moore\AppData). Each of these folders contains three subfolders. The Roaming folder contains machine-independent data that should follow the user's profile, such as custom dictionaries. The Local folder is specific to the computer itself and is never synchronized across the network. LocalLow is similar to the Local folder, but it has a lower data integrity level. Therefore it can be used, for example, by a web browser set to protected or safe mode.
* **Windows**: The majority of the files required for the Windows operating system are contained here.
* **System, System32, SysWOW64**: Contains all DLLs required for the core features of Windows and the Windows API. The operating system searches these folders any time a program asks to load a DLL without specifying an absolute path.
* **WinSxS**: The Windows Component Store contains a copy of all Windows components, updates, and service packs.

The Windows equivalent of `cd <directory>` is `dir <directory>`. As with Linux, we can use the `tree` utility to see the directory structure of a path or disk.

```PowerShell
PS C:\htb> tree c:\ /f | more
```

<details>

<summary>Find the non-standard directory in the C drive. Submit the contents of the flag file saved in this directory.</summary>

c8fe8d977d3a0c655ed7cf81e4d13c75

Use `cd` to navigate to the C drive. Go into the Academy directory (the non-standard directory).

</details>

### File System

Windows has five types of file systems: FAT12, FAT16, FAT32, NTFS, and exFAT. FAT12 and FAT16 are no longer used.

FAT32 (File Allocation Table) is widely used across many types of storage devices such as USB memory sticks and SD cards but can also be used to format hard drives. It provides device compatibility and operating system cross-compatibility but can only with files less than 4GB and size and lacks built-in data protection, file compression, and file encryption tools.

NTFS (New Technology File System) is the default Windows file system since Windows NT 3.1. In addition to making up for the shortcomings of FAT32, NTFS also has better support for metadata and better performance due to improved data structuring. NTFS provides reliability, security, large-sized partitions, and journaling. Most mobile devices and older media devices do not support NTFS.

The NTFS file system has the following key permission types: 
- **Full Control**: Allows reading, writing, changing, deleting of files/folders.
- **Modify**: Allows reading, writing, and deleting of files/folders.
- **List Folder Contents**: Allows for viewing and listing folders and subfolders as well as executing files. Folders only inherit this permission.
- **Read and Execute**: Allows for viewing and listing files and subfolders as well as executing files. Files and folders inherit this permission.
- **Write**: Allows for adding files to folders and subfolders and writing to a file.
- **Read**: Allows for viewing and listing of folders and subfolders and viewing a file's contents.
- **Traverse Folder**: This allows or denies the ability to move through folders to reach other files or folders, even without permissions to list the directory contents or view the files along the way.

Files and folders inherit the NTFS permissions of their parent folder. The `icacls` command can be used to view and set permissions.

These are the possible inheritance settings:
- `(CI)`: Container inherit
- `(OI)`: Object inherit
- `(IO)`: Inherit only
- `(NP)`: Do not propagate inherit
- `(I)`: Permission inherited from parent container

These are the basic access permissions available:
- `F`: Full access
- `D`: Delete access
- `N`: No access
- `M`: Modify access
- `RX`: Read and execute access
- `R`: Read-only access
- `W`: Write-only access

For example, we can use the command `icacls c:\users /grant joe:f` to grant the user joe full control over `c:\users`. Because `(oi)` and `(ci)` are not included in this command, however, the user joe will not have rights over subdirectories and files contained within `c:\users`. We can revoke those permissions using `icacls c:\users /remove joe`.

<details>

<summary>What system user has full control over the c:\users directory?</summary>

bob.smith

This can be found by viewing permissions for the directory using `icalcs c:\users`. 

</details>

### NTFS vs. Share Permissions

The `Server Message Block protocol` (`SMB`) is used in Windows to connect shared resources like files and printers.

<figure><img src="https://academy.hackthebox.com/storage/modules/49/smb_diagram.png" alt=""><figcaption><p>SMB uses requests nad responses to allow for the sharing of resources.</p></figcaption></figure>

NTFS and Share permissions are similar but not identical.

These are Share permissions:
- **Full Control**: Users are permitted to perform all actions given by Change and Read permissions as well as change permissions for NTFS files and subfolders
- **Change**: Users are permitted to read, edit, delete, and add files and subfolders
- **Read**: Users are allowed to view file & subfolder contents

These are NTFS basic permissions. NTFS also has additional special permissions.
- **Full Control**: Users are permitted to add, edit, move, delete files & folders as well as change NTFS permissions that apply to all allowed folders
- **Modify**: Users are permitted or denied permissions to view and modify files and folders. This includes adding or deleting files
- **Read & Execute**: Users are permitted or denied permissions to read the contents of files and execute programs
- **List folder contents**: Users are permitted or denied permissions to view a listing of files and subfolders
- **Read**: Users are permitted or denied permissions to read the contents of files
- **Write**: Users are permitted or denied permissions to write changes to a file and add new files to a folder
- **Special Permissions**: A variety of advanced permissions options

NTFS permissions apply to the system where the folder and files are hosted. Share permissions apply when the folder is being accessed through SMB, typically from a different system over the network.

Keep in mind that Windows Defender Firewall could potentially block access to the SMB share. To test whether this is occurring, completely deactivate each firewall profile in Windows or enable specific predefined inbound firewall rules in the Windows Defender Firewall advanced security settings. However, do not keep the firewall deactivated, as that can leave your system open to compromise.

*The Windows Fundamental module walks users through how to create and configure a network share in this section. I recommend that you access the module and follow along.*

<details>

<summary>What protocol discussed in this section is used to share resources on the network using Windows? (Format: case sensitive)</summary>

SMB

SMB stands for Server Message Block protocol.

</details>

<details>

<summary>What is the name of the utility that can be used to view logs made by a Windows system? (Format: 2 words, 1 space, not case sensitive)</summary>

Event Viewer

Event Viewer lets administrators and users view the event logs.

</details>

<details>

<summary>What is the full directory path to the Company Data share we created?</summary>

C:\Users\htb-student\Desktop\Company Data

The command `net share` can be used to view which shares we have created.

</details>

## Working with Services & Processes

### Windows Services & Processes

Services allow for the creation and management of long-running processes. Windows services are managed via the Service Control Manager (SCM) system, accessible via the `services.msc` MMC add-in.

The following command can be used to view services:

```Powershell
PS C:\htb> Get-Service | ? {$_.Status -eq "Running"} | select -First 2 |fl
```

Windows has three categories of services: Local Services, Network Services, and System Services. Services can usually only be created, modified, and deleted by users with administrative privileges.

These are critical Windows services that cannot be stopped and restarted without a system restart:
- `smss.exe`: Session Manager SubSystem. Responsible for handling sessions on the system.
- `csrss.exe`: Client Server Runtime Process. The user-mode portion of the Windows subsystem.
- `wininit.exe`: Starts the Wininit file .ini file that lists all of the changes to be made to Windows when the computer is restarted after installing a program.
- `logonui.exe`: Used for facilitating user login into a PC.
- `lsass.exe`: The Local Security Authentication Server verifies the validity of user logons to a PC or server. It generates the process responsible for authenticating users for the Winlogon service.
- `services.exe`: Manages the operation of starting and stopping services.
- `winlogon.exe`: Responsible for handling the secure attention sequence, loading a user profile on logon, and locking the computer when a screensaver is running.
- `System`: A background system process that runs the Windows kernel.
- `svchost.exe with RPCSS`: Manages system services that run from dynamic-link libraries (files with the extension .dll) such as "Automatic Updates," "Windows Firewall," and "Plug and Play." Uses the Remote Procedure Call (RPC) Service (RPCSS).
- `svchost.exe with Dcom/PnP`: Manages system services that run from dynamic-link libraries (files with the extension .dll) such as "Automatic Updates," "Windows Firewall," and "Plug and Play." Uses the Distributed Component Object Model (DCOM) and Plug and Play (PnP) services.

Critical processes include Windows Logon Application, System, System Idle Process, Windows Start-Up Application, Client Server Runtime, Windows Session Manager, Service Host, and Local Security Authority Subsystem Service (LSASS) process.

`lsass.exe` is the process that is responsible for enforcing the security policy on Windows systems and is thus a high value target.

The SysInternals Tools suite is a set of portable Windows applications that can be used to administer Windows systems (for the most part without requiring installation). Processes Explorer, in particular, can show which handles and DLL processes are loaded when a program runs. 

Task Manager provides information about running processes, system performance, running services, startup programs, logged-in users/logged in user processes, and services.

Process Explorer can show which handles and DLL processes are loaded when a program runs. This tool can also be used to analyze and troubleshoot parent-child process relationships.

<details>

<summary>Identify one of the non-standard update services running on the host. Submit the full name of the service executable (not the DisplayName) as your answer.</summary>

FoxitReaderUpdateService.exe

I looked through the Task Manger's Services tab to find the name of the service. Right click and press "Go to Details" to see the name of the service executable.

</details>

### Service Permissions

Service permissions and the permissions of the directories they execute from can be used by attackers to hide and execute malicious code. Thus, individual user accounts should be created to run critical network services. These are referred to as service accounts.

Most services run with LocalSystem privileges by default which is the highest level of access allowed on an individual Windows OS. Not all applications need Local System account-level permissions, so it is beneficial to perform research on a case-by-case basis when considering installing new applications in a Windows environment.

There are many ways to examine and manage services, including `services.msc`, `sc`, and `Get-Acl`. 

The following command queries a service:

```Shell
C:\htb> sc qc <service_name>
```

We can stop a service as such. Note that this action cannot be performed in a non-administrative context.

```Shell
C:\htb> sc stop <service_name>
```

We can examine service permissions as such:

```Shell
C:\htb> sc sdshow <service_name>
```

The output of the `sdshow` command may look something like `D:(A;;CCLCSWRPLORC;;;AU)(A;;CCDCLCSWRPWPDTLOCRSDRCWDWO;;;BA)(A;;CCDCLCSWRPWPDTLOCRSDRCWDWO;;;SY)S:(AU;FA;CCDCLCSWRPWPDTLOSDRCWDWO;;;WD)`. 

We can break this output into a few different parts:
- `D: (A;;CCLCSWRPLORC;;;AU)`: This portion is the security descriptor
    - `D:`: The proceeding characters are DACL permissions
    - `AU:`: Defines the security principal Authenticated Users
    - `A;;`: Access is allowed
    - `CC`: SERVICE_QUERY_CONFIG is the full name, and it is a query to the service control manager (SCM) for the service configuration
    - `LC`: SERVICE_QUERY_STATUS is the full name, and it is a query to the service control manager (SCM) for the current status of the service
    - `SW`: SERVICE_ENUMERATE_DEPENDENTS is the full name, and it will enumerate a list of dependent services
    - `RP`: SERVICE_START is the full name, and it will start the service
    - `LO`: SERVICE_INTERROGATE is the full name, and it will query the service for its current status
    - `RC`: READ_CONTROL is the full name, and it will query the security descriptor of the service
- `;;CCLCSWRPLORC;;;`: Each set of 2 characters in between the semi-colons represents actions allowed to be performed by a specific user or group
- `;;;AU`: These characters specify the security principal (User and/or Group) that is permitted to perform those actions
- `A;;`: The character immediately after the opening parentheses and before the first set of semi-colons defines whether the actions are Allowed or Denied.

## Interacting with Windows

### Windows Sessions

There are two types of sessions.
- Interactive (local logon): Initiated by a user authenticating to a local or domain system by entering their credentials
- Non-interactive: Initiated by three non-interactive accounts (listed below) by the Windows operating system to automatically start services and applications without requiring user interaction

There are three types of non-interactive accounts:
- **Local System Account**: Also known as the `NT AUTHORITY\SYSTEM` account, this is the most powerful account in Windows systems. It is used for a variety of OS-related tasks, such as starting Windows services. This account is more powerful than accounts in the local administrators group.
- **Local Service Account**: Known as the `NT AUTHORITY\LocalService` account, this is a less privileged version of the SYSTEM account and has similar privileges to a local user account. It is granted limited functionality and can start some services.
- **Network Service Account**: This is known as the `NT AUTHORITY\NetworkService` account and is similar to a standard domain user account. It has similar privileges to the Local Service Account on the local machine. It can establish authenticated sessions for certain network services.

### Interacting with the Windows Operating System

You can use a graphical user interface (GUI), the Remote Desktop Protocol (RDP), the command line, or PowerShell to interact with Windows.

PowerShell uses cmdlets, which are small single-function built-in tools. Many cmdlets, in addition to their regular name, also have aliases. We can use the `Get-Alias` cmdlet to get the aliases of different cmdlets.

Which scripts we can run on a system depends on the execution policy. Execution policies may need to be changed for certain scripts to run:
- **AllSigned**: All scripts can run, but a trusted publisher must sign scripts and configuration files. This includes both remote and local scripts. We receive a prompt before running scripts signed by publishers that we have not yet listed as either trusted or untrusted.
- **Bypass**: No scripts or configuration files are blocked, and the user receives no warnings or prompts.
- **Default**: This sets the default execution policy, `Restricted` for Windows desktop machines and `RemoteSigned` for Windows servers.
- **RemoteSigned**: Scripts can run but requires a digital signature on scripts that are downloaded from the internet. Digital signatures are not required for scripts that are written locally.
- **Restricted**: This allows individual commands but does not allow scripts to be run. All script file types, including configuration files (`.ps1xml`), module script files (`.psm1`), and PowerShell profiles (`.ps1`) are blocked.
- **Undefined**: No execution policy is set for the current scope. If the execution policy for ALL scopes is set to undefined, then the default execution policy of `Restricted` will be used.
- **Unrestricted**: This is the default execution policy for non-Windows computers, and it cannot be changed. This policy allows for unsigned scripts to be run but warns the user before running scripts that are not from the local intranet zone.

The execution policy is not meant to be a security control that restricts user actions since users can easily bypass the policy.
<details>

<summary>What is the alias set for the ipconfig.exe command?</summary>

ifconfig

The command `Get-Alias | findstr ipconfig` can be used to find aliases for ipconfig.exe.

</details>

<details>

<summary>Find the Execution Policy set for the LocalMachine scope.</summary>

Unrestricted

The Execution Policy can be found with the command `Get-ExecutionPolicy -List`.

</details>

### Windows Management Instrumentation (WMI)

WMI is a subsystem of PowerShell that provides system administrators with powerful tools for system monitoring. WMI can be used through PowerShell.
- **WMI service**: The Windows Management Instrumentation process, which runs automatically at boot and acts as an intermediary between WMI providers, the WMI repository, and managing applications.
- **Managed objects**: Any logical or physical components that can be managed by WMI.
- **WMI providers**: Objects that monitor events/data related to a specific object.
- **Classes**: These are used by the WMI providers to pass data to the WMI service.
- **Methods**: These are attached to classes and allow actions to be performed. For example, methods can be used to start/stop processes on remote machines.
- **WMI repository**: A database that stores all static data related to WMI.
- **CIM Object Manager**: The system that requests data from WMI providers and returns it to the application requesting it.
- **WMI API**: Enables applications to access the WMI infrastructure.
- **WMI Consumer**: Sends queries to objects via the CIM Object Manager.

WMI can be used to view the status information of local and remote systems, configure security settings and system properties, and more.

We can use WMI through PowerShell or the WMI Command-Line Interface (WMIC). For example, the following command gets information about the OS:

```Powershell
PS C:\htb> Get-WmiObject -Class Win32_OperatingSystem | select SystemDirectory,BuildNumber,SerialNumber,Version | ft
```

<details>

<summary>Use WMI to find the serial number of the system.</summary>

00329-10280-00000-AA938

Use the `Get-WmiObject -Class Win32_OperatingSystem | select SerialNumber | ft` command in PowerShell.

</details>

## Further Windows Usage

### Microsoft Management Console (MMC)

The MMC can be used to group snap-ins, or administrative tools, to manage hardware, software, and network components within a Windows host, and to create and distribute custom tools.

Type `mmc` in the Start Menu. Browse to `File -> Add` or Remove Snap-ins, and add the snap-ins you wish. Then, save your snap-ins as a .msc file.

### Windows Subsystem for Linux (WSL)

Windows Subsystem for Linux (WSL) allows Linux binaries to run on Windows. After enabling WSL and installing a Linux distro, we gain access to a Bash shell with the standard Linux directory structure. We can also access Windows files through the `/mnt` directory in WSL.

## Diving Deeper & Close Out

### Desktop Experience vs. Server Core

Windows Server Core is minimalistic server environment that only contains key server functionality. Server Core has lower management requirements, a smaller attack surface, and uses less disk space and memory than its traditional desktop counterpart, which is referred to as Desktop Experience. Unlike Desktop Experience, which uses a graphical user interface (GUI), all configuration and maintenance tasks are performed via the command-line, PowerShell, or remote management. Because it focuses on usability over efficiency, Windows Desktop Experience includes applications such as Mmc.exe and Control Panel that are not available on Server Core.

### Windows Security

Each of the security principals on Windows systems has a unique security identifier (SID). The system automatically generates SIDs.

Each SID has a pattern of the following form: `(SID)-(revision level)-(identifier-authority)-(subauthority1)-(subauthority2)-(etc)`
- `S`: SID - Identifies the string as a SID.
- `1`: Revision Level - To date, this has never changed and has always been `1`.
- `5`: Identifier-authority - A 48-bit string that identifies the authority (the computer or network) that created the SID.
- `21`: Subauthority1 - This is a variable number that identifies the user's relation or group described by the SID to the authority that created it. It tells us in what order this authority created the user's account.
- `674899381-4069889467-2080702030`: Subauthority2 - Tells us which computer (or domain) created the number.
- `1002`: Subauthority3 - The RID that distinguishes one account from another. Tells us whether this user is a normal user, a guest, an administrator, or part of some other group.

The Security Accounts Manager (SAM) grants rights to a network to execute speciic processes. The access rights themselves are managed by Access Control Entries (ACE) in Access Control Lists (ACL).

User Account Control (UAC) prevents malware from running or manipulating processes that could damage the computer or its contents.

This diagram shows how UAC works:

<figure><img src="https://academy.hackthebox.com/storage/modules/49/uacarchitecture1.png" alt=""><figcaption><p>UAC makes decisions based on a series of checks.</p></figcaption></figure>

The Registry is a hierarchical database in Windows critical for the operating system. It stores low-level settings for the Windows operating system and applications that choose to use it. It is divided into computer-specific and user-specific data. We can open the Registry Editor by typing `regedit` from the command line or Windows search bar.

This database consists of main folders (root keys) in which subfolders (subkeys) with their entries/files (values) are located. A root key starts with `HKEY`. These are the possible subkey values:
- `REG_BINARY`: Binary data in any form.
- `REG_DWORD`: A 32-bit number.
- `REG_DWORD_LITTLE_ENDIAN`: A 32-bit number in little-endian format. Windows is designed to run on little-endian computer architectures. Therefore, this value is defined as `REG_DWORD` in the Windows header files.
- `REG_DWORD_BIG_ENDIAN`: A 32-bit number in big-endian format. Some UNIX systems support big-endian architectures.
- `REG_EXPAND_SZ`: A null-terminated string that contains unexpanded references to environment variables (for example, "%PATH%"). It will be a Unicode or ANSI string depending on whether you use the Unicode or ANSI functions. To expand the environment variable references, use the `ExpandEnvironmentStrings` function.
- `REG_LINK`: A null-terminated Unicode string containing the target path of a symbolic link created by calling the `RegCreateKeyEx` function with `REG_OPTION_CREATE_LINK`.
- `REG_MULTI_SZ`: A sequence of null-terminated strings, terminated by an empty string (\0). The following is an example: String1\0String2\0String3\0LastString\0\0 The first \0 terminates the first string, the second to the last \0 terminates the last string, and the final \0 terminates the sequence. Note that the final terminator must be factored into the length of the string.
- `REG_NONE`: No defined value type.
- `REG_QWORD`: A 64-bit number.
- `REG_QWORD_LITTLE_ENDIAN`: A 64-bit number in little-endian format. Windows is designed to run on little-endian computer architectures. Therefore, this value is defined as `REG_QWORD` in the Windows header files.
- `REG_SZ`: A null-terminated string. This will be either a Unicode or an ANSI string, depending on whether you use the Unicode or ANSI functions.

Registry hives contain a logical group of keys, subkeys, and values to support software and files loaded into memory when the OS is started or a user logs in. These hives are useful for maintaining access to the system.

Other Windows features include AppLocker, Group Policy, and Windows Defender Antivirus.
- AppLocker is an application whitelisting solution.
- Group Policy allows administrators to set, configure, and adjust a variety of settings.
    - Group Policy can be accessed with `gpedit.msc`
- Windows Defender Antivirus is a built-in antivirus that ships for free with Windows operating systems.
    - Defender features include real-time protection and cloud-delivered protection, which works in conjunction with automatic sample submission to upload suspicious files for analysis.

<details>

<summary>Find the SID of the bob.smith user.</summary>

S-1-5-21-2614195641-1726409526-3792725429-1003

Use the `get-localuser | Select name,sid` command.

</details>

<details>

<summary>What 3rd party security application is disabled at startup for the current user? (The answer is case sensitive).</summary>

NordVPN

Applications disabled at startup can be viewed in the Startup tab of Task Manager.

</details>

### Skills Assessment - Windows Fundamentals

Before answering the questions below, complete the following steps:
1. Create a shared folder called called Company Data
2. Create a subfolder called HR inside of the Company Data folder
3. Create a user called Jim
    - Uncheck: User must change password at logon
4. Create a security group called HR
5. Add Jim to the HR security group
6. Add the HR security group to the shared Company Data folder and NTFS permissions list
    - Remove the default group that is present
    - Share Permissions: Allow Change & Read
    - Disable Inheritance before issuing specific NTFS permissions
    - NTFS permissions: Modify, Read & Execute, List folder contents, Read, Write
7.
    - Remove the default group that is present
    - Disable Inheritance before issuing specific NTFS permissions
    - NTFS permissions: Modify, Read & Execute, List folder contents, Read, and Write
8. Use PowerShell to list details about a service

<details>

<summary>What is the name of the group that is present in the Company Data Share Permissions ACL by default?</summary>

Everyone

Everyone is the default share permission for this folder.

</details>

<details>

<summary>What is the name of the tab that allows you to configure NTFS permissions?</summary>

Security

NTFS permissions can be configured in the Security tab.

</details>

<details>

<summary>What is the name of the service associated with Windows Update?</summary>

wuauserv

wuauserv, or the Windows Update Service, manages the downloading and installation of updates for the OS.

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
