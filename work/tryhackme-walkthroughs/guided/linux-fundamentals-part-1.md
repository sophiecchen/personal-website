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

This room is part 1 in a 3-part series going over the fundamentals of Linux, a family of open-source Unix-like operating systems.

## Task 2: A Bit of Background on Linux

<details>

<summary>Research: What year was the first release of a Linux operating system?</summary>

1991

The original Linux kernel was released on September 17, 1991.

</details>

## Task 4: Running Your First few Commands

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

</details>

## Task 6: Searching for Files

<details>

<summary>Use grep on "access.log" to find the flag that has a prefix of "THM". What is the flag?</summary>

THM{ACCESS}

Use `grep THM* access.log` to search for prefixes of "THM".

</details>

## Task 7: An Introduction to Shell Operators

<details>

<summary>If we wanted to run a command in the background, what operator would we want to use?</summary>

&

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

***

[Home](https://app.gitbook.com/o/0kO27okC5uVB9ALX3rho/s/036xtfEIzcEdGegONXWM/) ⋅ [Work](https://app.gitbook.com/o/0kO27okC5uVB9ALX3rho/s/WaFS755Q4sf02CxLcghQ/) ⋅ [Thoughts](https://app.gitbook.com/o/0kO27okC5uVB9ALX3rho/s/s4QQPMntQ25hmJToKSOu/)
