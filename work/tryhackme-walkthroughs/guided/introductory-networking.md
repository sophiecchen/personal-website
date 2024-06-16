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

This room provides an overview of key networking concepts. This room will teach us:
* The OSI Model
* The TCP/IP Model
* How these models look in practice
* Basic networking tools

## Task 2: The OSI Model: An Overview

The Open Systems Interconnection (OSI) Model is a standard model used in computer networking theory that breaks down computer networks into 7 layers. In practice, networking is more compact.
1. **Physical**: This layer is responsible for converting binary data into physical signals, transporting these signals, receiving them, and converting them back into binary data.
2. **Data Link**: This layer is responsible for adding a physical identifier, called the Media Access Control (MAC) address, of the receiving endpoint and presenting the data in a format suitable for transmission.
    * When receiving data, this layer also checks for errors.
3. **Network**: This layer is responsible for locating the destination of a request using the IP address.
4. **Transport**: This layer is responsible for selecting a protocol for transmission and dividng up the data into bite-sized pieces.
    * Transmission Control Protocol (TCP) is a common protocol that is connection-based and values accuracy over speed.
    * User Datagram Protocol (UDP) is a common protocol that is connectionless and values speed over accuracy.
    * The bite-sized pieces are called segments in TCP and datagrams in UDP.
5. **Session**: This layer sets up and maintains a connection, called a session, with the destination computer.
6. **Presentation**: This layer translate data into a standardized format that can be understood by the receiving computer and performs encryption, compression, and other data translations.
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

While bite-sized pieces are called datagrams in UDP, these pieces are called segments in TCP.

</details>

<details>

<summary>[Research] Which layer would the FTP protocol communicate with?</summary>

7

The File Transfer Protocol (FTP) communicates with the application layer.

</details>

<details>

<summary>Which transport layer protocol would be best suited to transmit a live video?</summary>

UDP

UDP is preferred in situations where speed is more important than accuracy.

</details>

## Task 3: Encapsulation

Suppose a computer wants to send information another. The data starts at layer 7 and works its way down to layer 1, where it is then sent to the other computer. At each layer, more information is added to the data in a process called encapsulation. 

The receiving computer then reverses encapsulation in a process called de-encapsulation.

The encapsulation and de-capsulation process allows for a standard format of transmititng data. Encapsulated data is given a different names at different layers. Each step in encapsulation can be referenced below.

