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

<figure><img src="https://academy.hackthebox.com/storage/modules/18/NEW_filesystem.png" alt=""><figcaption><p>The Linux file system is structured in a tree-like hierarchy.</p></figcaption></figure>

The Linux filesystem contains the following directories:
* `/`: Contains all files required to boot the operating system and other file systems
* `/bin`: Contains essential command binaries
* `/boot`: Contains static bootloader, kernel executable, and other files required to boot the operating systems
* `/dev`: Contains device files to facilitate access to hardware devices attached to the system
* `/etc`: Contains local system configuration files and configuration files for installed applications
* `/home`: Contains files for each user on the system
* `/lib`: Contains shared library files that are required for system boot
* `/media`: Acts as the mount point for external removable media devices such as USB drives
* `/mnt`: Acts as the temporary mount point for regular file systems
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

A Linux terminal, also called a shell or command line, provides a text-based input-output (I/O) interface that allows users and the system's kernel to interact. The most commonly used shell in Linux is the Bourne-Again Shell (BASH).

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

Linux includes built-in functionality for us to view information about commands we are unfamiliar with. We can view the manual of a command with `man`. Note that throughout this tutorial, I will use `<>` to signify placeholders that you can fill in.

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

Many useful tools are installed by default in Linux.

The following commands display or set basic information about the system:
* `whoami`: Displays the current username
* `id`: Returns user's identity and group membership
* `hostname`: Sets or prints the name of the current host system
* `uname`: Prints basic information about the operating system name and system hardware
* `pwd`: Returns working directory name
* `who`: Displays who is logged in
* `env`: Prints environment or sets and executes command
* `lsblk`: Lists block devices
* `lsusb`: Lists USB devices
* `lsof`: Lists opened files
* `lspci`: Lists PCI devices

The following commands display or set information relating to the networking functions of the system:
* `ifconfig`: Used to assign or to view an address to a network interface and used to configure network interface parameters
* `ip`: Used to show or manipulate routing, network devices, interfaces and tunnels
* `netstat`: Shows network status
* `ss`: Used to investigate sockets
* `ps`: Shows process status

We can also use `ssh <username>@<ip_address>` to securely log into a remote system.

<details>

<summary>Find out the machine hardware name and submit it as the answer.</summary>

x86\_64

The `uname -i` command prints the hardware of the system.

</details>

<details>

<summary>What is the path to htb-student's home directory?</summary>

/home/htb-student

Recall that user home directories are stored in `/home`. Navigate to the htb-student directory and type `pwd` to print the present working directory.

</details>

<details>

<summary>What is the path to the htb-student's mail?</summary>

/var/mail/htb-student

Recall that mail is stored in `/var`. Navigate to the htb-student's mail and type `pwd` to print the present working directory.

</details>

<details>

<summary>Which shell is specified for the htb-student user?</summary>

/bin/bash

Type `env` to print information about the environment and look for what `SHELL` is set to.

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
 
As mentioned in the previous section, typing `pwd` in the command line prints the current directory. We can navigate through our file system using `ls`, which lists files in our current directory, and `cd <directory>`, which allows us to change directories.

Here are some navigation shortcuts to improve your workflow:
- Use `cd -` to jump into the directory one was last in
- Use `cd ..` to move to the parent directory of the current directory
- Use `[CTRL] + [L]` as a shortcut for `clean`, which clears the terminal
- Use `[CTRL] + [R]` and type some target text to search through command history

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

`touch <file>` can be used to make files while `mkdir <directory>` can be used to make directories. As a shortcut, `mkdir -p <parent>/<directory>` will add parent directories if they do not exist.

`tree .` can be used to view the file structure of the current directory. `stat <file>` can be used to view file information.

`mv <file> <destination>`and `cp <file> <destination>` are used for moving (and renaming) and copying files or directories.

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

We can edit flies directly in the command line with text editors like Nano and Vim, which can be opened with `nano <file>` or `vim <file>`. Nano has a more approachable learning curve, but Vim is a powerful and compact modal editor that is worth getting to know.

If we just desire to view files without editing them, we can use `cat <file>` to print the contents directly to the terminal.

### Find Files and Directories

In a large system, finding the files and folders we need is crucial.

We can use `which <program>` to find the path to a file that is executed when running the program, if it exists.

`find <location> <options>` allows us to find files and folders and filter results. For example, adding `-type f` as an option allows us to look for files while `-name *.conf` allows us to look for files ending with ".conf". We should add `2>/dev/null` at the end of our command to hide error messages. 

