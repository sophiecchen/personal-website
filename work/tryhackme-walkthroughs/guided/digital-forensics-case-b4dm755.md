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

# Digital Forensics Case B4DM755

[TryHackMe Walkthroughs](./) ⋅ [Guided](../) ⋅ Digital Forensics Case B4DM755

***

## Task 1: Introduction

This room simulates a public-sector digital forensics case spanning from evidence collection to court testimony. A court of law has authorized us to conduct a search on a specific person by analyzing artifacts and evidence. In this room, we will:
* Ensure proper chain of custody procedures for transporting evidence to the forensics laboratory
* Use FTK Imager to acquire a forensic disk image and preserve digital artifacts and evidence
* Analyze forensic artifacts received at the forensics laboratory for presentation during a trial in a court of law

## Task 2: Case B4DM755: Details of the Crime

Suppose we are a forensic lab analyst whose job is to analyze artifacts from crime scenes.

We have been given the following information about the suspect:
* Name: William S. McClean (William Super McClean)
* Nationality: British
* Charges Pressed: Corporate espionage and theft of trade secrets
* Other information: Currently in Metro Manila, Phillippines; transaction with incriminating materials will happen today with local gang member

We have been assigned as DFIR first responder and are tasked with appropriately acquiring digital artifacts and evidence. Proper search authority and a search warrent have been obtained.

<details>

<summary>What is your official role?</summary>

forensic lab analyst

As noted above, our official role is our job title: forensic lab analyst.

</details>

<details>

<summary>What role was assigned to you for this specific scenario?</summary>

DFIR first responder

In this specific scenario, we are acting as a DFIR first responder.

</details>


<details>

<summary>What do you have to gather?</summary>

digital artefacts and evidence

As a DFIR first responder, we are responsible for gathering digital artifacts and evidence that will be analyzed and possibly used in court.

</details>


<details>

<summary>What document is needed before performing any legal search?</summary>

search warrant

A search warrant authorizes law enforcement officers to investigate the subject and his place of residence.

</details>


## Task 3: Practical Application of the Digital Forensics Process

DFIR first responders typically follow these steps for computer systems at the scene of a crime:
1. Take an image of RAM
2. Check for drive encryption
3. Take an image of the drive(s)

DFIR first responders should establish a chain of custody while following these best practices:
* Ensure proper documentation of seized materials
* Hash and copy obtained files
* Do **not** shutdown devices since this can alter data. Pull the power plug instead.
* Bag, seal, and tag the obtained artifacts.

<details>

<summary>Before imaging drives, what must we check them for?</summary>

</details>

drive encryption

Whether the drive is encrypted or not needs to be known before trying to imaging the drive.

<details>

<summary>What should be done to ensure and maintain the integrity of original files in the Chain of Custody?</summary>

</details>

hash and copy

Hashing and copying allows we to ensure that the original files have not been modified in any way.

<details>

<summary>What must be done before sending obtained artefacts to the Forensics Laboratory?</summary>

bag, seal, and tag the obtained artefacts

Artifacts need to be secured and labeled before being sent to a different location.

</details>

## Task 4: Case B4DM755: At the Scene of Crime

Law enforcement arrived at the suspect's residence after the transaction supposedly happened. There were indications that he attempted to eradicate evidence.

Law enforcement officers searched the suspect's residence and discovered a flash drive with an attached key chain. The key chain had the initials WSM and is believed to belong to the suspect.

<details>
<summary>What is the only possible artefact found in the suspect's residence?</summary>

flash drive

As noted above, law enforcement officers discovered a flash drive with an attached keychain.

</details>

<details>
<summary>Based on the scenario and the previous task, what should be done with that acquired suspect artefact?</summary>

</details>

<details>
<summary>What is the crucial aspect of the Chain of Custody that ensures individual accountability and guarantees a transparent and untainted transfer of artefacts and evidence?</summary>

</details>

## Task 5: Introduction to FTK Imager

<details>
<summary>What device will prevent tampering when acquiring a forensic disk image?</summary>

</details>

<details>
<summary>What is the UI element of FTK Imager which displays a hierarchical view of the added evidence sources?</summary>

</details>

<details>
<summary>Is the attached flash drive encrypted? (Y/N)</summary>

</details>

<details>
<summary>What is the UI element of FTK Imager which displays a list of files and folders?</summary>

</details>

## Task 6: Using FTK Imager to Acquire Digital Artifacts and Evidence

<details>
<summary>What is the UI element of FTK Imager which displays the content of selected files?</summary>

</details>

<details>
<summary>What is the SHA1 hash of the physical drive and forensic image?</summary>

</details>

<details>
<summary>Including hidden files, how many files are currently stored on the flash drive?</summary>

</details>

<details>
<summary>How many files were deleted in total?</summary>

</details>

<details>
<summary>How many recovered files are corrupted (e.g., 0 file size)?</summary>

</details>

## Task 7: Case B4DM755: At the Forensics Laboratory

<details>
<summary>Aside from FTK Imager, what is the directory name of the other tool located in the tools directory under Desktop?</summary>

</details>

<details>
<summary>What is the visible extension of the "hideout" file?</summary>

</details>

<details>
<summary>View the metadata of the "hideout" file. What is its actual extension?</summary>

</details>

<details>
<summary>A phone was used to photograph the "hideout". What is the phone's model?</summary>

</details>

<details>
<summary>A phone was used to photograph the "warehouse". What is the phone's model?</summary>

</details>

<details>
<summary>Are there any indications that the suspect is involved in other illegal activity? (Y/N)</summary>

</details>

<details>
<summary>Who was the point of contact of Mr William S. McClean in 2022?</summary>

</details>

<details>
<summary>A meetup occurred in 2022. What are the GPS coordinates during that time?</summary>

</details>

<details>
<summary>What is the password to extract the contents of pandorasbox.zip?</summary>

</details>

<details>
<summary>From which company did the source code in the pandorasbox directory originate?</summary>

</details>

<details>
<summary>In one of the documents that the suspect has yet to sign, who was listed as the beneficiary?</summary>

</details>

<details>
<summary>What is the hidden flag?</summary>

</details>

## Task 8: Post-Analysis of Evidence to Court Proceedings

<details>
<summary>In which phase is a warrant obtained for search, seizure, and examination of the suspect's computer data due to violations of domestic and international laws?</summary>

</details>

<details>
<summary>In which phase is a forensic analysis performed on the acquired digital evidence requested from various sources?</summary>

</details>

<details>
<summary>Which phase involves presenting forensic artefacts and evidence with proper documentation in a court of law?</summary>

</details>

***

[Home](https://app.gitbook.com/o/0kO27okC5uVB9ALX3rho/s/036xtfEIzcEdGegONXWM/) ⋅ [Work](https://app.gitbook.com/o/0kO27okC5uVB9ALX3rho/s/WaFS755Q4sf02CxLcghQ/) ⋅ [Thoughts](https://app.gitbook.com/o/0kO27okC5uVB9ALX3rho/s/s4QQPMntQ25hmJToKSOu/)
