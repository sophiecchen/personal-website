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
* Other information: Currently in Metro Manila, Philippines; transaction with incriminating materials will happen today with local gang member

We have been assigned as DFIR first responder and are tasked with appropriately acquiring digital artifacts and evidence. Proper search authority and a search warrant have been obtained.

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

digital artfacts and evidence

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

taking an image 

Once an artifact has been transported to the laboratory, a professional should take an image for analysis.

</details>

<details>
<summary>What is the crucial aspect of the Chain of Custody that ensures individual accountability and guarantees a transparent and untainted transfer of artefacts and evidence?

ensure proper documentation

Artifacts and evidence must be properly documented so that we can ensure they were not tampered with. 
</summary>

</details>

## Task 5: Introduction to FTK Imager

FTK Imager is a forensic tool that allows DFIR professionals to acquire data and perform analysis on a copy of that data. In a real-world setting, a write-blocking device, or write blocker for short, must be used to prevent the original evidence from being modified.

The user interface (UI) of FTK Imager includes three parts:
* **Evidence tree pane**: Displays a hierarchical view of added evidence sources
* **File list pane**: Displays a list of files and folders contained in a selected directory from the evidence tree pane 
* **Viewer pane**: Displays the content of selected files

The following scenario emulates a situation where a physical drive, connected to a write blocker, is attached. EFS encryption is a type of filesystem-level encryption provided by Windows on NTFS file systems. We can detect the presence of EFS encryption with the following steps:
1. Open FTK Imager and go to `File -> Add  Evidence Item...`
2. Choose "Physical Drive" as the selected source and "Microsoft Virtual Disk" as the selected drive. Click `Finish`. 
3. Go to `File -> Detect EFS Encryption` to see whether there is EFS encryption on the drive.

<details>
<summary>What device will prevent tampering when acquiring a forensic disk image?</summary>

write-blocking device

A write-blocking device prevents the original evidence from being written to, which would compromise the evidence's integrity.

</details>

<details>
<summary>What is the UI element of FTK Imager which displays a hierarchical view of the added evidence sources?</summary>

evidence tree pane

The evidence tree pane displays a hierarchical view of added evidence sources.

</details>

<details>
<summary>Is the attached flash drive encrypted? (Y/N)</summary>

N

After following the steps above, FTK Imager indicates that no EFS encryption was detected.

</details>

<details>
<summary>What is the UI element of FTK Imager which displays a list of files and folders?</summary>

file list pane

The file list pane displays a list of files and folders contained in a selected directory from the evidence tree pane.

</details>

## Task 6: Using FTK Imager to Acquire Digital Artifacts and Evidence

We can create a disk image with the following steps:
1. Open FTK Imager and go to `File -> Create Disk Image`.
2. Choose "Physical Drive" as the selected source and "Microsoft Virtual Disk" as the selected drive. Click `Finish`. 
3. Check "Verify images after they are created" and "Create directory listings of all files in the image after they are created" at the bottom of the Create Image window.
4. Press `Add` to open the Select Image Type window, and choose "Raw (dd)." Click `Next`.
5. Enter case details in the Evidence Item Information window. Click `Next`.
6. Enter the Image Destination Folder and Image Filename. Click `Finish`.
7. Press `Start` to create the forensic disk image.
8. Once the image has been created, check that the cryptographic hashes of the physical drive and the acquired forensic image match.

<details>
<summary>What is the UI element of FTK Imager which displays the content of selected files?</summary>

viewer pane

The viewer pane displays the content of selected files.

</details>

<details>
<summary>What is the SHA1 hash of the physical drive and forensic image?</summary>

d82f393a67c6fc87a023b50c785a7247ab1ac395

The hash of the image pops up after the image is created.

</details>

We can mount the forensic disk image we created with the following steps:
1. Open FTK Imager and go to `File -> Add Evidence Item`.
2. Choose "Image File" on the Select Source window. Click `Next`.
3. Set "Evidence Source" to the path of the forensic disk image that we created previously. Click `Finish`.

FTK Imager will be populated with our disk image.

<details>
<summary>Including hidden files, how many files are currently stored on the flash drive?</summary>

8

Taking a look at the output in FTK, count the number of items that do not have an X on the icon. Do not include entries with the `.FileSlack` extension.

</details>

<details>
<summary>How many files were deleted in total?</summary>

6

There were 6 icons that had an X on the icon.

</details>

<details>
<summary>How many recovered files are corrupted (e.g., 0 file size)?</summary>

3

Three files had a size of 0: `condominium.pdf`, `resortsworld.png`, and `townhouse.pdf`.

</details>

## Task 7: Case B4DM755: At the Forensics Laboratory

Upon receiving evidence at the Forensics Lab, an analyst should do the following steps:
- Verify and document every detail of the Chain of Custody form.
- Use FTK Imager to create a forensic disk image of the seized flash drive from the suspect's residence.
- Check that the cryptographic hashes of the physical drive and the acquired forensic image match.
- Preserve the flash drive after creating an image.
- Perform review and analysis on the created forensic disk image.
- Document all operations and analysis you do as a forensic analyst
- While presenting at trial, ensure that the cryptographic hashes of the physical evidence and the forensic disk image match.