`locate <file>` allows us to search through a local database about existing files and folders. Before running this command though, we should type `sudo updatedb` in order to update this database.

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

Type `which xxd` to find the "xxd" binary.

</details>

### File Descriptors and Redirections

A file descriptor (FD) indicates a connection maintained by the kernel to perform I/O operations. The first three Linux file descriptors are as follows: 
1. Data Stream for Input (STDIN - 0)
2. Data Stream for Output (STDOUT - 1)
3. Data Stream for Error Output (STDERR - 2)

We can use a file's contents as input using the `<` operator. We can input a literal instead of a file using `<<`.

```Shell
usr@htb[/htb]$ cat < <input file>
```

We can save the output of a command to a file using the `>` operator. We can append to a file rather than write to one using `>>`.

```Shell
usr@htb[/htb]$ cat > <output file>
```

A common application of this operator is to redirect errors in a command into the sinkhole `/dev/null`:
```Shell
usr@htb[/htb]$ <command> > 2>/dev/null
```

A pipe `|` allows us to redirect output from one program to another. For example, the following command searches for `.conf` files in `/etc`, and of those files, looks for those files which have "systemd" in their name.

```Shell
usr@htb[/htb]$ find /etc/ -name *.conf 2>/dev/null | grep systemd
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

We do not always need a file editor to view the contents of a file. Pagers allow us to scroll through the file in an interactive view. We can press `q` to quit the pager. `more <file>` opens in a file in a pager and leaves the file contents in the terminal after we quit the pager. `less <file>` also opens the file in the pager, but it does not leave the file contents in the terminal after we quit the pager.

If we just want to see part of a file, we can use `head <file>` to view the first 10 lines of the file and `tail <file>` to view the last 10 lines of the file.

We can sort the output of a file numerically or alphabetically with the `sort` command.

```Shell
usr@htb[/htb]$ cat /etc/passwd | sort 
```

We can use `grep <pattern> <file>` to find patterns in a file. By using the `-v` flag, we can exclude patterns in a file. For example, the following command exclude users who have disabled the standard shell.

```Shell
usr@htb[/htb]$ cat /etc/passwd | grep -v "false\|nologin"
``` 

`cut -d"<deliminator>" -f<number> <file>` allows us to take a string and separate it by a deliminator. For example, a possible output of the command `cat /etc/passwd | grep -v "false\|nologin" | cut -d":" -f1` is as follows:

```
root
sync
postgres
mrb3n
cry0l1t3
htb-student
```

`tr <replaced> <replace>` allows us to replace certain characters, while `column -t` allows us to display results in tabular form. For example, a possible output of the command `cat /etc/passwd | grep -v "false\|nologin" | tr ":" " " | column -t` is as follows:

```
root         x  0     0      root               /root        		 /bin/bash
sync         x  4     65534  sync               /bin         		 /bin/sync
postgres     x  111   117    PostgreSQL         administrator,,,    /var/lib/postgresql		/bin/bash
mrb3n        x  1000  1000   mrb3n              /home/mrb3n  	     /bin/bash
cry0l1t3     x  1001  1001   /home/cry0l1t3     /bin/bash
htb-student  x  1002  1002   /home/htb-student  /bin/bash
```

We can use `awk '{print $1, $NF}'` to display only the first and last result of the line, and `sed` will allow us to search and replace more complex character patterns.

Knowing how many successful matches result from a command is often helpful. `wc -l` can be used to count the number of lines in an output.

<details>

<summary>How many services are listening on the target system on all interfaces? (Not on localhost and IPv4 only)</summary>

7

This can be found with the command `netstat -tunl4 | grep "LISTEN" | wc -l`.

</details>

<details>

<summary>Determine what user the ProFTPd server is running under. Submit the username as the answer.</summary>

proftpd

This can be found with the command `cat /etc/passwd | grep "proftpd"`.

</details>

<details>

<summary>Use cURL from your Pwnbox (not the target machine) to obtain the source code of the "https://www.inlanefreight.com" website and filter all unique paths of that domain. Submit the number of these paths as the answer.</summary>

34

This can be found with the command `curl https://www.inlanefreight.com > temp`. We can then search the temp file we created for unique paths. 

</details>

### Regular Expressions

Regular expressions, or regexes, allow us to search for patterns in text and files. Regexes are commonly used with the `grep` and `sed` commands.