![encapsulation](https://muirlandoracle.co.uk/wp-content/uploads/2020/02/image.jpeg)

Notice how, in addition to a header, layer 2 also adds a trailer. This trailer is used to verify that the data has not been corrupted or tampered with during transmission.

<details>

<summary>How would you refer to data at layer 2 of the encapsulation process (with the OSI model)?</summary>

frames

The data link layer, layer 2, works with frames.

</details>

<details>

<summary>How would you refer to data at layer 4 of the encapsulation process (with the OSI model), if the UDP protocol has been selected?</summary>

datagrams

The transport, layer 4, works with datagrams in the UDP protocol and segments in the TCP protocol.

</details>

<details>

<summary>What process would a computer perform on a received message?</summary>

de-encapsulation

A computer receiving a message performs de-encapsulation in order to recover the original data.

</details>

<details>

<summary>Which is the only layer of the OSI model to add a <em>trailer</em> during encapsulation?</summary>

data link

All layers in the OSI model add a header during encapsulation, but the data link layer also adds a trailer.

</details>

<details>

<summary>Does encapsulation provide an extra layer of security (Aye/Nay)?</summary>

aye

The data link layer's trailer mathematically verifies that the data has not been corrupted during transmission. This feature also protects against tampering.

</details>

## Task 4: The TCP/IP Model

The TCP/IP model for networking reflects how networking occurs in the real-world. This model consists of four layers:
1. Network interface
2. Internet
3. Transport
4. Application

These four layers cover the same functions as the seven layers of the OSI model. A comparison between these two networking models can be seen below.

![osi_v_tcpip](https://muirlandoracle.co.uk/wp-content/uploads/2020/02/image-3.png)

TCP/IP takes half of its name from TCP. Task 2 contrasted TCP, a connection-based protocol, with UDP, a connectionless protocol. To form a connection between two computers using TCP, a connection is first formed using a three-way handshake.
1. The intiating computer sends a request contiaining synchronize (SYN) information.
2. The receiving computer responds with the SYN information and an acknlowledgement (ACK), collectively referred to as SYN/ACK.
3. The intiating computer sends the ACK information back to the receiving computer.

After these three steps are completed, a connection between the two computers is established for reliable data transmission.

<details>

<summary>Which model was introduced first, OSI or TCP/IP?</summary>

TCP/IP

The TCP/IP model is older than OSI and serves as a basis for real-world networking.

</details>

<details>

<summary>Which layer of the TCP/IP model covers the functionality of the Transport layer of the OSI model (Full Name)?</summary>

transport

The transport layers of the OSI model and TCP/IP model are responsible for the same functionalities.

</details>

<details>

<summary>Which layer of the TCP/IP model covers the functionality of the Session layer of the OSI model (Full Name)?</summary>

application

The functionality of the OSI session layer is included in the TCP/IP application layer.

</details>

<details>

<summary>The Network Interface layer of the TCP/IP model covers the functionality of two layers in the OSI model. These layers are Data Link, and?.. (Full Name)?</summary>

physical

The TCP/IP network interface layer covers the functionalty of both the OSI data link and physical layers.

</details>

<details>

<summary>Which layer of the TCP/IP model handles the functionality of the OSI network layer?</summary>

internet

The network and internet layers of the OSI model and TCP/IP model are responsible for the same functionalities.

</details>

<details>

<summary>What kind of protocol is TCP?</summary>

connection-based

Unlike UDP, TCP is a connection-based protocol.

</details>

<details>

<summary>What is SYN short for?</summary>

synchronise

SYN is short for synchronize and is information sent by a computer initiating a connection to another using TCP.

</details>

<details>

<summary>What is the second step of the three way handshake?</summary>

SYN/ACK

After a SYN packet is sent to a server, the server responds with the SYN information and acknowledgement information. These two parts form a SYN/ACK packet.

</details>

<details>

<summary>What is the short name for the "Acknowledgement" segment in the three-way handshake?</summary>

ACK

The acknowledgement segment, which is the third part of the three-way handshake, is abbreviated as ACK.

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

`traceroute` can be used to map the path a request takes as it heads to the target machine. On Linux, the command is run as `traceroute <destination>`. The Windows equivalent to `traceroute` is `tracert`. Linux uses UDP by default, while Windows uses Internet Control Message Protocol (ICMP).

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

traceroute runs on ICMP by default on Windows. ICMP 

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

Use Google Maps to search for golf courses near the listed registrant address.

</details>

<details>

<summary>What is the registered Tech Email for microsoft.com?</summary>

msnhst@microsoft.com

Run `whois microsoft.com` and look for the registered tech email.

</details>

## Task 8: Dig

The Domain Name System (DNS) protcol translates between IP addresses, which identify computers on the Internet using strings of numbers like 10.10.10.10, and domain names, which identify computers on the Internet using strings of letters like tryhackme.com.

Here is the process for translating a domain name to an IP address. If the computer finds an IP address and domain match, then the translation process is complete.
1. When a domain is requested, the computer first checks its hosts file to see if an IP address has been explicitly mapped to a domain.
2. Next, the computer checks its local DNS cache to see if it has stored an IP address for the request domain.
3. The computer then sends a request to a recursive DNS server, which is usually provided by an Internet Service Provider (ISP).
    * A recursive DNS server checks its cache and then directs the computer to the proper place to find the associated IP address for the requested domain.
4. The computer queries root name servers, then Top-Level Domain (TLD) servers, and then authoritative name servers.
    * TLD servers are responsible for domain extensions such as .com and .gov.
    * Authoritative name servers are responsible for the main part of the domain, such as tryhackme or google.
    * When an authoritative name server is reached, it will send the requested data back to the computer.

<details>

<summary>What is DNS short for?</summary>

Domain Name System

The Domain Name System the protocol that allows us to use easy-to-remember names to communicate with devices on the Internet. 

</details>

<details>

<summary>What is the first type of DNS server your computer would query when you search for a domain?</summary>

recursive

A recursive DNS server will be the queried by a computer first. It will check its cache for an address before going to a root server to seek out an answer.

</details>

<details>

<summary>What type of DNS server contains records specific to domain extensions (i.e. <em>.com,</em> .co.uk*, etc)*? Use the long version of the name.</summary>

top-level domain

Top-level domains are the contains records for domain extensions such as .com and .gov.

</details>

<details>

<summary>Where is the very first place your computer would look to find the IP address of a domain?</summary>

hosts file

A computer first looks in the hosts file to see if an IP address has been explicitly mapped to a domain

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
