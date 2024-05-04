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

This section TODO

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

<details>

<summary>Find the non-standard directory in the C drive. Submit the contents of the flag file saved in this directory.</summary>

c8fe8d977d3a0c655ed7cf81e4d13c75

Use `cd` to navigate to the C drive. Go into the Academy directory (the non-standard directory).

</details>

### File System

<details>

<summary>What system user has full control over the c:\users directory?</summary>

bob.smith

</details>

### NTFS vs. Share Permissions

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

<details>

<summary>Identify one of the non-standard update services running on the host. Submit the full name of the service executable (not the DisplayName) as your answer.</summary>

FoxitReaderUpdateService.exe

I looked through the Task Manger's Services tab to find the name of the service. Right click and press "Go to Details" to see the name of the service executable.

</details>

## Interacting with Windows

### Interacting with the Windows Operating System

<details>

<summary>What is the alias set for the ipconfig.exe command?</summary>

ifconfig

</details>

<details>

<summary>Find the Execution Policy set for the LocalMachine scope.</summary>

Unrestricted

</details>

### Windows Management Instrumentation (WMI)

<details>

<summary>Use WMI to find the serial number of the system.</summary>

00329-10280-00000-AA938

Use the `Get-WmiObject -Class Win32_OperatingSystem | select SerialNumber | ft` command in PowerShell.

</details>

## Diving Deeper & Close Out

### Windows Security

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