The basic syntax of regexes is as follows:
- `(a)`: Parentheses are used to group parts of a regex.
- `[a-z]`: Brackets are used to define character classes.
- `{1, 10}`: Curly braces are used to define a number or range of numbers that indicate the how many repetitions of a previous pattern you are looking for.
- `|`: The OR operator matches when one of the two expressions matches.
- `.*`:  This works similarly to the AND operator and only matches when both of the two expressions match. 

For example, the following regex finds lines in `<file>` that either contain the string "my" or "false".

```Shell
usr@htb[/htb]$ grep -E "(my|false)" <file>
```

The following regex finds lines in `<file>` that contain both the string "my" and "false".

```Shell
usr@htb[/htb]$ grep -E "(my.*false)" <file>
```

### Permission Management

Permissions in Linux are assigned to both users and groups. Linux permissions dictate who can access, modify, and run which resources. There are three permissions in Linux:
- `(r)`: Read
- `(w)`: Write
- `(x)`: Execute

Permissions can be specified for the resource owner, group, and others.

Note that execute permissions for a directory are necessary to traverse a directory. This does not allow a user to modify or execute files within the directory.

We can view the permissions of a file with `ls -l`. Here is an example output of `ls -l shell`:

```
-rwxr-x--x   1 cry0l1t3 htbteam 0 May  4 22:12 shell
```

The above output signifies that for the `shell` file, the owner `cry0l1t3` has read, write, and execute permissions. The group `htbteam` has read and execute permissions, and other users have execute permissions.

We can change permissions of a resource with `chmod <change> <resource>`. The following commands are equivalent:

```Shell
usr@htb[/htb]$ chmod a+r <resource>
usr@htb[/htb]$ chmod 754 <resource>
```

Notice that `a+r` means that we add read permissions to all users. `u` can be used for the owner, `g` can be used for the group, and `o` can be used for others. The code 754 is used to change permissions for the owner, group, and others all at once. 754 is equivalent to 111 101 100 in binary. This means that the owner has read, write, and execute permissions, the group has read and execute permissions, and other users have read permissions. 

We can also change the owner and group assignments of a file:

```Shell
usr@htb[/htb]$ chown <user>:<group> <file>
```

Special permissions for files can be set using the Set User ID (SUID) and Set Group ID (SGID) bits. These bits function like temporary access passes and allow a file to be run with the permissions of the file's owner or group. Special permissions are specified by an `s` in the spot of the usual `x` permission.

Sticky bits are a type of file permission that can be set on directories. These bits can be used to prevent the deletion and renaming of files within a directory by users other than the owner. Sticky bits are specified by an `T` or `t` in the spot of the usual `x` permission.

## System Management

### User Management

User management is fundamental for system administration. The following commands are helpful for managing users:
- `sudo`: Execute command as a different user.
- `su`: The `su` utility requests appropriate user credentials via PAM and switches to that user ID (the default user is the superuser). A shell is then executed.
- `useradd`: Creates a new user or update default new user information.
- `userdel`: Deletes a user account and related files.
- `usermod`: Modifies a user account.
- `addgroup`: Adds a group to the system.
- `delgroup`: Removes a group from the system.
- `passwd`: Changes user password.

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

Here are common package managers in Linux:
- `dpkg`: The `dpkg` is a tool to install, build, remove, and manage Debian packages. The primary and more user-friendly front-end for `dpkg` is aptitude.
- `apt`: Apt provides a high-level command-line interface for the package management system.
- `aptitude`: Aptitude is an alternative to apt and is a high-level interface to the package manager.
- `snap`: Install, configure, refresh, and remove snap packages. Snaps enable the secure distribution of the latest apps and utilities for the cloud, servers, desktops, and the internet of things.
- `gem`: Gem is the front-end to RubyGems, the standard package manager for Ruby.
- `pip`: Pip is a Python package installer recommended for installing Python packages that are not available in the Debian archive. It can work with version control repositories (currently only Git, Mercurial, and Bazaar repositories), logs output extensively, and prevents partial installs by downloading all requirements before starting installation.
- `git`: Git is a fast, scalable, distributed revision control system with an unusually rich command set that provides both high-level operations and full access to internals.

Debian-based Linux distributions use the `apt` package manager. A package is an archive file containing multiple ".deb" files. The `dpkg` utility is used to install programs from the associated ".deb" file. `apt` packages together all of the dependencies needed to install a program.

We can see repository characteristics by viewing the `/etc/apt/sources.list` file. We can also check the `apt-cache` for information about packages installed on our system offline.

We can list all installed packages with `apt`:

```Shell
usr@htb[/htb]$ apt list --installed
```

We can install packages as such: 

```Shell
usr@htb[/htb]$ sudo apt install <package>
```

