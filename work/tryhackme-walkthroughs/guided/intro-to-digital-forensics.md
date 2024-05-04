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

# Intro to Digital Forensics

[TryHackMe Walkthroughs](./) ⋅ [Guided](../) ⋅ Intro to Digital Forensics

***

## Task 1: Introduction to Digital Forensics

Task 1 

<details>

<summary>Consider the desk in the photo above. In addition to the smartphone, camera, and SD cards, what would be interesting for digital forensics?</summary>

Laptop

</details>

## Task 2: Digital Forensics Processes

<details>

<summary>It is essential to keep track of who is handling it at any point in time to ensure that evidence is admissible in the court of law. What is the name of the documentation that would help establish that?</summary>

Chain of Custody

</details>

## Task 3: Practical Example of Digital Forensics

<details>

<summary>Using <code>pdfinfo</code>, find out the author of the attached PDF file.</summary>

Ann Gree Shepherd

Use the command `pdfinfo ransom-letter.pdf` to view author information.

</details>

<details>

<summary>Using <code>exiftool</code> or any similar tool, try to find where the kidnappers took the image they attached to their document. What is the name of the street?</summary>

Milk Street

Use the command `exiftool letter-image.jpg` to view location information. Enter this location data (GPS coordinates) into Google Maps.

</details>

<details>

<summary>What is the model name of the camera used to take this photo?</summary>

Canon EOS R6

Use the command `exiftool letter-image.jpg` to view camera information.

</details>

***

[Home](https://app.gitbook.com/o/0kO27okC5uVB9ALX3rho/s/036xtfEIzcEdGegONXWM/) ⋅ [Work](https://app.gitbook.com/o/0kO27okC5uVB9ALX3rho/s/WaFS755Q4sf02CxLcghQ/) ⋅ [Thoughts](https://app.gitbook.com/o/0kO27okC5uVB9ALX3rho/s/s4QQPMntQ25hmJToKSOu/)