To analyze the files further, I right clicked on the files I wanted to examin in FTK imager and exported the files into a folder.

<details>
<summary>Aside from FTK Imager, what is the directory name of the other tool located in the tools directory under Desktop?</summary>

exiftool-12.47

This is the name of the other tool, as named by the directory inside the tools directory on the user Desktop.

</details>

<details>
<summary>What is the visible extension of the "hideout" file?</summary>

.png

The hideout file is called "hideout.png."

</details>

<details>
<summary>View the metadata of the "hideout" file. What is its actual extension?</summary>

.jpg

I ran the command `exiftool hideout.pdf` to see the metadata of the file. The file type extension for this file was jpg.

</details>

<details>
<summary>A phone was used to photograph the "hideout". What is the phone's model?</summary>

ONEPLUS A6013

The metadata of the file also listed the camera model name as ONEPLUS A6013.

</details>

<details>
<summary>A phone was used to photograph the "warehouse". What is the phone's model?</summary>

I ran the command `exiftool warehouse.pdf` to see the metadata of the file. The camera model name for this file was Mi 9 Lite.

</details>

<details>
<summary>Are there any indications that the suspect is involved in other illegal activity? (Y/N)</summary>

Y

I used exiftool to view the metadata of the rest of the files. When I ran `exiftool operations.xlsx`, I noticed that the file type was listed as a zip file. So, I ran `cp operations.xlsx operations.zip` and `Expand-Archive -LiteralPath operations.zip -DestinationPath operations` to unzip the file. Within the unzipped operations directory was a notes.txt file that indicated there was other illegal activity.

</details>

<details>
<summary>Who was the point of contact of Mr William S. McClean in 2022?</summary>

Karl Renato Abelardo

I used `cat notes.txt` to print the contents of the notes file. In the file, the 2022 point of contact is listed as Karl Renato Abelardo.

</details>

<details>
<summary>A meetup occurred in 2022. What are the GPS coordinates during that time?</summary>

14°26'25.7"N 120°59'00.8"E

In the notes file, the 2022 GPS coordinates are listed as 14°26'25.7"N 120°59'00.8"E.

</details>

<details>
<summary>What is the password to extract the contents of pandorasbox.zip?</summary>

DarkVault$Pandora=DONOTOPEN!K1ngCr1ms0n!

This password was listed at the bottom of notes.txt.

</details>

<details>
<summary>From which company did the source code in the pandorasbox directory originate?</summary>

SwiftSpend Financial

I used the Windows File System GUI to unzip pandorasbox. Within the unzipped pandorasbox directory was a directory called HFT_Algorithm. I used `cat` to view the contents of the main.py script within this directory. The comment at the top of `main.py` included information about the source code.

</details>

<details>
<summary>In one of the documents that the suspect has yet to sign, who was listed as the beneficiary?</summary>

Mr. Giovanni Vittorio DeVentura

This information was included in the pandorasbox directory in the file "UTCL242231 - Capital distribution to the principal beneficiary GVDeVentura.docx."

</details>

<details>
<summary>What is the hidden flag?</summary>

THM{sCr0LL_sCr0LL_cL1cK_cL1cK_4TT3NT10N_2_D3T41L5_15_CRUC14L!!}

Within the unzipped pandorasbox directory, I used the command `cat DONOTOPEN` to get the flag.

</details>

## Task 8: Post-Analysis of Evidence to Court Proceedings

Law enforcement agencies and DFIR professionals must follow four phases of investigation when investigating a case for court.
1. **Pre-search**: Send requests to preserve data of suspect's social media and ISPs, obtain a warrant, and perform inspections of suspect's public information
2. **Search**: Perform search, seizure, and examination of digital devices and obtain data from social media networks and ISPs
3. **Post-search**: Perform forensic analysis of acquired evidence
4. **Trial**: Present forensic evidence with documentation at court

<details>
<summary>In which phase is a warrant obtained for search, seizure, and examination of the suspect's computer data due to violations of domestic and international laws?</summary>

pre-search

A warrant must be obtained before performing any searches or seizing any evidence. Thus, obtaining a warrant occurs in the pre-search phase.

</details>

<details>
<summary>In which phase is a forensic analysis performed on the acquired digital evidence requested from various sources?</summary>

post-search

The post-search phase is when analysis of acquired digital evidence is performed.
</details>

<details>
<summary>Which phase involves presenting forensic artefacts and evidence with proper documentation in a court of law?</summary>

trial

Forensic evidence with documentation are presented in court during the trial phase.

</details>

***

[Home](https://app.gitbook.com/o/0kO27okC5uVB9ALX3rho/s/036xtfEIzcEdGegONXWM/) ⋅ [Work](https://app.gitbook.com/o/0kO27okC5uVB9ALX3rho/s/WaFS755Q4sf02CxLcghQ/) ⋅ [Thoughts](https://app.gitbook.com/o/0kO27okC5uVB9ALX3rho/s/s4QQPMntQ25hmJToKSOu/)