We can also download open-source code manually with `git`. `git clone <link>` can be used to clone repositories from Github.

### Service and Process Management

Services, or daemons, run silently in the background of a Linux system without direct user interaction. There are two types of services: internal (ex. system startup services) and services installed by users (ex. server services).

Daemons are often identified by the letter d at the end of the program name. 

Most modern Linux distributions use `systemd` as their initialization system, which is the first process that starts during booting. All processes in a Linux system are assigned a PID and can be viewed under the `/proc/` directory. Processes may also have a Parent Process ID (PPID), indicating that they were started by another parent process.

We can start a service as such:

```Shell
usr@htb[/htb]$ systemctl start <service>
```

We can check that the service runs without errors as such: 

```Shell
usr@htb[/htb]$ systemctl status <service>
```

We can also use `systemctl` to run a service on startup and list all services. 

if our service is `ssh`, for example, we can view the logs of the service using `journalctl -u ssh.service --no-pager`.

A process can be in the following states:
- Running
- Waiting (waiting for an event or system resource)
- Stopped
- Zombie (stopped but still has an entry in the process table).

We can force kill a frozen process with `kill 9 <PID>`. Notice how 9 is the signal sent to the process.

These are the most commonly used signals:
- **1**: `SIGHUP` - This is sent to a process when the terminal that controls it is closed.
- **2**: `SIGINT` - Sent when a user presses `[Ctrl] + C` in the controlling terminal to interrupt a process.
- **3**: `SIGQUIT` - Sent when a user presses `[Ctrl] + D` to quit.
- **9**: `SIGKILL` - Immediately kill a process with no clean-up operations.
- **15**: `SIGTERM` - Program termination.
- **19**: `SIGSTOP` - Stop the program. It cannot be handled anymore.
- **20**: `SIGTSTP` - Sent when a user presses `[Ctrl] + Z` to request for a service to suspend. The user can handle it afterward.

We can background a process with `bg` or by placing `&` at the end of a command. We can then display background processes with `jobs`. `fg <PID>` will allow us to foreground a backgrounded process.

There are three ways that we can execute several commands:
- Semicolon (`;`): Runs following commands even if previous commands error
- Double `ampersand` characters (`&&`): Runs following commands only if previous commands succeed
- Pipes (`|`): Allow us to pass the results from a previous command to the next command

<details>

<summary>Use the "systemctl" command to list all units of services and submit the unit name with the description "Load AppArmor profiles managed internally by snapd" as the answer.</summary>

snapd.apparmor.service

Use `systemctl list-units --type=service | grep "Load"` to search for this service.

</details>

### Task Scheduling

Task scheduling is a feature of Linux that allows users and administrators to automate tasks by running them at specific times or regular intervals.

Systemd is a service that can be used to set up processes and scripts to run at a specific time or time interval. This service also allows us to specify specific events and triggers that will trigger a specific task.
1. Create a timer
2. Create a service
3. Activate the timer

We can create a timer by first creating a directory for the timer script. Here is an example of a timer script:

```
[Unit]
Description=My Timer

[Timer]
OnBootSec=3min
OnUnitActiveSec=1hour

[Install]
WantedBy=timers.target
```

We can then create a service:

```
[Unit]
Description=My Service

[Service]
ExecStart=/full/path/to/my/script.sh

[Install]
WantedBy=multi-user.target
```

To allow this service to run, we reload `systemd` and use `systemctl` to start the system manually or enable autostart.

Alternatively, we can use Cron to schedule and automate processes. We setup a Cron daemon to store the tasks we want to complete in a file called a crontab and then tell the daemon where to run the tasks.

Here is an example of a crontab:

```
# System Update
0 */6 * * * /path/to/update_software.sh

# Execute scripts
0 0 1 * * /path/to/scripts/run_scripts.sh

# Cleanup DB
0 0 * * 0 /path/to/scripts/clean_database.sh

# Backups
0 0 * * 7 /path/to/scripts/backup.sh
```

The numbers that prepend each line with a script indicate when each script should be run.

<details>

<summary>What is the type of the service of the "syslog.service"?</summary>

notify

See detailed information about a service with the `systemctl show syslog.service` command.

</details>

### Network Services

While there are many network services, these are must-knows:
- OpenSSH
- Network File System (NFS)
- Apache Web Server
- Python Web Server
- OpenVPN

Shell (SSH) is a protocol that allows the secure transmission of data and commands over a network. OpenSSH is a free and open-source implementation of SSH. We can SSH into a system using `ssh <user>@<ip>`.

