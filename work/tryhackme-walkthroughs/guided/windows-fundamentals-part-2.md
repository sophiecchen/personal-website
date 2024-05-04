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

# Windows Fundamentals Part 2

[TryHackMe Walkthroughs](./) ⋅ [Guided](../) ⋅ Windows Fundamentals Part 2

***

This room is part 2 in a 3-part series going over the fundamentals of the Windows operating system.

## Task 1:

## Task 2: System Configuration

<details>

<summary>What is the name of the service that lists Systems Internals as the manufacturer?</summary>

PsShutdown

Open System Configuration and click on the Service tab. I sorted by manufacturer to see which service had System Internals as the manufacturer.

</details>

<details>

<summary>Whom is the Windows license registered to?</summary>

Windows User

Launch About Windows in the Tools tab of System Configuration.

</details>

<details>

<summary>What is the command for Windows Troubleshooting?</summary>

C:\Windows\System32\control.exe /name Microsoft.Troubleshooting

Click on Windows Troubleshooting in the Tools tab of System Configuration.

</details>

<details>

<summary>What command will open the Control Panel? (The answer is the name of .exe, not the full path)</summary>

control.exe

</details>

## Task 3: Change UAC Settings

<details>

<summary>What is the command to open User Account Control Settings? (The answer is the name of the .exe file, not the full path)</summary>

UserAccountControlSettings.exe

Click on User Account Control Settings in the Tools tab of System Configuration.

</details>

## Task 4: Computer Management

<details>

<summary>What is the command to open Computer Management? (The answer is the name of the .msc file, not the full path)</summary>

compmgmt.msc

Click on Computer Management in the Tools tab of System Configuration.

</details>

<details>

<summary>At what time every day is the GoogleUpdateTaskMachineUA task configured to run?</summary>

6:15 AM

Launch Computer Management and go to the Task Scheduler tab.

</details>

<details>

<summary>What is the name of the hidden folder that is shared?</summary>

sh4r3dF0Ld3r

Launch Computer Management and go to the Shared Folders tab. Navigate to the Shares subfolder.

</details>

## Task 5: System Information

<details>

<summary>What is the command to open System Information? (The answer is the name of the .exe file, not the full path)</summary>

msinfo32.exe

Click on System Information in the Tools tab of System Configuration.

</details>

<details>

<summary>What is listed under System Name?</summary>

THM-WINFUN2

Launch System Information. This information is listed in the System Summary tab.&#x20;

</details>

<details>

<summary>Under Environment Variables, what is the value for ComSpec?</summary>

%SystemRoot%\system32\cmd.exe

Launch System Information. This information is listed under the Environment Variables tab of Software Environment.

</details>

## Task 6: Resource Monitor

<details>

<summary>What is the command to open Resource Monitor? (The answer is the name of the .exe file, not the full path)</summary>

resmon.exe

Click on Resource Monitor in the Tools tab of System Configuration.

</details>

## Task 7: Command Prompt

<details>

<summary>In System Configuration, what is the full command for Internet Protocol Configuration?</summary>

C:\Windows\System32\cmd.exe /k %windir%\system32\ipconfig.exe

Click on Internet Protocol Configuration in the Tools tab of System Configuration.

</details>

<details>

<summary>For the ipconfig command, how do you show detailed information?</summary>

ipconfig /all

Type `ipconfig -h` in the command prompt to view the manual page of `ipconfig`.

</details>

## Task 8: Registry Editor

<details>

<summary>What is the command to open the Registry Editor? (The answer is the name of the .exe file, not the full path)</summary>

regedt32.exe

Click on Registry Editor in the Tools tab of System Configuration.

</details>

***

[Home](https://app.gitbook.com/o/0kO27okC5uVB9ALX3rho/s/036xtfEIzcEdGegONXWM/) ⋅ [Work](https://app.gitbook.com/o/0kO27okC5uVB9ALX3rho/s/WaFS755Q4sf02CxLcghQ/) ⋅ [Thoughts](https://app.gitbook.com/o/0kO27okC5uVB9ALX3rho/s/s4QQPMntQ25hmJToKSOu/)
