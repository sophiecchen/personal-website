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

# Linux Fundamentals Part 2

[TryHackMe Walkthroughs](./) ⋅ [Guided](../) ⋅ Linux Fundamentals Part 2

***

## Task 1: Introduction

This room is the second in a three-part series on Linux fundamentals. This room will have us:
* Unlocking the potential of our first few commands by introducing flags and arguments
* Advancing our knowledge of the filesystem by copying and moving files
* Discovering how access to files and folders is managed and how we can determine our access
* Running our first few scripts and executables


## Task 2: Accessing Your Linux Machine Using SSH (Deploy)

Secure Shell (SSH) is a protocol between devices in an encrypted form. We can SSH into the machine for this room using the command `ssh tryhackme@<machine_ip>`. The machine IP is listed at the top of the page after we start the machine for the room.

## Task 3: Introduction to Flags and Switches

Commands in Linux have a default behavior. For example, `ls` lists the contents of the working directory. We can add flags to commands to extend the behavior of commands. `man <command>` can be used to view the associated flags for each command.

<details>

<summary>What directional arrow key would we use to navigate down the manual page?</summary>

down

Pressing the down key scrolls the manual page down, and pressing the up key scrolls up.

</details>

<details>

<summary>What flag would we use to display the output in a "human-readable" way?</summary>

\-h

Use the command `man ls` to view the flags for `ls`. Then, press the down key to find the flag that results in "human-readable" output.

</details>

## Task 4: Filesystem Interaction Continued

The command line can also be used to manipulate files. `touch <file>` creates a new file and `mkdir <directory>` creates a new folder. Files and folders can be copied with `cp <file> <destination>`, moved with `mv <file> <destination>`, and removed with `rm <file>`. `file <file>` can be used to output the file type.

<details>

<summary>How would you create the file named "newnote"?</summary>

touch newnote

The `touch` command is used to create a new file.

</details>

<details>

<summary>On the deployable machine, what is the file type of "unknown1" in "tryhackme's" home directory?</summary>

ASCII text

Use the `file` command to view the file's type.

</details>

<details>

<summary>How would we move the file "myfile" to the directory "myfolder"</summary>

mv myfile myfolder

The `mv` command is used to move or rename a file.

</details>

<details>

<summary>What are the contents of this file?</summary>

THM{FILESYSTEM}

Use `cat myfile` to output the contents of the file to the command line.

</details>

## Task 5: Permissions 101

In Linux, a file's characteristics determines what actions can be performed on that file and by whom. The three basic actions we have in Linux are read, write and execute.

A file's permissions can be viewed by using the `-l` flag on the `ls` command. 

We can switch users using `su <user>`.

<details>

<summary>On the deployable machine, who is the owner of "important"?</summary>

user2

Use `ls -l` to view the owner of "important".

</details>

<details>

<summary>What would the command be to switch to the user "user2"?</summary>

su user2

The `su` command is used to switch users.

</details>

<details>

<summary>Output the contents of "important", what is the flag?</summary>

THM{SU\_USER2}

After switching to user2 using `su`, we can `cat` to view the output of "important".

</details>

## Task 6: Common Directories

The Linux filesystem is organized into directories that hold important files for the operating system. The `/etc` directory holds system files that are used by the operating system. `/var` holds variable data such as logs. `/root` is the home directory for the root user, and `/tmp` holds temporary information and is wiped after the computer is restarted.

<details>

<summary>What is the directory path that would we expect logs to be stored in?</summary>

/var/log

Logs are stored in the `log` directory of `/var`.

</details>

<details>

<summary>What root directory is similar to how RAM on a computer works?</summary>

/tmp

RAM on a computer is wiped after the computer is restarted, similar to `tmp`.

</details>

<details>

<summary>Name the home directory of the root user</summary>

/root

The root user's home directory is simply `root`.

</details>

## Task 7: Conclusions and Summaries

In conclusion, this room allowed us to:
* Use terminal text editors
* Deploy general utilities, such as downloading and serving contents using a Python web server
* Take a look into processes
* Maintain and automate our system using crontabs, package management, and reviewing logs

## Task 8: Linux Fundamentals Part 3

My walkthrough for the next room in this Linux introductory series can be found [here](linux-fundamentals-part-3.md).

***

[Home](https://app.gitbook.com/o/0kO27okC5uVB9ALX3rho/s/036xtfEIzcEdGegONXWM/) ⋅ [Work](https://app.gitbook.com/o/0kO27okC5uVB9ALX3rho/s/WaFS755Q4sf02CxLcghQ/) ⋅ [Thoughts](https://app.gitbook.com/o/0kO27okC5uVB9ALX3rho/s/s4QQPMntQ25hmJToKSOu/)