Network File System (NFS) is a network protocol that allows us to store and manage files on remote systems as if they were stored on the local system. NFS directories, transfer speed, encryption, and permissions can be configured in `/etc/exports`.

These are the available permissions of NFS:
- `rw`: Gives users and systems read and write permissions to the shared directory.
- `ro`: Gives users and systems read-only access to the shared directory.
- `no_root_squash`: Prevents the root user on the client from being restricted to the rights of a normal user.
- `root_squash`: Restricts the rights of the root user on the client to the rights of a normal user.
- `sync`: Synchronizes the transfer of data to ensure that changes are only transferred after they have been saved on the file system.
- `async`: Transfers data asynchronously, which makes the transfer faster, but may cause inconsistencies in the file system if changes have not been fully committed.

A web server is software that delivers data, documents, applications, and various functions over the Internet. Apache web server is a widely used web server on Linux and is broadly compatible with various operating systems. Python is a simple alternative to the Apache web server. We can start a web server in our current directory using `python3 -m http.server <port>`.

A Virtual Private Network (VPN) functions like a secure, invisible tunnel that connects us to another network. OpenVPN popular open-source VPN server available for various operating systems. We can connect to an OpenVPN by saving the `.ovpn` file we received from the OpenVPN server and then running `sudo openvpn --config <file>.ovpn`.

### Working with Web Services

As stated in the previous section, one of the most widespread web servers is Apache Apache's true strength lies in its modularity—it can be customized and extended with various modules to perform specific tasks. Apache can handle static web pages and dynamic web pages created from server-side scripting languages like PHP, Perl, or Ruby. We can start an Apache web server using `sudo systemctl start apache2`. 

`curl` allows us to transfer files from the shell over protocols like HTTP, HTTPS, and FTP. `wget` is an alternative. As shown below, using `curl` and `wget` is similar: 

```Shell
usr@htb[/htb]$ curl <url>
usr@htb[/htb]$ wget <url>
```

As stated in the previous section, Python is an alternative to Apache. We can start a web server in our current directory using `python3 -m http.server <port>`.

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

The following command copies an entire directory to a remote host:

```Shell
usr@htb[/htb]$ rsync -av <path_to_local> <user>@<backup_server>:<path_to_backup>
```

If we want to restore, our backup, we can use the following command:

```Shell
usr@htb[/htb]$ rsync -av <user>@<remote_host>:/<path_to_backup> <path_to_local>
```

To use `rsync` with encryption, we can transfer our backup over SSH:

```Shell
usr@htb[/htb]$ rsync -avz -e ssh <path_to_local> <user>@<backup_server>:<path_to_backup>
```

Duplicity builds on Rsync and adds encryption features to protect the backups.

Deja Dup is a simpler, user-friendly option that offers a graphic interface. Like Duplicity, Deja Dup builds on Rsync and supports encrypted backups.

### File System Management

Linux supports many file systems, including ext2, ext3, ext4, XFS, Btrfs, and NTFS. Each of these file systems has different features, and the best choice depends on the needs of the computer system.

The Linux file system architecture is a hierarchical structure that is composed of various components, including inodes. Inodes are data structures that store metadata about each file and directory, including permissions, ownership, size, and timestamps.

At the top of this hierarchical structure is the inode table. The inode table is a table of information associated with each file and directory on a Linux system. Files can be stored as files, directories, or symbolic links (`symlinks`).

Linux disk management can be used to mange physical storage devices. The main tool for disk management on Linux is the `fdisk`, which allows us to create, delete, and manage partitions on a drive. Common partitioning tools in Linux include `fdisk`, `gpart`, and `GParted`.

Mounting is the process in which each logical partition or drive is assigned to a specific directory on Linux. Mounting involves attaching a drive to a specific directory, making it accessible to the file system hierarchy.
- The `mount` tool is used to mount file systems on Linux.
- The `/etc/fstab` file is used to define the default file systems that are mounted at boot time
- We can unmount with `unmount` but we must first make sure that file system is not being used by any processes

When the system runs out of physical memory, the kernel transfers inactive pages of memory to the swap space, freeing up physical memory for use by active processes. This process is known as swapping.
- `mkswap`: Creates a Linux swap area
- `swapon`: Actives the swap space for system use

Swap space is also used for hibernation, a power-saving feature that saves the system's state to the swap space so that when a system is turned on after being powered off, it can resume where it left off.

<details>

<summary>How many partitions exist in our Pwnbox? (Format: 0)</summary>

3

