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

## Introduction

### Linux Structure

Linux is a family of operating systems that are free and open-source.

Linux operating systems follow five principles:
1. Everything is a file
2. Small, single-purpose programs
3. Ability to chain programs together to perform complex tasks
4. Avoid captive user interfaces
5. Configuration data stored in a text file

Components of Linux include:
* **Bootloader**: Guides the booting process, which starts the operating system
* **OS kernel**: Manages the resources for a system's input and output (I/O) devices at the hardware level
* **Daemons**: Automatically run in the background and ensure that key functions like scheduling are working properly
* **OS shell**: Acts as an interface between the operating system and the user
* **Graphics server**: Allows graphical programs to run locally or remotely
* **Windows manager**: Allows the user to access and manage essential features and services of the operating system in a more visual and easy-to-learn manner
* **Utilities**: Perform particular functions for the user or another program

The Linux operating system can be broken down into layers.
* **Hardware**: Physical components in the system, such as the RAM, hard drive, and CPU
* **Kernel**: The core of the operating system that virtualizes and controls common computer hardware resources
* **Shell**: A command-line interface that can execute a user's commands
* **System utility**: Software that makes the operating system's functionality available to the user

The Linux operating system is structured in a tree-like hierarchy and is documented by the [Filesystem Hierarchy Standard](http://www.pathname.com/fhs/) (FHS).

<figure><img srcg="https://academy.hackthebox.com/storage/modules/18/NEW_filesystem.png" alt=""><figcaption><p>The Linux file system is structured in a tree-like hierarchy.</p></figcaption></figure>

The Linux filesystem contains the following directories:
* `/`: Contains all files required to boot the operating system and other filesystems
* `/bin`: Contains essential command binaries
* `/boot`: Contains static bootloader, kernel executable, and other files required to boot the operating systems
* `/dev`: Contains device files to facilitate access to hardware devices attached to the system
* `/etc`: Contains local system configuration files and configuration files for installed applications
* `/home`: Contains files for each user on the system
* `/lib`: Contains shared library files that are required for system boot
* `/media`: Acts as the mount point for external removable media devices such as USB drives
* `/mnt`: Acts as the temporary mount point for regular filesystems
* `/opt`: Contains optional files such as third-party tools
* `/root`: Acts as the root user's home directory
* `/sbin`: Contains executables used for system administration
* `/tmp`: Contains temporary files made by the operating systems and many programs
* `/usr`: Contains executables, libraries, man files, etc.
* `/var`: Contains variable data files such as log files, email in-boxes, web application related files, cron files, etc.

### Linux Distributions

We refer to individual operating systems in the Linux family as distributions, or distros for short. These distributions differ by the packages they include, the user interface they provide, and the tools they make available.
* Kali Linux is popular for cyber security specialists.
* Ubuntu is popular for desktop users.
* Debian is popular for servers and embedded systems.
* Red Hat Enterprise Linux and CentOS are popular for enterprise-level computing.

### Introduction to Shell

A Linux terminal, also called a shell or command line, provides a text-based input-output (I/O) interface that allows users and the system's kernel to interact. The most commonly used shell in Linux is the `Bourne-Again Shell` (BASH).

Terminal emulators are a type of software that emulate terminal functionality. This software allows text-based programs to be used within a graphical user interface (GUI). Command-line interfaces (CLI) run as additional terminals in a single terminal.

## The Shell

### Prompt Description

A prompt description is a string of characters on a terminal screen that indicates the system is waiting for our input. The prompt description often includes information such as the user, current working directory, privileges, etc. Here are examples of prompts:

```Shell
<username>@<hostname><current working directory>$
<username>@<hostname>[~]$
root@htb[/htb]#
```

As shown above, $ stands for user shell prompt (unprivileged) while # stands for root shell prompt (privilege). 

The prompt can be customized using special characters and variables in the shell’s configuration file (`.bashrc` for the Bash shell). Customization is useful for troubleshooting and logging. For example, customization could allow us to include a timestamp on each command, so that commands we made can later be filtered and sorted.

### Getting Help

Linux includes built-in functionality for us to view information about commands we are unfamiliar with. We can view the manual of a command with `man`:

```Shell
usr@htb[/htb]$ man <tool>
```

We can also view optional parameters without browsing through the complete documentation using the `--help` parameter:

```Shell
usr@htb[/htb]$ <tool> --help
usr@htb[/htb]$ <tool> -h
```

If we are unsure what command we are searching for, we can search the descriptions of all manual pages for tools with a given keyword using `apropos`:

```Shell
usr@htb[/htb]$ apropos <keyword>
```

### System Information

The following commands are useful tools often installed by default:
* `whoami`: Displays the current username
|`id`|Returns users identity and group membership|
|`hostname`|Sets or prints the name of current host system.|
|`uname`|Prints basic information about the operating system name and system hardware.|
|`pwd`|Returns working directory name.|
|`ifconfig`|The ifconfig utility is used to assign or to view an address to a network interface and/or configure network interface parameters.|
|`ip`|Ip is a utility to show or manipulate routing, network devices, interfaces and tunnels.|
|`netstat`|Shows network status.|
|`ss`|Another utility to investigate sockets.|
|`ps`|Shows process status.|
|`who`|Displays who is logged in.|
|`env`|Prints environment or sets and executes command.|
|`lsblk`|Lists block devices.|
|`lsusb`|Lists USB devices|
|`lsof`|Lists opened files.|
|`lspci`|Lists PCI devices.|

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

`pwd` can be used to see the current directory. `ls` is used to list and `cd` is used to change directory.
- Use `cd -` to jump into the directory one was last in
- Use [Ctrl] + [L] as a shortcut for `clean`
- Use [Ctrl] + [R] and type some target text to search through command history
### Working with Files and Directories
`touch` can be used to make files and `mkdir` can be used to make directories. `mkdir -p parent/directory` will add parent directories if they do not exist. `tree .` can be used to view the file structure of the current directory. `mv`and `cp` are used for moving (and renaming) and copying.

Use `stat <file>` to see file information!

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

### Editing Files

Editing is done with either `nano`or `vim`. Vim is a powerful and compact modal editor that is worth getting to know. `cat` can be used to view files.

### Find Files and Directories

Finding files fast is very useful.

```Shell
which <program>   # returns path to file that should be executed
				  # returns nothing if program does not exist

find <location> <options>  # possible options include:
						   # type -f (look for files)
						   # -name *.conf (look for .conf filenames)
						   # 2>/dev/null (hides error messages)

sudo updatedb
locate *.conf   # faster than find because uses database
				# has less options than find
```

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

A file descriptor (FD) indicates a connection maintained by the kernel to perform I/O operations.
1. Data Stream for Input (STDIN - 0)
	1. < is input file, << is input literal
2. Data Stream for Output (STDOUT - 1)
	1. > is write, >> is append
	2. | is redirect output from one program to another
3. Data Stream for Error Output (STDERR - 2)
	1. This is why there is a 2 in `2>/dev/null` when redirecting errors to a sinkhole (getting rid of them)

For example,

```Shell
find /etc/ -name *.conf 2>dev/null | grep systemd | wc -l
```

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

Pagers allow us to scroll through the file in an interactive view. Use `q`to quit the pager.

```Shell
more /etc/passwd    # leaves output in terminal after quitting
less /etc/passwd    # does not leave output in terminal after quitting
head /etc/passwd    # prints the first 10 lines of the file
tail /etc/passwd    # prints the last 10 lines of the file

cat /etc/passwd | sort    # sorts numerically or alphabetically
grep <pattern> <file>     # finds patterns (use -v to exclude patterns)
cut -d":" -f1             # cuts with the deliminator ":"
tr ":" " "                # replaces colon with space
column -t                 # displays results in tabular form
wc -l                     # counts number of lines in output
```

Also check out `awk` and `sed` for further sorting and manipulating results.

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

### Regular Expressions

Regexes are commonly used with `grep` and `sed`.

### Permission Management

Execute permissions for a directory are necessary to traverse a directory. These do not allow a user to modify or execute files within the directory.

```Shell
chmod a+r file     # u = owner, g = group, o = others, a = all users
chmod 754          # binary equivalent: 111 101 100

chown <user>:<group> <file/directory>     # change owner or
										 # change group assignments
```

Special permissions for files can be set using the Set User ID (SUID) and Set Group ID (SGID) bits. Sticky bits are a type of file permission that can be set on directories. These bits can be used to prevent the deletion and renaming of files within a directory by users other than the owner.

## System Management

### User Management

| **Command** | **Description**                                                                                                                                            |
| ----------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `sudo`      | Execute command as a different user.                                                                                                                       |
| `su`        | The `su` utility requests appropriate user credentials via PAM and switches to that user ID (the default user is the superuser). A shell is then executed. |
| `useradd`   | Creates a new user or update default new user information.                                                                                                 |
| `userdel`   | Deletes a user account and related files.                                                                                                                  |
| `usermod`   | Modifies a user account.                                                                                                                                   |
| `addgroup`  | Adds a group to the system.                                                                                                                                |
| `delgroup`  | Removes a group from the system.                                                                                                                           |
| `passwd`    | Changes user password.                                                                                                                                     |

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

### Package Management

Most package managers provide the following features:
- Package downloading
- Dependency resolution
- A standard binary package format
- Common installation and configuration locations
- Additional system-related configuration and functionality
- Quality control

| `dpkg`     | The `dpkg` is a tool to install, build, remove, and manage Debian packages. The primary and more user-friendly front-end for `dpkg` is aptitude.                                                                                                                                                                                                        |
| ---------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `apt`      | Apt provides a high-level command-line interface for the package management system.                                                                                                                                                                                                                                                                     |
| `aptitude` | Aptitude is an alternative to apt and is a high-level interface to the package manager.                                                                                                                                                                                                                                                                 |
| `snap`     | Install, configure, refresh, and remove snap packages. Snaps enable the secure distribution of the latest apps and utilities for the cloud, servers, desktops, and the internet of things.                                                                                                                                                              |
| `gem`      | Gem is the front-end to RubyGems, the standard package manager for Ruby.                                                                                                                                                                                                                                                                                |
| `pip`      | Pip is a Python package installer recommended for installing Python packages that are not available in the Debian archive. It can work with version control repositories (currently only Git, Mercurial, and Bazaar repositories), logs output extensively, and prevents partial installs by downloading all requirements before starting installation. |
| `git`      | Git is a fast, scalable, distributed revision control system with an unusually rich command set that provides both high-level operations and full access to internals.                                                                                                                                                                                  |

Debian-based Linux distributions use the `APT` package manager. A package is an archive file containing multiple ".deb" files. The `dpkg` utility is used to install programs from the associated ".deb" file. `APT` packages together all of the dependencies needed to install a program.

See repository characteristics by viewing the `/etc/apt/sources.list` file.

### Service and Process Management

There are two types of services: internal (ex. system startup services) and services installed by users (ex. server services). Such services, called daemons (identified by the letter d at the end of the program name), run in the background without any user interaction.

```Shell
systemctl start ssh    # start OpenSSH service
systemctl status ssh   # check if OpenSSH runs without errors
systemctl enable ssh   # run OpenSSH after startup
systelctl list-units --type=service    # list all services
journalctl -u ssh.service --no-pager   # check for errors in log
```

A process can be in the following states:
- Running
- Waiting (waiting for an event or system resource)
- Stopped
- Zombie (stopped but still has an entry in the process table).

```Shell
kill -l          # lists a signals that can be sent to a process
kill 9 <PID>     # force kill a frozen process
```

| **Signal** | **Description**                                                                                                          |
| ---------- | ------------------------------------------------------------------------------------------------------------------------ |
| `1`        | `SIGHUP` - This is sent to a process when the terminal that controls it is closed.                                       |
| `2`        | `SIGINT` - Sent when a user presses `[Ctrl] + C` in the controlling terminal to interrupt a process.                     |
| `3`        | `SIGQUIT` - Sent when a user presses `[Ctrl] + D` to quit.                                                               |
| `9`        | `SIGKILL` - Immediately kill a process with no clean-up operations.                                                      |
| `15`       | `SIGTERM` - Program termination.                                                                                         |
| `19`       | `SIGSTOP` - Stop the program. It cannot be handled anymore.                                                              |
| `20`       | `SIGTSTP` - Sent when a user presses `[Ctrl] + Z` to request for a service to suspend. The user can handle it afterward. |
Display background processes with `jobs`.  Use `SIGTSTP` to suspend a process, and then let that process run in the background `bg`. You can also do this automatically by putting `&` at the end of a command. `fg <ID>` will allow you to foreground a process.

Run several commands:
- Semicolon (`;`): ignores previous command results and errors
- Double `ampersand` characters (`&&`): runs only if previous commands succeed
- Pipes (`|`)

<details>

<summary>Use the "systemctl" command to list all units of services and submit the unit name with the description "Load AppArmor profiles managed internally by snapd" as the answer.</summary>

snapd.apparmor.service

Use `systemctl list-units --type=service | grep "Load"` to search for this service.

</details>

### Task Scheduling

Systemd is a service that can be used to set up processes and scripts to run at a specific time or time interval and specify specific events and triggers that will trigger a specific task.
1. Create a timer
2. Create a service
3. Activate the timer

We can also use Cron to schedule and automate processes. We setup a Cron daemon to store the tasks in a file called crontab and then tell the daemon where to run the tasks.

*See HTB Linux Fundamentals for specifics on how to do this with Systemd and Cron.*

<details>

<summary>What is the type of the service of the "syslog.service"?</summary>

notify

See detailed information about a service with the `systemctl show syslog.service` command.

</details>

### Network Services

The most important network services you should be familiar with are SSH, NFS, Apache, and VPN.
- OpenSSH: a free and open-source implementation of the Secure Shell (SSH) protocol that allows the secure transmission of data and commands over a network
- Network File System (NFS): a network protocol that allows us to store and manage files on remote systems as if they were stored on the local system
- Apache is widespread, but Python Web Server is a simple, fast alternative
- OpenVPN: a popular open-source VPN server available for various operating systems

### Working with Web Services

One of the most widespread web servers is Apache. Apache offers the possibility to create web pages dynamically using server-side scripting languages like PHP, Perl, or Ruby.

`curl` allows us to transfer files from the shell over protocols like HTTP, HTTPS, and FTP. `wget` is an alternative.

<details>

<summary>Find a way to start a simple HTTP server inside Pwnbox or your local VM using "npm". Submit the command that starts the web server on port 8080 (use the short argument to specify the port number).</summary>

http-server -p 8080

</details>

<details>

<summary>Find a way to start a simple HTTP server inside Pwnbox or your local VM using "php". Submit the command that starts the web server on the localhost (127.0.0.1) on port 8080.</summary>

php -S 127.0.0.1:8080

</details>

### Backup and Restore

When backing up data on an Ubuntu system, we can utilize tools such as:
- Rsync
- Deja Dup
- Duplicity

Rsync is an open-source tool that is particularly useful for transferring large amounts of data over the network. Combined with cron, rsync can be used to automatically backup files to a different server over SSH.

### File System Management

The Linux file system is a hierarchical structure that is composed of various components. At the top of this structure is the inode table. The inode table is a table of information associated with each file and directory on a Linux system. Files can be stored as files or directories.

The main tool for disk management on Linux is the `fdisk`, which allows us to create, delete, and manage partitions on a drive.

Each logical partition or drive needs to be assigned to a specific directory on Linux. This process is called mounting. Mounting involves attaching a drive to a specific directory, making it accessible to the file system hierarchy.
- The `mount` tool is used to mount file systems on Linux
- The `/etc/fstab` file is used to define the default file systems that are mounted at boot time
- We can unmount with `unmount` but we must first make sure that file system is not being used by any processes

When the system runs out of physical memory, the kernel transfers inactive pages of memory to the swap space, freeing up physical memory for use by active processes. This process is known as swapping.

<details>

<summary>How many partitions exist in our Pwnbox? (Format: 0)</summary>

3

Use `sudo fdisk -l` to see all of the partitions.

</details>

### Containerization

Containerization is a process of packaging and running applications in isolated environments, such as a container, virtual machine, or serverless environment. Containers, simulating a system or network, are useful for safely testing exploits or malware in a controlled environment.

*See HTB Linux Fundamentals for how to setup Docker and Linux containers.*

## Linux Networking

### Network Configuration

Managing and configuring networks can be done with tools like `ipconfig` or `ip`. We can also set the default gateway, edit DNS settings, and edit interfaces.

Network access control (NAC) is a security system that ensures that only authorized and compliant devices are granted access to the network.
- Discretionary access control (DAC): grants resource owners the responsibility of controlling access permissions to their resources
- Mandatory access control (MAC): determines resource access based on the resource's security level and the user's security level or process requesting access
- Role-based access control (RBAC): assigns permissions to users based on their roles within an organization

The most common network troubleshooting tools:
1. Ping
2. Traceroute
3. Netstat
4. Tcpdump
5. Wireshark
6. Nmap

Hardening is commonly done with SELinux, AppArmor, and TCP wrappers.

### Remote Desktop Protocols in Linux

The XServer is the user-side part of the `X Window System network protocol` (`X11` / `X`). The `X11` is a fixed system that consists of a collection of protocols and applications that allow us to call application windows on displays in a graphical user interface. `X11` is predominant on Unix systems and is completely unencrypted.

The `X Display Manager Control Protocol` (`XDMCP`) protocol used to manage remote X Window sessions on other machines. XDMCP is an insecure protocol and should not be used in any environment that requires high levels of security.

`Virtual Network Computing` (`VNC`) is a remote desktop sharing system based on the RFB protocol that allows users to control a computer remotely. It allows a user to view and interact with a desktop environment remotely over a network connection. VNC is generally considered to be secure. The most used tools for such kinds of connections are UltraVNC and RealVNC because of their encryption and higher security.

## Linux Hardening

### Linux Security

Security is a processes, not a product.

Some kernel versions have to be updated manually. Also, keep your packages up to date:

```Shell
apt update && apt dist-upgrade
```

Setup firewall rules and disallow password login and root user login via SSH. Do audits and follow some of these best practices:
- Removing or disabling all unnecessary services and software
- Removing all services that rely on unencrypted authentication mechanisms
- Ensure NTP is enabled and Syslog is running
- Ensure that each user has its own account
- Enforce the use of strong passwords
- Set up password aging and restrict the use of previous passwords
- Locking user accounts after login failures
- Disable all unwanted SUID/SGID binaries

TCP wrappers restrict access to certain services based on the hostname or IP address of the user requesting access. TCP wrappers use the following configuration files:
- /etc/hosts.allow
- /etc/hosts.deny

These files can be configured by adding specific rules to the files.

### Firewall Setup

Firewalls provide a security mechanism for controlling and monitoring network traffic between different network segments, such as internal and external networks or different network zones.

The iptables utility provides a flexible set of rules for filtering network traffic based on various criteria such as source and destination IP addresses, port numbers, protocols, and more.

| **Component** | **Description**                                                                                                                                                              |
| ------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `Tables`      | Tables are used to organize and categorize firewall rules.                                                                                                                   |
| `Chains`      | Chains are used to group a set of firewall rules applied to a specific type of network traffic.                                                                              |
| `Rules`       | Rules define the criteria for filtering network traffic and the actions to take for packets that match the criteria.                                                         |
| `Matches`     | Matches are used to match specific criteria for filtering network traffic, such as source or destination IP addresses, ports, protocols, and more.                           |
| `Targets`     | Targets specify the action for packets that match a specific rule. For example, targets can be used to accept, drop, or reject packets or modify the packets in another way. |
*See HTB Linux Fundamentals for details about each of these core components.*

### System Logs and Monitoring

System logs on Linux are a set of files that contain information about the system and the activities taking place on it.
- Kernel Logs: stored in `/var/log/kern.log`
- System Logs: stored in `var/log/syslog`
- Authentication Logs: stored in `/var/log/auth.log`
- Application Logs: stored in logs depending on application

| **Service**  | **Description**                                                                                             |
| ------------ | ----------------------------------------------------------------------------------------------------------- |
| `Apache`     | Access logs are stored in the /var/log/apache2/access.log file (or similar, depending on the distribution). |
| `Nginx`      | Access logs are stored in the /var/log/nginx/access.log file (or similar).                                  |
| `OpenSSH`    | Access logs are stored in the /var/log/auth.log file on Ubuntu and in /var/log/secure on CentOS/RHEL.       |
| `MySQL`      | Access logs are stored in the /var/log/mysql/mysql.log file.                                                |
| `PostgreSQL` | Access logs are stored in the /var/log/postgresql/postgresql-version-main.log file.                         |
| `Systemd`    | Access logs are stored in the /var/log/journal/ directory.                                                  |

- Security Logs: stored in logs such as `/var/log/fail2ban.log` (failed login attempts), `/var/log/ufw.log` (firewall), etc.

## Linux Distributions vs Solaris

### Solaris

Solaris is a Unix-based operating system known for its robustness, scalability, and support for high-end hardware and software systems. It is widely used in the banking, finance, and government sectors. It is also used in large-scale data centers, cloud computing environments, and virtualization platforms.

Solaris is propriety and differs from Linux in its filesystem, security, system monitoring, process and package management, and kernel and hardware support.

*See HTB Linux Fundamentals for key differences*.

## Tips and Tricks

### Shortcuts
- `[CTRL] + A` - Move the cursor to the `beginning` of the current line.
- `[CTRL] + E` - Move the cursor to the `end` of the current line.
- `[CTRL] + [←]` / `[→]` - Jump at the beginning of the current/previous word.
- `[ALT] + B` / `F` - Jump backward/forward one word.
- `[CTRL] + U` - Erase everything from the current position of the cursor to the `beginning` of the line.
- `[Ctrl] + K` - Erase everything from the current position of the cursor to the `end` of the line.
- `[CTRL] + L` - Clears the terminal. An alternative to this shortcut is the `clear` command you can type to clear our terminal.
- `[CTRL] + R` - Search through command history for commands we typed previously that match our search patterns.

***

[Home](https://app.gitbook.com/o/0kO27okC5uVB9ALX3rho/s/036xtfEIzcEdGegONXWM/) ⋅ [Work](https://app.gitbook.com/o/0kO27okC5uVB9ALX3rho/s/WaFS755Q4sf02CxLcghQ/) ⋅ [Thoughts](https://app.gitbook.com/o/0kO27okC5uVB9ALX3rho/s/s4QQPMntQ25hmJToKSOu/)
