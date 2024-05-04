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

# Linux Fundamentals Part 3

[TryHackMe Walkthroughs](./) ⋅ [Guided](../) ⋅ Linux Fundamentals Part 3

***

## Task 1:

## Task 3: Terminal Text Editors

<details>

<summary>Edit "task3" located in "tryhackme"'s home directory using Nano. What is the flag?</summary>

THM{TEXT\_EDITORS}

</details>

## Task 4: General/Useful Utilities

<details>

<summary>Download the file http://MACHINE_IP:8000/.flag.txt onto the TryHackMe AttackBox. Remember, you will need to do this in a new terminal.</summary>

THM{WGET\_WEBSERVER}

</details>

## Task 5: Processes 101

<details>

<summary>If we were to launch a process where the previous ID was "300", what would the ID of this new process be?</summary>

301

</details>

<details>

<summary>If we wanted to cleanly kill a process, what signal would we send it?</summary>

SIGTERM

</details>

<details>

<summary>Locate the process that is running on the deployed instance (MACHINE_IP). What flag is given?</summary>

THM{PROCESSES}

</details>

<details>

<summary>What command would we use to stop the service "myservice"?</summary>

systemctl stop myservice

</details>

<details>

<summary>What command would we use to start the same service on the boot-up of the system?</summary>

systemctl enable myservice

</details>

<details>

<summary>What command would we use to bring a previously backgrounded process back to the foreground?</summary>

fg

</details>

## Task 6: Maintaining Your System: Automation

<details>

<summary>When will the crontab on the deployed instance (MACHINE_IP) run?</summary>

@reboot

</details>

## Task 8: Maintaining Your System: Logs

<details>

<summary>What is the IP address of the user who visited the site?</summary>

10.9.232.111

</details>

<details>

<summary>What file did they access?</summary>

catsanddogs.jpg

</details>

***

[Home](https://app.gitbook.com/o/0kO27okC5uVB9ALX3rho/s/036xtfEIzcEdGegONXWM/) ⋅ [Work](https://app.gitbook.com/o/0kO27okC5uVB9ALX3rho/s/WaFS755Q4sf02CxLcghQ/) ⋅ [Thoughts](https://app.gitbook.com/o/0kO27okC5uVB9ALX3rho/s/s4QQPMntQ25hmJToKSOu/)