Use `sudo fdisk -l` to see all of the partitions.

</details>

### Containerization

Containerization is a process of packaging and running applications in isolated environments, such as a container, virtual machine, or serverless environment. Containers, simulating a system or network, are useful for safely testing exploits or malware in a controlled environment.

Docker is an open-source platform for automating the deployment of applications as self-contained units called containers. The Docker engine and specific Docker images are needed to run a container. These can be obtained from the Docker Hub, a repository of pre-made images, or created by the user. 

Creating a Docker image is done by creating a Dockerfile, which contains all the instructions the Docker engine needs to create the container. Once the Docker image has been created, it can be executed through the Docker engine easily and efficiently.

These are common commands for managing Docker containers:
- `docker ps`: List all running containers
- `docker stop`: Stop running a container
- `docker start`: Start a stopped container
- `docker restart`: Restart a running container
- `docker rm`: Remove a container
- `docker rmi`: Remove a Docker image
- `docker logs`: View a container's logs

An alternative to Docker is Linux Containers (LXC). LXC allows multiple isolated Linux systems to run on a single host. LXC is more systems-focused than Docker: while powerful, LXC has a steeper learning curve.

These are common commands for managing LXC containers:
- `lxc-ls`: List all existing containers
- `lxc-stop -n <container>`: Stop a running container.
- `lxc-start -n <container>`: Start a stopped container.
- `lxc-restart -n <container>`: Restart a running container.
- `lxc-config -n <container name> -s storage`: Manage container storage
- `lxc-config -n <container name> -s network`: Manage container network settings
- `lxc-config -n <container name> -s security`: Manage container security settings
- `lxc-attach -n <container>`: Connect to a container.
- `lxc-attach -n <container> -f /path/to/share`: Connect to a container and share a specific directory or file.

LXC containers should be secured by restricting unneeded access to them. LXC uses namespaces and individual root file systems to enforce isolation between containers. 

## Linux Networking

### Network Configuration

Managing and configuring networks can be done with tools like `ipconfig` or `ip`. We can also set the default gateway, edit DNS settings, and edit interfaces.

We can view our network settings with either of the following commands:

```Shell
usr@htb[/htb]$ ipconfig
usr@htb[/htb]$ ip addr
```

Activate a network interface with either of the following commands:

```Shell
usr@htb[/htb]$ sudo ifconfig <interface> up
usr@htb[/htb]$ sudo ip link set <interface> up
```

Assign an IP address to an interface with:

```Shell
usr@htb[/htb]$ sudo ifconfig <interface> <address>
```

Assign a netmask to an interface with:

```Shell
usr@htb[/htb]$ sudo ifconfig <interface> netmask <mask>
```

Assign the route to an interface with:

```Shell
usr@htb[/htb]$ sudo route add default gw <address> <interface>
```

Network access control (NAC) is a security system that ensures that only authorized and compliant devices are granted access to the network.
- **Discretionary access control (DAC)**: Grants resource owners the responsibility of controlling access permissions to their resources
- **Mandatory access control (MAC)**: Determines resource access based on the resource's security level and the user's security level or process requesting access
- **Role-based access control (RBAC)**: Assigns permissions to users based on their roles within an organization

In addition to NAC, tools such as syslog, rsyslog, ss, lsof, and the ELK stack can be used to monitor and analyze network traffic.

The most common network troubleshooting tools:
1. **Ping**: Used to test connectivity between two devices
2. **Traceroute**: Used to see what hops a packet takes from one device to another
3. **Netstat**: Used to display active network connections and their associated ports
4. **Tcpdump**: Used to display TCP/IP packets being sent and received in a network
5. **Wireshark**: Used to capture packets being sent and received in a network
6. **Nmap**: Used to discover hosts and services on a computer network

Network hardening is commonly done with the following tools:
- **SELinux**: A MAC system integrated into the Linux kernel
- **AppArmor**: A user-friendly MAC system and alternative to SELinux
- **TCP wrappers**: A tool that restricts access to network services based on the IP address of incoming connections

### Remote Desktop Protocols in Linux

Remote desktop protocols are used in many OSes to provide graphical remote access to a system. `X11`, `XDMCP`, and `VNC` are examples of Linux remote desktop protocols.

The XServer is the user-side part of the `X Window System network protocol` (`X11` / `X`). The `X11` is a fixed system that consists of a collection of protocols and applications that allow us to call application windows on displays in a graphical user interface. `X11` is predominant on Unix systems and is completely unencrypted.

