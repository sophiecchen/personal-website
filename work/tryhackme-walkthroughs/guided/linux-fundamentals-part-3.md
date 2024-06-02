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

## Task 1: Introduction

In this room, we will learn about automation, package management, and service/application logging.

## Task 2: Deploy Your Linux Machine

To complete this room, we first need to deploy and log into the associated machine.

## Task 3: Terminal Text Editors

We can edit files with terminal text editors like Nano and Vim.

`nano <filename>` can be used to open or create a file in the text editor. Pressing `CTRL+X` will allow us to exit nano.

Vim is a much more advanced text editor. Its learning curve is higher but also includes advanced features and customizability.

<details>

<summary>Edit "task3" located in "tryhackme"'s home directory using Nano. What is the flag?</summary>

THM{TEXT\_EDITORS}

Navigate to "tryhackme"'s home directory and run `nano task3` to edit the file.

</details>

## Task 4: General/Useful Utilities

We can download files from the web via HTTP using `wget <address>`. We can copy files and folders between our local system and a remote system using secure copy. `scp <local_file> <remote_user>@<remote_destination>:<remote_file>` copies from our system to the remote system where `remote_file` specifies the name that we wish to store the file as on the remote system. `scp <remote_user>@<remote_destination>:<remote_file> <local_file>` copies from the remote system to our system where `local_file` specifies the name that we wish to store the file as on our local system.

Python3's "HTTPServer" allows us to serve files on the web and can be run with the command `python3 -m  http.server`.

<details>

<summary>Download the file http://MACHINE_IP:8000/.flag.txt onto the TryHackMe AttackBox. Remember, you will need to do this in a new terminal.</summary>

THM{WGET\_WEBSERVER}

First start a web server in the home directory of "tryhackme" with `python3 -m http.server`. Then, use `wget http://<machine_ip>:8000/.flag.txt` to download the file. Make sure to replace `<machine_ip>` with the IP of the machine. 

</details>

## Task 5: Processes 101

Processes are the programs that are running on your machine. They are managed by the kernel, where each process will have an ID associated with it, also known as its PID. PIDs are assigned by the order in which a process starts.

`ps` can be used to view processes running as our user session. `ps aux` includes processes run by other users and system processes.

`ps` gives you a one-time view of processes. In contrast, `top` can be used to see real-time statistics about the processes running on your system.

TODO

<details>

<summary>If we were to launch a process where the previous ID was "300", what would the ID of this new process be?</summary>

301

IDs are assigned by the order in which a process starts. If the previous ID was 300, then the next ID assigned will be 300 + 1 = 301.

</details>

<details>

<summary>If we wanted to cleanly kill a process, what signal would we send it?</summary>

SIGTERM

The SIGTERM signal kills a process but allows it to clean up beforehand.

</details>

<details>

<summary>Locate the process that is running on the deployed instance (MACHINE_IP). What flag is given?</summary>

THM{PROCESSES}

TODO

</details>

<details>

<summary>What command would we use to stop the service "myservice"?</summary>

systemctl stop myservice

`systemctl <option> <service>` TODO.

</details>

<details>

<summary>What command would we use to start the same service on the boot-up of the system?</summary>

systemctl enable myservice

TODO

</details>

<details>

<summary>What command would we use to bring a previously backgrounded process back to the foreground?</summary>

fg

`fg` brings a previously backgrounded process back to focus.

</details>

## Task 6: Maintaining Your System: Automation

TODO

<details>

<summary>When will the crontab on the deployed instance (MACHINE_IP) run?</summary>

@reboot

TODO

</details>

## Task 7: Maintaining Your System: Package Management

TODO

## Task 8: Maintaining Your System: Logs

As noted in [Linux Fundamentals Part 1](linux-fundamentals-part-1.md), logs are located in the `/var/log` folder in Linux. TODO.

<details>

<summary>What is the IP address of the user who visited the site?</summary>

10.9.232.111

TODO

</details>

<details>

<summary>What file did they access?</summary>

catsanddogs.jpg

TODO

</details>

## Task 9: Conclusions & Summaries

In conclusion, this room covered the following:
* Using terminal text editors
* General utilities such as downloading and serving contents using a python webserver
* A look into processes
* Maintaining & automating your system by the use of crontabs, package management, and reviewing logs

***

[Home](https://app.gitbook.com/o/0kO27okC5uVB9ALX3rho/s/036xtfEIzcEdGegONXWM/) ⋅ [Work](https://app.gitbook.com/o/0kO27okC5uVB9ALX3rho/s/WaFS755Q4sf02CxLcghQ/) ⋅ [Thoughts](https://app.gitbook.com/o/0kO27okC5uVB9ALX3rho/s/s4QQPMntQ25hmJToKSOu/)
