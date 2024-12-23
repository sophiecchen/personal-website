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

***

## Task 1: Introduction to Digital Forensics

The field of forensics applies science to investigate crimes. Digital forensics, focusing on digital evidence, stands at the intersection between cybersecurity and forensics.

There are two types of investigations where digital forensics is applicable:
1. Public-sector investigations: These investigations are carried out by government and law enforcement.
2. Private-sector investigations: These investigations are carried out by corporations.

<details>

<summary>Consider the desk in the photo above. In addition to the smartphone, camera, and SD cards, what would be interesting for digital forensics?</summary>

Laptop

Laptops often contain a wealth of recoverable evidence. 

</details>

## Task 2: Digital Forensics Processes

Before acquiring evidence, we should have proper search authorization.

At the scene, we should complete the following tasks:
1. Acquire the evidence.
2. Establish a chain of custody so that we know who has the evidence at any time.
3. Place the evidence in a secure container.
4. Transport the evidence to the lab.

Upon arrival at the lab, we should do the following:
1. Retrieve the evidence from the secure container.
2. Create a forensic copy of the evidence using validated tools.
3. Return the evidence to the secure container.
4. Begin analysis on the forensic copy.

Following proper procedures is crucial in digital forensics because our findings must be repeatable.

<details>

<summary>It is essential to keep track of who is handling it at any point in time to ensure that evidence is admissible in the court of law. What is the name of the documentation that would help establish that?</summary>

chain of custody

The chain of custody keep track of who is handling evidence at any point in time so that the evidence is verifiably not tampered with.

</details>

## Task 3: Practical Example of Digital Forensics

Files in a computer have associated data, called metadata. This metadata includes information about the file, such as creation date and last modification date. We can view the metadata of a PDF file by downloading `pdfinfo` using `sudo apt install poppler-utils`. The tool can be run as follows: `pdfinfo <file>`.

<details>

<summary>Using <code>pdfinfo</code>, find out the author of the attached PDF file.</summary>

Ann Gree Shepherd

Use the command `pdfinfo ransom-letter.pdf` to view author information.

</details>

Images also have metadata. The standard format for saving image metadata is the Exchangeable Image File Format (EXIF), and EXIF metadata can be viewed with `exiftool`. To download this too, first run `sudo apt install libimage-exiftool-perl`. Then, EXIF metadata can be viewed with the command `exiftool <image>`.

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