The `X Display Manager Control Protocol` (`XDMCP`) protocol used to manage remote X Window sessions on other machines. XDMCP is an insecure protocol and should not be used in any environment that requires high levels of security.

`Virtual Network Computing` (`VNC`) is a remote desktop sharing system based on the RFB protocol that allows users to control a computer remotely. It allows a user to view and interact with a desktop environment remotely over a network connection. VNC is generally considered to be secure. The most used tools for such kinds of connections are UltraVNC and RealVNC because of their encryption and higher security.

## Linux Hardening

### Linux Security

Security is a processes, not a product. The following actions are just some actions that can be taken to increase a Linux system's security:
- Removing or disabling all unnecessary services and software
- Removing all services that rely on unencrypted authentication mechanisms
- Ensure NTP is enabled and Syslog is running
- Ensure that each user has its own account
- Enforce the use of strong passwords
- Set up password aging and restrict the use of previous passwords
- Locking user accounts after login failures
- Disable all unwanted SUID/SGID binaries

Updating and patching is especially important in security. Some kernel versions have to be updated manually. Keeping packages up to date can be accomplished as follows:

```Shell
apt update && apt dist-upgrade
```

We should also setup firewall rules and disallow password login and root user login via SSH. TCP wrappers are a security tool in Linux that restrict access to certain services based on the hostname or IP address of the user requesting access. TCP wrappers use `/etc/hosts.allow` and `/etc/hosts.deny` to determine which services are granted access, and these files can be configured by a system administrator.

### Firewall Setup

Firewalls provide a security mechanism for controlling and monitoring network traffic between different network segments, such as internal and external networks or different network zones.

The iptables utility provides a flexible set of rules for filtering network traffic based on various criteria such as source and destination IP addresses, port numbers, protocols, and more. These are the main components of iptables:
- **Tables**: Tables are used to organize and categorize firewall rules.
- **Chains**: Chains are used to group a set of firewall rules applied to a specific type of network traffic.
- **Rules**: Rules define the criteria for filtering network traffic and the actions to take for packets that match the criteria.
- **Matches**: Matches are used to match specific criteria for filtering network traffic, such as source or destination IP addresses, ports, protocols, and more.
- **Targets**: Targets specify the action for packets that match a specific rule. For example, targets can be used to accept, drop, or reject packets or modify the packets in another way.

There are three built-in tables in iptables:
- `filter`: Used to filter network traffic based on IP addresses, ports, and protocols
- `nat`: Used to modify the source or destination IP addresses of network packets
- `mangle`: Used to modify the header fields of network packets

Each of these tables has built-in chains, which organize rules that define how network traffic should be filtered or modified. Users can also define their own chains.

We can add rules to chains using the `-A` options. Rules include a set of criteria or matches and a target specifying the action for packets that match the criteria. 

These are common targets:
- **ACCEPT**: Allows the packet to pass through the firewall and continue to its destination
- **DROP**: Drops the packet, effectively blocking it from passing through the firewall
- **REJECT**: Drops the packet and sends an error message back to the source address, notifying them that the packet was blocked
- **LOG**: Logs the packet information to the system log
- **SNAT**: Modifies the source IP address of the packet, typically used for Network Address Translation (NAT) to translate private IP addresses to public IP addresses
- **DNAT**: Modifies the destination IP address of the packet, typically used for NAT to forward traffic from one IP address to another
- **MASQUERADE**: Similar to SNAT but used when the source IP address is not fixed, such as in a dynamic IP address scenario
- **REDIRECT**: Redirects packets to another port or IP address
- **MARK**: Adds or modifies the Netfilter mark value of the packet, which can be used for advanced routing or other purposes

These are common matching options:
- `-p` or `--protocol`: Specifies the protocol to match (e.g. tcp, udp, icmp)
- `--dport`: Specifies the destination port to match
- `--sport`: Specifies the source port to match
- `-s` or `--source`: Specifies the source IP address to match
- `-d` or `--destination`: Specifies the destination IP address to match
- `-m state`: Matches the state of a connection (e.g. NEW, ESTABLISHED, RELATED)
- `-m multiport`: Matches multiple ports or port ranges
- `-m tcp`: Matches TCP packets and includes additional TCP-specific options
- `-m udp`: Matches UDP packets and includes additional UDP-specific options
- `-m string`: Matches packets that contain a specific string
- `-m limit`: Matches packets at a specified rate limit
- `-m conntrack`: Matches packets based on their connection tracking information
- `-m mark`: Matches packets based on their Netfilter mark value
- `-m mac`: Matches packets based on their MAC address
- `-m iprange`: Matches packets based on a range of IP addresses

