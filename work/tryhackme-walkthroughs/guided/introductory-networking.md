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
## Task 1: Introduction

This room will cover the following:
* The OSI Model
* The TCP/IP Model
* How these models look in practice
* An introduction to basic networking tools

## Task 2: The OSI Model: An Overview

The Open Systems Interconnection (OSI) Model is a standard model used in computer networking theory that breaks down computer networks into 7 layers. In practice, networking is more compact.
1. **Physical**: This layer is responsible for converting binary data into physical signals, transporting these signals, receiving them, and converting them back into binary data.
2. **Data Link**: This layer TODO
3. **Network**: This layer TODO
4. **Transport**: This layer TODO
5. **Session**: This layer TODO
6. **Presentation**: This layer TODO
7. **Application**: This layer provides an interface for applications running on a computer to transmit information across a network.

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

TODO

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

Suppose a computer wants to send information another. The data starts at layer 7 and works its way down to layer 1, where it is then sent to the other computer. At each layer, more information is added to the data in a process called encapsulation. 

The receiving computer then reverses encapsulation in a process called de-encapsulation. TODO

<details>

<summary>How would you refer to data at layer 2 of the encapsulation process (with the OSI model)?</summary>

Frames

The data link layer, layer 2, works with frames.

</details>

<details>

<summary>How would you refer to data at layer 4 of the encapsulation process (with the OSI model), if the UDP protocol has been selected?</summary>

Datagrams

The transport, layer 4, works with datagrams in the UDP protocol and segments in the TCP protocol.

</details>

<details>

<summary>What process would a computer perform on a received message?</summary>

De-encapsulation

A computer receiving a message performs de-encapsulation in order to recover the original data.

</details>

<details>

<summary>Which is the only layer of the OSI model to add a <em>trailer</em> during encapsulation?</summary>

Data Link

All layers in the OSI model add a header during encapsulation, but the data link layer also adds a trailer.

</details>

<details>

<summary>Does encapsulation provide an extra layer of security (Aye/Nay)?</summary>

Aye

The data link layer's trailer mathematically verifies that the data has not been corrupted during transmission. This feature also protects against tampering.

</details>

## Task 4: The TCP/IP Model

TODO

<details>

<summary>Which model was introduced first, OSI or TCP/IP?</summary>

TCP/IP

The TCP/IP model is older than OSI and serves as a basis for real-world networking.

</details>

<details>

<summary>Which layer of the TCP/IP model covers the functionality of the Transport layer of the OSI model (Full Name)?</summary>

Transport

TODO

</details>

<details>

<summary>Which layer of the TCP/IP model covers the functionality of the Session layer of the OSI model (Full Name)?</summary>

Application

TODO

</details>

<details>

<summary>The Network Interface layer of the TCP/IP model covers the functionality of two layers in the OSI model. These layers are Data Link, and?.. (Full Name)?</summary>

Physical

TODO

</details>

<details>

<summary>Which layer of the TCP/IP model handles the functionality of the OSI network layer?</summary>

Internet

TODO

</details>

<details>

<summary>What kind of protocol is TCP?</summary>

Connection-based

TODO

</details>

<details>

<summary>What is SYN short for?</summary>

Synchronise

TODO

</details>

<details>

<summary>What is the second step of the three way handshake?</summary>

SYN/ACK

TODO

</details>

<details>

<summary>What is the short name for the "Acknowledgement" segment in the three-way handshake?</summary>

ACK

TODO

</details>

## Task 5: Ping

The `ping` command can be used to test whether a connection to a remote resource is possible. This command can be run with `ping <resource>`.

<details>

<summary>What command would you use to ping the bbc.co.uk website?</summary>

ping bbc.co.uk

You can ping a website using `ping <resource>`.

</details>

<details>

<summary>Ping <em>muirlandoracle.co.uk.</em> What is the IPv4 address?</summary>

217.160.0.152

Run `ping muirlandoracle.co.uk.` and look at the response to see the IPv4 address.

</details>

<details>

<summary>What switch lets you change the interval of sent ping requests?</summary>

\-i

View the manual with `man ping` to see options for the `ping` command.

</details>

<details>

<summary>What switch would allow you to restrict requests to IPv4?</summary>

\-4

