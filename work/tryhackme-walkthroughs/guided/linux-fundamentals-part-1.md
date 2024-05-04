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

# Linux Fundamentals Part 1

[TryHackMe Walkthroughs](./) ⋅ [Guided](../) ⋅ Linux Fundamentals Part 1

***

## Task 1: Introduction

This module will have you:
* Running your very first commands in an interactive Linux machine in your browser
* Teaching you some essential commands used to interact with the file system
* Introduce you to how users and groups work on Linux (and what this means for us as penetration testers) 

## Task 2: A Bit of Background on Linux

Linux is commonly used for websites, control panels, critical infrastructure, and more. Linux is actually an umbrella term for a group of operating systems all based on Unix. We refer to these operating systems as "flavors" of Linux.

<details>

<summary>Research: What year was the first release of a Linux operating system?</summary>

1991 This information can be found with a quick Google search. The original Linux kernel was released on September 17, 1991.

</details>

## Task 3: Interacting With Your First Linux Machine (In-Browser)

You can interact with a Linux machine in TryHackMe by pressing the "Start Machine" button on the top-right of each task.

## Task 4: Running Your First few Commands

Two basic commands that can be run in the Linux command line are `echo` and `whoami`. `echo` outputs the text you provide to it. `whoami` outputs the username you are logged in as.

<details>

<summary>If we wanted to output the text "TryHackMe", what would our command be?</summary>

echo TryHackMe

The `echo` command outputs text. No quotation marks are needed.

</details>

<details>

<summary>What is the username of who you're logged in as on your deployed Linux machine?</summary>

tryhackme

Use the command `whoami` to see your username.

</details>

## Task 5: Interacting With the Filesystem!

The Linux command line allows you to interact with the filesystem. `cd` allows you to change directories and `ls` lists the files in the current directory. `pwd` prints which directory you are currently in. `cat` stands for concatenate and outputs multiple files concatenated together. However, it is most commonly used to print the contents of a single file.

<details>

<summary>On the Linux machine that you deploy, how many folders are there?</summary>

4

Use the `ls` command to list files and folders.

</details>

<details>

<summary>Which directory contains a file?</summary>

folder4

Use the `cd <folder_name>` to enter each folder. Use `cd ../` to go "back" one folder.

</details>

<details>

<summary>What is the contents of this file?</summary>

Hello World

Use `cat <file_name>` to view file contents.

</details>

<details>

<summary>Use the cd command to navigate to this file and find out the new current working directory. What is the path?</summary>

/home/tryhackme/folder4

Use `pwd` to print the directory you are currently in.

</details>

## Task 6: Searching for Files

You can search the filesystem for files by name or other attributes with `find`. `grep` can be used to search the contents of files for specific values.

<details>

<summary>Use grep on "access.log" to find the flag that has a prefix of "THM". What is the flag?</summary>

THM{ACCESS}

Use `grep THM* access.log` to search for prefixes of "THM".

</details>

## Task 7: An Introduction to Shell Operators

Various operators in the Linux command line allow you to use commands with more flexibility. `&` allows you to run commands in the background of your terminal. `&&` looks similar but is unrelated to `&`. Rather, `&&` allows you to combine multiple commands together in one line of your terminal. The`>` operator is a redirector, meaning that we can take the output from a command (such as using cat to output a file) and direct it elsewhere. `>>` has the same functionality as the `>` operator but appends the output rather than replacing (meaning nothing is overwritten).

<details>

<summary>If we wanted to run a command in the background, what operator would we want to use?</summary>

&

Running a command in the background is done with `<command> &`.

</details>

<details>

<summary>If I wanted to replace the contents of a file named "passwords" with the word "password123", what would my command be?</summary>

echo password123 > passwords

`>` is used to write a command's output to a file.

</details>

<details>

<summary>Now if I wanted to add "tryhackme" to this file named "passwords" but also keep "passwords123", what would my command be</summary>

echo tryhackme >> passwords

`>>` is used to append a command's output to a file.

</details>

## Task 8: Conclusions & Summaries

In conclusion, this module covered the following:
* Understanding why Linux is so commonplace today
* Interacting with your first-ever Linux machine!
* Ran some of the most fundamental commands
* Had an introduction to navigating around the filesystem & how we can use commands like find and grep to make finding data even more efficient!
* Power up your commands by learning about some of the important shell operators.

## Task 9: Linux Fundamentals Part 2

The walkthrough for the next room in this Linux introductory series can be found [here](linux-fundamentals-part-2.md).

***

[Home](https://app.gitbook.com/o/0kO27okC5uVB9ALX3rho/s/036xtfEIzcEdGegONXWM/) ⋅ [Work](https://app.gitbook.com/o/0kO27okC5uVB9ALX3rho/s/WaFS755Q4sf02CxLcghQ/) ⋅ [Thoughts](https://app.gitbook.com/o/0kO27okC5uVB9ALX3rho/s/s4QQPMntQ25hmJToKSOu/)