### System Logs and Monitoring

System logs are a set of files that contain information about the Linux system and the activities taking place on it.
- **Kernel Logs**: Stored in `/var/log/kern.log`
- **System Logs**: Stored in `var/log/syslog`
- **Authentication Logs**: Stored in `/var/log/auth.log`
- **Application Logs**: Stored in logs depending on application
    - **Apache**: Access logs are stored in the `/var/log/apache2/access.log` file (or a file with a similar name)
    - **Nginx**: Access logs are stored in the `/var/log/nginx/access.log` file (or a file with a similar name)
    - **OpenSSH**: Access logs are stored in the `/var/log/auth.log` file on Ubuntu and in `/var/log/secure` on CentOS/RHEL
    - **MySQL**: Access logs are stored in the `/var/log/mysql/mysql.log` file
    - **PostgreSQL**: Access logs are stored in the `/var/log/postgresql/postgresql-version-main.log` file
    - **Systemd**: Access logs are stored in the `/var/log/journal/` directory
- **Security Logs**: Stored in logs such as `/var/log/fail2ban.log` (failed login attempts), `/var/log/ufw.log` (firewall), etc.

## Linux Distributions vs Solaris

### Solaris

Solaris is a Unix-based operating system known for its robustness, scalability, and support for high-end hardware and software systems. It is widely used in the banking, finance, and government sectors. It is also used in large-scale data centers, cloud computing environments, and virtualization platforms.

Solaris is propriety and differs from Linux in its filesystem, security, system monitoring, process and package management, and kernel and hardware support.

Here are the directories of Solaris:
- `/`: The root directory contains all other directories and files in the file system.
- `/bin`: It contains essential system binaries that are required for booting and basic system operations.
- `/boot`: The boot directory contains boot-related files such as boot loader and kernel images.
- `/dev`: The dev directory contains device files that represent physical and logical devices attached to the system.
- `/etc`: The etc directory contains system configuration files, such as system startup scripts and user authentication data.
- `/home`: Users’ home directories.
- `/kernel`: This directory contains kernel modules and other kernel-related files.
- `/lib`: Directory for libraries required by the binaries in `/bin` and `/sbin` directories.
- `/lost+found`: This directory is used by the file system consistency check and repair tool to store recovered files.
- `/mnt`: Directory for mounting file systems temporarily.
- `/opt`: This directory contains optional software packages that are installed on the system.
- `/proc`: The proc directory provides a view into the system's process and kernel status as files.
- `/sbin`: This directory contains system binaries required for system administration tasks.
- `/tmp`: Temporary files created by the system and applications are stored in this directory.
- `/usr`: The usr directory contains system-wide read-only data and programs, such as documentation, libraries, and executables.
- `/var`: This directory contains variable data files, such as system logs, mail spools, and printer spools.

Solaris uses the Solaris Package Manager (SPM) and has its own implementation of NFS. Solaris and Linux have a number of differences in the commands used.

## Tips and Tricks

### Shortcuts

There are many shortcuts that will allow us to work more efficiently in the command line.
- `[TAB]`: Initiate auto-complete
- `[CTRL] + A`: Move the cursor to the beginning of the current line
- `[CTRL] + E`: Move the cursor to the end of the current line
- `[CTRL] + [←]`/`[→]`: Jump at the beginning of the current/previous word
- `[ALT] + B`/`F`: Jump backward/forward one word
- `[CTRL] + U`: Erase everything from the current position of the cursor to the beginning of the line
- `[CTRL] + K`: Erase everything from the current position of the cursor to the end of the line
- `[CTRL] + W`: Erase the word preceding the cursor position
- `[CTRL] + C`: Ends the current task/process by sending the SIGINT signal
- `[CTRL] + L`: Clear the terminal (equivalent to `clear`)
- `[CTRL] + Z`: Suspend the current process by sending the SIGTSTP signal
- `[CTRL] + R`: Search through command history for commands we typed previously that match our search patterns
- `[↑]/[↓]`: Go to the previous and next command in the command history

***

[Home](https://app.gitbook.com/o/0kO27okC5uVB9ALX3rho/s/036xtfEIzcEdGegONXWM/) ⋅ [Work](https://app.gitbook.com/o/0kO27okC5uVB9ALX3rho/s/WaFS755Q4sf02CxLcghQ/) ⋅ [Thoughts](https://app.gitbook.com/o/0kO27okC5uVB9ALX3rho/s/s4QQPMntQ25hmJToKSOu/)
