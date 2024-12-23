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

# Intro to Cyber Threat Intel

[TryHackMe Walkthroughs](./) ⋅ [Guided](../) ⋅ Intro to Cyber Threat Intel

## Task 1: Introduction

This room introduces us to the basics of cyber threat intelligence. In this room, we will learn:
* The basics of CTI and its various classifications
* The lifecycle followed to deploy and use intelligence during threat investigations
* Frameworks and standards used in distributing intelligence

## Task 2: Cyber Threat Intelligence

Cyber Threat Intelligence (CTI) is evidence-based knowledge about adversaries, including their indicators, tactics, motivations, and actionable advice against them. 

Intelligence is the correlation of data and information to extract patterns of actions based on contextual analysis. Threat intelligence can be gathered internally, from the community forums, or from external sources such as public sources and threat intelligence feeds.

There are a few different types of intelligence:
* **Strategic intel**: Looks into the organization's threat landscape and maps out risk areas
* **Technical intel**: Looks into evidence and artifacts of an attack performed by an adversary
* **Tactical intel**: Assesses adversaries' tactics, techniques, and procedures (TTPs)
* **Operational intel**: Looks into the adversary's motives and intent to attack

<details>

<summary>What does CTI stand for?</summary>

Cyber Threat Intelligence

CTI is short for cyber threat intelligence, a subfield of cybersecurity that focuses on intelligence about adversaries. 

</details>

<details>

<summary>IP addresses, Hashes and other threat artifacts would be found under which Threat Intelligence classification?</summary>

technical intel

Technical intelligence includes specific artifacts and evidence on system, such as IP addresses and hashes.

</details>

## Task 3: CTI Lifecycle

Cyber threat intelligence follows six, cyclic steps that form a feedback process loop.
1. **Planning & direction**: Define objectives and goals and identify crucial parameters such as information assets, tools, sources of intelligence, etc.
2. **Collection**: Gather the required data to address objectives
3. **Processing**: Extract, sort, organize, and correlate data to present it in a usable and understandable format
4. **Analysis**: Derive insights from the data and potentially investigate a threat or strengthen security controls
5. **Dissemination**: Disseminate intelligence to stakeholders
6. **Feedback**: Seek feedback from stakeholders

<details>

<summary>At which phase of the CTI lifecycle is data converted into usable formats through sorting, organizing, correlation and presentation?</summary>

processing

Processing is the phase where raw data is converted into understandable insights.

</details>

<details>

<summary>During which phase do security analysts get the chance to define the questions to investigate incidents?</summary>

direction

Defining questions to investigate incidents should happen at the first phase (direction), of the CTI lifecycle.

</details>

## Task 4: CTI Standards & Frameworks

Standards and frameworks in CTI allow for common terminology and the distribution of threat intelligence across the industry. Common frameworks include:
* **MITRE ATT&CK**: A knowledge base of adversary behavior, focusing on indicators and tactics
* **TAXII**: Defines two models, collection and channel, for exchanging threat intelligence 
* **STIX**: Provides relationships between threat information such as attack campaigns, indicators, etc.
* **Cyber Kill Chain**: Breaks down adversary into 7 steps: (1) reconnaissance, (2) weaponization, (3) delivery, (4) exploitation, (5) installation, (6) command and control, and (7) actions on objectives 
* **The Diamond Model**: Looks at intrusion analysis and tracking attack groups over time using four key areas: (1) adversary, (2) victim, (3) infrastructure, and (4) capabilities

<details>

<summary>What sharing models are supported by TAXII?</summary>

Collection and Channel

The collection model makes threat intelligence available upon request by users while the channel model pushes threat intelligence to users from a central server.

</details>

<details>

<summary>When an adversary has obtained access to a network and is extracting data, what phase of the kill chain are they on?</summary>

Actions on Objectives

After obtaining access and extracting data, the adversary has already established control over the system. Thus, they are on the last phase of the kill chain: actions on objectives.

</details>

## Task 5: Practical Analysis

Open the site associated with the task to answer the following questions.

<details>

<summary>What was the source email address?</summary>

vipivillain@badbank.com

Notice the alert described as "Email received by John Doe from vipivillain@badbank.com".

</details>

<details>

<summary>What was the name of the file downloaded?</summary>

flbpfuh.exe

Notice the alert described as "File download initiated by John Doe. File name: flbpfuh.exe"

</details>

<details>

<summary>After building the threat profile, what message do you receive?</summary>

THM{NOW\_I\_CAN\_CTI}

Scroll down and click on each question in a white box. After answering all questions, the flag pops up.

</details>
