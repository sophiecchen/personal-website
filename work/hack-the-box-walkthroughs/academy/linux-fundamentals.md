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

# Linux Fundamentals

[Hack The Box Walkthroughs](./) ⋅ [Academy](../) ⋅ Linux Fundamentals

***

## The Shell

### System Information

This section TODO

<details>

<summary>Find out the machine hardware name and submit it as the answer.</summary>

x86\_64

The `uname -i` command prints the hardware of the system.

</details>

<details>

<summary>What is the path to htb-student's home directory?</summary>

/home/htb-student

</details>

<details>

<summary>What is the path to the htb-student's mail?</summary>

/var/mail/htb-student

</details>

<details>

<summary>Which shell is specified for the htb-student user?</summary>

/bin/bash

</details>

<details>

<summary>Which kernel version is installed on the system? (Format: 1.22.3)</summary>

4.15.0

The `uname -v` command prints the kernel version.

</details>

<details>

<summary>What is the name of the network interface that MTU is set to 1500?</summary>

ens192

The `ipconfig` command allows us to see network interface information.

</details>

## Workflow

### Navigation

<details>

<summary>What is the name of the hidden "history" file in the htb-user's home directory?</summary>

.bash\_history

Type `ls -la` in the htb-user's home directory to see hidden files.

</details>

<details>

<summary>What is the index number of the "sudoers" file in the "/etc" directory?</summary>

147627

Navigate to the /etc directory with `cd`. `ls -i` lists the inode/index number of a file.

</details>

### Working with Files and Directories

<details>

<summary>What is the name of the last modified file in the "/var/backups" directory?</summary>

apt.extended\_states.0

Navigate to the /var/backups directory with `cd`. `ls -lat` lists files in order of last modified.

</details>

<details>

<summary>What is the inode number of the "shadow.bak" file in the "/var/backups" directory?</summary>

265293

Navigate to the /var/backups directory with `cd`. `ls -i` lists the inode/index number of a file.

</details>

### Find Files and Directories

<details>

<summary>What is the name of the config file that has been created after 2020-03-03 and is smaller than 28k but larger than 25k?</summary>

00-mesa-defaults.conf

Type `find / -name *.conf -size -28k -size +25k -newermt 2020-03-03 2>/dev/null`.

</details>

<details>

<summary>How many files exist on the system that have the ".bak" extension?</summary>

4

Type `find / -name *.bak -type f 2>/dev/null | wc -l`.  This searches for files with the .bak extension, excludes errors from output, and pipes the result into `wc -l`, which enumerates the results.

</details>

<details>

<summary>Submit the full path of the "xxd" binary.</summary>

/usr/bin/xxd

</details>

### File Descriptors and Redirections

<details>

<summary>How many files exist on the system that have the ".log" file extension?</summary>

32

Type `find / -name *.log -type f 2>/dev/null | wc -l`.  This searches for files with the .log extension, excludes errors from output, and pipes the result into `wc -l`, which enumerates the results.

</details>

<details>

<summary>How many total packages are installed on the target system?</summary>

737

`apt list --installed | wc -l` can be used to find the installed packages on the system and enumerate them.

</details>

### Filter Contents

<details>

<summary>How many services are listening on the target system on all interfaces? (Not on localhost and IPv4 only)</summary>

7

</details>

<details>

<summary>Determine what user the ProFTPd server is running under. Submit the username as the answer.</summary>

proftpd

</details>

<details>

<summary>Use cURL from your Pwnbox (not the target machine) to obtain the source code of the "https://www.inlanefreight.com" website and filter all unique paths of that domain. Submit the number of these paths as the answer.</summary>

34

</details>

## System Management

### User Management

<details>

<summary>Which option needs to be set to create a home directory for a new user using "useradd" command?</summary>

\-m

Use `useradd -h` to see options for this command.

</details>

<details>

<summary>Which option needs to be set to lock a user account using the "usermod" command? (long version of the option)</summary>

\--lock

Use `usermod -h` to see options for this command.

</details>

<details>

<summary>Which option needs to be set to execute a command as a different user using the "su" command? (long version of the option)</summary>

\--command

Use `man su` to see options for this command.

</details>

### Service and Process Management

<details>

<summary>Use the "systemctl" command to list all units of services and submit the unit name with the description "Load AppArmor profiles managed internally by snapd" as the answer.</summary>

snapd.apparmor.service

Use `systemctl list-units --type=service | grep "Load"` to search for this service.

</details>

### Task Scheduling

<details>

<summary>What is the type of the service of the "syslog.service"?</summary>

notify

See detailed information about a service with the `systemctl show syslog.service` command.

</details>

### Working with Web Services

<details>

<summary>Find a way to start a simple HTTP server inside Pwnbox or your local VM using "npm". Submit the command that starts the web server on port 8080 (use the short argument to specify the port number).</summary>

http-server -p 8080

</details>

<details>

<summary>Find a way to start a simple HTTP server inside Pwnbox or your local VM using "php". Submit the command that starts the web server on the localhost (127.0.0.1) on port 8080.</summary>

php -S 127.0.0.1:8080

</details>

### File System Management

<details>

<summary>How many partitions exist in our Pwnbox? (Format: 0)</summary>

3

Use `sudo fdisk -l` to see all of the partitions.

</details>

***

[Home](https://app.gitbook.com/o/0kO27okC5uVB9ALX3rho/s/036xtfEIzcEdGegONXWM/) ⋅ [Work](https://app.gitbook.com/o/0kO27okC5uVB9ALX3rho/s/WaFS755Q4sf02CxLcghQ/) ⋅ [Thoughts](https://app.gitbook.com/o/0kO27okC5uVB9ALX3rho/s/s4QQPMntQ25hmJToKSOu/)
