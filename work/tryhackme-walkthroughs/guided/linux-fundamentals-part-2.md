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

This room will have you:
* Unlocking the potential of your first few commands by introducing you to using flags and arguments
* Advancing your knowledge of the filesystem to perform some more useful commands such as copying and moving files
* Discovering how access to files and folders is managed and how we can determine our access.
* Running your first few scripts and executables!


## Task 2: Accessing Your Linux Machine Using SSH (Deploy)

Secure Shell or SSH simply is a protocol between devices in an encrypted form. You can SSH into the machine for this room using the command `ssh tryhackme@<machine_ip>`. The machine IP is listed at the top of the page after you start the machine for the room.

## Task 3: Introduction to Flags and Switches

Commands in Linux have a default behavior. For example, `ls` lists the contents of the working directory. We can add flags to commands to extend the behaviour of commands. `man <command>` can be used to view the associated flags for each command.

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

The command line can also be used to manipulate files. `touch` creates a new file and `mkdir` creates a new folder. Files and folders can be copied with `cp`, moved with `mv`, and removed with `rm`. `file` can be used to output the file type.

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

<details>

<summary>On the deployable machine, who is the owner of "important"?</summary>

user2

</details>

<details>

<summary>What would the command be to switch to the user "user2"?</summary>

su user2

</details>

<details>

<summary>Output the contents of "important", what is the flag?</summary>

THM{SU\_USER2}

</details>

## Task 6: Common Directories

The Linux filesystem is organized into directories that hold important files for the operating system. The `/etc` directory holds TODO.
`/var`
`/root`
`/tmp`

<details>

<summary>What is the directory path that would we expect logs to be stored in?</summary>

/var/log

</details>

<details>

<summary>What root directory is similar to how RAM on a computer works?</summary>

/tmp

</details>

<details>

<summary>Name the home directory of the root user</summary>

/root

</details>

## Task 7: Conclusions and Summaries

In conclusion, this room covered the following:
* Using terminal text editors
* General utilities such as downloading and serving contents using a python webserver
* A look into processes
* Maintaining & automating your system by the use of crontabs, package management, and reviewing logs

## Task 8: Linux Fundamentals Part 3

The walkthrough for the next room in this Linux introductory series can be found [here](linux-fundamentals-part-3.md).

***

[Home](https://app.gitbook.com/o/0kO27okC5uVB9ALX3rho/s/036xtfEIzcEdGegONXWM/) ⋅ [Work](https://app.gitbook.com/o/0kO27okC5uVB9ALX3rho/s/WaFS755Q4sf02CxLcghQ/) ⋅ [Thoughts](https://app.gitbook.com/o/0kO27okC5uVB9ALX3rho/s/s4QQPMntQ25hmJToKSOu/)
