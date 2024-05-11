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

# Threat Intelligence Tools

[TryHackMe Walkthroughs](./) ⋅ [Guided](../) ⋅ Threat Intelligence Tools

***
## Task 1:

## Task 2:

## Task 3: UrlScan.io

<details>
<summary>What was TryHackMe's Cisco Umbrella Rank based on the screenshot?</summary>

345612

This information is listed in the first section of the Summary.

</details>

<details>
<summary>How many domains did UrlScan.io identify on the screenshot?</summary>

13

This information is listed in the first section of the Summary.

</details>

<details>

<summary>What was the main domain registrar listed on the screenshot?</summary>

NAMECHEAP INC

This information is listed in the Live information section of the Summary.

</details>

<details>

<summary>What was the main IP address identified for TryHackMe on the screenshot?</summary>

2606:4700:10::ac43:1b0a

This information is listed in the first section of the Summary.

</details>

## Task 4: Abuse.ch

<details>

<summary>The IOC 212.192.246.30:5555 is identified under which malware alias name on ThreatFox?</summary>

Katana

Search ioc:212.192.246.30:5555 in the ThreatFox database.

</details>

<details>

<summary>Which malware is associated with the JA3 Fingerprint 51c64c77e60f3980eea90869b68c58a8 on SSL Blacklist?</summary>

Dridex

</details>

<details>

<summary>From the statistics page on URLHaus, what malware-hosting network has the ASN number AS14061?</summary>

DIGITALOCEAN-ASN

</details>

<details>

<summary>Which country is the botnet IP address 178.134.47.166 associated with according to FeodoTracker?</summary>

Georgia

</details>

## Task 5: PhishTool

The email to be analyzed is located in the folder called "Emails" located on the Desktop. Double click on the email. For this exercise, you can setup Thunderbird arbitrarily.

<details>

<summary>What social media platform is the attacker trying to pose as in the email?</summary>

LinkedIn

This information can be found by looking at the footer.

</details>

<details>

<summary>What is the senders email address?</summary>

darkabutla@sc500.whpservers.com

This information can be found at the top of the email.

</details>

<details>

<summary>What is the recipient's email address?</summary>

cabbagecare@hotsmail.com

This information can be found at the top of the email.

</details>

<details>

<summary>What is the Originating IP address? Defang the IP address.</summary>

204\[.]93\[.]183\[.]11

Click more (on the upper-right side of the email), and then click view source. Find the part of the line that says "sender ip is". Put brackets around the period to defang.

</details>

<details>

<summary>How many hops did the email go through to get to the recipient?</summary>

4

Click more (on the upper-right side of the email), and then click view source. There are four "Received" headers, indicating 4 jumps.

</details>

## Task 6: Cisco Talos Intelligence

<details>

<summary>What is the listed domain of the IP address from the previous task?</summary>

scnet.net

Enter the IP address into [Talos Intelligence's Reputation Center](threat-intelligence-tools.md#what-is-the-listed-domain-of-the-ip-address-from-the-previous-task).

</details>

<details>

<summary>What is the customer name of the IP address?</summary>

Complete Web Reviews

Use the command `whois <ip_address>` to find this information.

</details>

## Task 7: Scenario 1

<details>

<summary>According to Email2.eml, what is the recipient's email address?</summary>

chris.lyons@supercarcenterdetroit.com

This information can be found at the top of the email.

</details>

<details>

<summary>From Talos Intelligence, the attached file can also be identified by the Detection Alias that starts with an H...</summary>

HIDDENEXT/Worm.Gen

I downloaded this file and ran the command `sha256sum <file>` to get the SHA256 hash. I put this hash into Talos Intelligence.

</details>

## Task 8: Scenario 2

<details>

<summary>What is the name of the attachment on Email3.eml?</summary>

Sales\_Receipt 5606.xls

This information can be found at the bottom of the email.

</details>

<details>

<summary>What malware family is associated with the attachment on Email3.eml?</summary>

Dridex

I downloaded this file and ran the command `sha256sum <file>` to get the SHA256 hash. I put this hash into Talos Intelligence.

</details>

***

[Home](https://app.gitbook.com/o/0kO27okC5uVB9ALX3rho/s/036xtfEIzcEdGegONXWM/) ⋅ [Work](https://app.gitbook.com/o/0kO27okC5uVB9ALX3rho/s/WaFS755Q4sf02CxLcghQ/) ⋅ [Thoughts](https://app.gitbook.com/o/0kO27okC5uVB9ALX3rho/s/s4QQPMntQ25hmJToKSOu/)
