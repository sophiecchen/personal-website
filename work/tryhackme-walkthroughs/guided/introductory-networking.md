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

# Introductory Networking

[TryHackMe Walkthroughs](./) ⋅ [Guided](../) ⋅ Introductory Networking

***
## Task 1:
## Task 2: The OSI Model: An Overview

<details>

<summary>Which layer would choose to send data over TCP or UDP?</summary>

4

Layer 4 is the is transport layer.

</details>

<details>

<summary>Which layer checks received information to make sure that it hasn't been corrupted?</summary>

2

Layer 2 is the data link layer.

</details>

<details>

<summary>In which layer would data be formatted in preparation for transmission?</summary>

2

Layer 2 is the data link layer.

</details>

<details>

<summary>Which layer transmits and receives data?</summary>

1

Layer 1 is the physical layer.

</details>

<details>

<summary>Which layer encrypts, compresses, or otherwise transforms the initial data to give it a standardized format?</summary>

6

Layer 6 is the presentation layer.

</details>

<details>

<summary>Which layer tracks communications between the host and receiving computers?</summary>

5

Layer 5 is the session layer.

</details>

<details>

<summary>Which layer accepts communication requests from applications?</summary>

7

Layer 7 is the application layer.

</details>

<details>

<summary>Which layer handles logical addressing?</summary>

3

Layer 3 is the network layer.

</details>

<details>

<summary>When sending data over TCP, what would you call the "bite-sized" pieces of data?</summary>

Segments

</details>

<details>

<summary>[Research] Which layer would the FTP protocol communicate with?</summary>

7

The file transfer protocol (FTP) communicates with the application layer.

</details>

<details>

<summary>Which transport layer protocol would be best suited to transmit a live video?</summary>

UDP

UDP is preferred in situations where speed is more important than accuracy.

</details>

## Task 3: Encapsulation

<details>

<summary>How would you refer to data at layer 2 of the encapsulation process (with the OSI model)?</summary>

Frames

</details>

<details>

<summary>How would you refer to data at layer 4 of the encapsulation process (with the OSI model), if the UDP protocol has been selected?</summary>

Datagrams

</details>

<details>

<summary>What process would a computer perform on a received message?</summary>

De-encapsulation

</details>

<details>

<summary>Which is the only layer of the OSI model to add a <em>trailer</em> during encapsulation?</summary>

Data Link

</details>

<details>

<summary>Does encapsulation provide an extra layer of security (Aye/Nay)?</summary>

Aye

</details>

## Task 4: The TCP/IP Model

<details>

<summary>Which model was introduced first, OSI or TCP/IP?</summary>

TCP/IP

</details>

<details>

<summary>Which layer of the TCP/IP model covers the functionality of the Transport layer of the OSI model (Full Name)?</summary>

Transport

</details>

<details>

<summary>Which layer of the TCP/IP model covers the functionality of the Session layer of the OSI model (Full Name)?</summary>

Application

</details>

<details>

<summary>The Network Interface layer of the TCP/IP model covers the functionality of two layers in the OSI model. These layers are Data Link, and?.. (Full Name)?</summary>

Physical

</details>

<details>

<summary>Which layer of the TCP/IP model handles the functionality of the OSI network layer?</summary>

Internet

</details>

<details>

<summary>What kind of protocol is TCP?</summary>

Connection-based

</details>

<details>

<summary>What is SYN short for?</summary>

Synchronise

</details>

<details>

<summary>What is the second step of the three way handshake?</summary>

SYN/ACK

</details>

<details>

<summary>What is the short name for the "Acknowledgement" segment in the three-way handshake?</summary>

ACK

</details>

## Task 5: Ping

<details>

<summary>What command would you use to ping the bbc.co.uk website?</summary>

ping bbc.co.uk

</details>

<details>

<summary>Ping <em>muirlandoracle.co.uk.</em> What is the IPv4 address?</summary>

217.160.0.152

</details>

<details>

<summary>What switch lets you change the interval of sent ping requests?</summary>

\-i

</details>

<details>

<summary>What switch would allow you to restrict requests to IPv4?</summary>

\-4

</details>

<details>

<summary>What switch would give you a more verbose output?</summary>

\-v

</details>

## Task 6: Traceroute

<details>

<summary>What switch would you use to specify an interface when using Traceroute?</summary>

\-i

</details>

<details>

<summary>What switch would you use if you wanted to use TCP SYN requests when tracing the route?</summary>

\-T

</details>

<details>

<summary>[Lateral Thinking] Which layer of the <em>TCP/IP</em> model will traceroute run on by default (Windows)?</summary>

Internet

</details>

## Task 7: WHOIS

<details>

<summary>What is the registrant postal code for facebook.com?</summary>

94025

</details>

<details>

<summary>When was the facebook.com domain first registered (Format: DD/MM/YYYY)?</summary>

29/03/1997

</details>

<details>

<summary>Which city is the registrant based in?</summary>

Redmond

</details>

<details>

<summary>[OSINT] What is the name of the golf course that is near the registrant address for microsoft.com?</summary>

Bellevue Golf Course

I used Google Maps to search for golf courses near the listed registrant address.

</details>

<details>

<summary>What is the registered Tech Email for microsoft.com?</summary>

msnhst@microsoft.com

</details>

## Task 8: Dig

<details>

<summary>What is DNS short for?</summary>

Domain Name System

</details>

<details>

<summary>What is the first type of DNS server your computer would query when you search for a domain?</summary>

Recursive

</details>

<details>

<summary>What type of DNS server contains records specific to domain extensions (i.e. <em>.com,</em> .co.uk*, etc)*? Use the long version of the name.</summary>

Top-Level Domain

</details>

<details>

<summary>Where is the very first place your computer would look to find the IP address of a domain?</summary>

Hosts File

</details>

<details>

<summary><strong>[Research]</strong> Google runs two public DNS servers. One of them can be queried with the IP 8.8.8.8, what is the IP address of the other one?</summary>

8.8.4.4

</details>

<details>

<summary>If a DNS query has a TTL of 24 hours, what number would the dig query show?</summary>

86400

</details>

***

[Home](https://app.gitbook.com/o/0kO27okC5uVB9ALX3rho/s/036xtfEIzcEdGegONXWM/) ⋅ [Work](https://app.gitbook.com/o/0kO27okC5uVB9ALX3rho/s/WaFS755Q4sf02CxLcghQ/) ⋅ [Thoughts](https://app.gitbook.com/o/0kO27okC5uVB9ALX3rho/s/s4QQPMntQ25hmJToKSOu/)