View the manual with `man ping` to see options for the `ping` command.

</details>

<details>

<summary>What switch would give you a more verbose output?</summary>

\-v

View the manual with `man ping` to see options for the `ping` command.

</details>

## Task 6: Traceroute

`traceroute` can be used to map the path a request takes as it heads to the target machine. On Linux, the command is run as `traceroute <destination>`. The Windows equivalent to `traceroute` is `tracert`. Linux uses UDP by default, while Windows uses ICMP.

<details>

<summary>What switch would you use to specify an interface when using Traceroute?</summary>

\-i

View the manual with `man traceroute` to see options for the `traceroute` command.

</details>

<details>

<summary>What switch would you use if you wanted to use TCP SYN requests when tracing the route?</summary>

\-T

View the manual with `man traceroute` to see options for the `traceroute` command.

</details>

<details>

<summary>[Lateral Thinking] Which layer of the <em>TCP/IP</em> model will traceroute run on by default (Windows)?</summary>

Internet

TODO

</details>

## Task 7: WHOIS

`whois` allows us to query who a domain name is registered to. In Europe personal details are redacted; however, elsewhere a great deal of information may be available. The tool can be installed with `sudo apt-get install whois` and run with `whois <domain>`.

<details>

<summary>What is the registrant postal code for facebook.com?</summary>

94025

Run `whois facebook.com` and look for the registrant postal code.

</details>

<details>

<summary>When was the facebook.com domain first registered (Format: DD/MM/YYYY)?</summary>

29/03/1997

Run `whois facebook.com` and look for the registration date.

</details>

<details>

<summary>Which city is the registrant based in?</summary>

Redmond

Run `whois facebook.com` and look for the city of the registrant.

</details>

<details>

<summary>[OSINT] What is the name of the golf course that is near the registrant address for microsoft.com?</summary>

Bellevue Golf Course

I used Google Maps to search for golf courses near the listed registrant address.

</details>

<details>

<summary>What is the registered Tech Email for microsoft.com?</summary>

msnhst@microsoft.com

Run `whois microsoft.com` and look for the registered tech email.

</details>

## Task 8: Dig

The Domain Name System (DNS) protcol TODO.

<details>

<summary>What is DNS short for?</summary>

Domain Name System

The Domain Name System the protocol that allows us to use easy-to-remember names to communicate with devices on the Internet. 

</details>

<details>

<summary>What is the first type of DNS server your computer would query when you search for a domain?</summary>

Recursive

A recursive DNS server will be the queried by a computer first. It will check its cache for an address before going to a root server to seek out an answer.

</details>

<details>

<summary>What type of DNS server contains records specific to domain extensions (i.e. <em>.com,</em> .co.uk*, etc)*? Use the long version of the name.</summary>

Top-Level Domain

Top-level domains are the TODO.

</details>

<details>

<summary>Where is the very first place your computer would look to find the IP address of a domain?</summary>

Hosts File

TODO

</details>

<details>

<summary><strong>[Research]</strong> Google runs two public DNS servers. One of them can be queried with the IP 8.8.8.8, what is the IP address of the other one?</summary>

8.8.4.4

Search "Google public DNS servers" on Google.

</details>

<details>

<summary>If a DNS query has a TTL of 24 hours, what number would the dig query show?</summary>

86400

Dig shows time in seconds, so the query would show $24 \cdot 60 \cdot 60 = 86400$.

</details>

## Task 9: Further Reading

[CISCO Self Study Guide](https://www.amazon.co.uk/Interconnecting-Cisco-Network-Devices-ICND1/dp/1587054620/ref=sr_1_1?keywords=Interconnecting+Cisco+Network+Devices%2C+Part+1&qid=1583683766&sr=8-1) by Steve McQuerry is a great resource to learn more about networking theory.

***

[Home](https://app.gitbook.com/o/0kO27okC5uVB9ALX3rho/s/036xtfEIzcEdGegONXWM/) ⋅ [Work](https://app.gitbook.com/o/0kO27okC5uVB9ALX3rho/s/WaFS755Q4sf02CxLcghQ/) ⋅ [Thoughts](https://app.gitbook.com/o/0kO27okC5uVB9ALX3rho/s/s4QQPMntQ25hmJToKSOu/)
