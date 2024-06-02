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

# DNS in Detail

[TryHackMe Walkthroughs](./) ⋅ [Guided](../) ⋅ DNS in Detail

***

## Task 1: What is DNS?

Devices on the Internet are identified with an address called an IP address. IP addresses such as 104.26.10.229 can be difficult to remember. To make IP addresses more friendly to humans, we use a protocol called the Domain Name System (DNS). DNS translates between IP addresses and domain names such as tryhackme.com and allows us to communicate with devices more easily.

<details>

<summary>What does DNS stand for?</summary>

Domain Name System

The Domain Name System protocol allows us to use easy-to-remember names to communicate with devices on the Internet. 

</details>

## Task 2: Domain Hierarchy

A domain can be split into different levels. Consider the domain `https://feodotracker.abuse.ch`.
* **.ch**: This is the top-level domain (TLD). TLDs can be generic TLDs (gTLD) or country code TLDs (ccTLD).
* **abuse**: This is a second-level domain. When registering a domain name, the second-level domain is limited to 63 characters and can only use the characters a-z, 0-9, and hyphens.
* **feodotracker**: This is a subdomain, which is separated from the second-level domain by a period. It has the same restrictions as a second-level domain. There can be multiple subdomains as long as the entire domain name is 253 characters or less.

<details>

<summary>What is the maximum length of a subdomain?</summary>

63

A subdomain name has the same creation restrictions as a Second-Level Domain, being limited to 63 characters.

</details>

<details>

<summary>Which of the following characters cannot be used in a subdomain ( 3 b _ - )?</summary>

\_

A subdomain can onl use the characters a-z, 0-9, and hyphens.

</details>

<details>

<summary>What is the maximum length of a domain name?</summary>

253

A domain name is limited to 253 characters or less.

</details>

<details>

<summary>What type of TLD is .co.uk?</summary>

ccTLD

ccTLD stands for country code top-level domain.

</details>

## Task 3: Record Types

There are many types of DNS records.
* **A**: These records resolve IPv4 addresses
* **AAAA**: These records resolve IPv6 addresses
* **CNAME**: These records resolve another domain name
* **MX**: These records resolve to the address of the servers that handle the email for the domain you are querying
* **TXT**: These records are free text fields where any text-based data can be stored and are commonly used to verify domain ownership and list authortative servers to check for spoofing

<details>

<summary>What type of record would be used to advise where to send email?</summary>

MX

The server that handles email for a specific domain can be found using an MX record.

</details>

<details>

<summary>What type of record handles IPv6 addresses?</summary>

AAAA

AAAA records resolve IPv6 addresses.

</details>

## Task 4: Making A Request

When you make a DNS request, the following steps occur:
1. The computer checks its cache to see if the address has been looked up recently. If the address is not in the cache, a request to the computer's Recursive DNS Server is made.
2. The Recursive DNS Server, usually provided by an ISP, checks its cache for the address. to send back to the computer. If the address is not in the cache, then root servers are used.
3. The root server directs the computer to the correct Top Level Domain Server.
4. The TLD server holds records for where to find the authortative server, or nameserver, to answer the DNS request.
5. The authoritative server is responsible for storing the DNS records for a particular domain name. THe DNS record may also be sent back to the Recursive DNS server in order to be cached for a certain amount time, specified by the record's time to live (TTL) value.

<details>

<summary>What field specifies how long a DNS record should be cached for?</summary>

TTL

TTL stands for Time to Live (ie how much time the DNS record should live in cache).

</details>

<details>

<summary>What type of DNS Server is usually provided by your ISP?</summary>

Recursive

A recursive DNS server is usually provided by the ISP, which will check its cache for an address before going to a root server to seek out an answer.

</details>

<details>

<summary>What type of server holds all the records for a domain?</summary>

Authoritative

An authortative server is also known as the nameserver for a domain and holds all of that domain's records.

</details>

## Task 5: Practical

Open the site associated with the task to answer the following questions.

<details>

<summary>What is the CNAME of shop.website.thm?</summary>

shops.myshopify.com

Change the DNS type to CNAME and add "shop" as the subdomain. Then, send a DNS request.

</details>

<details>

<summary>What is the value of the TXT record of website.thm?</summary>

THM{7012BBA60997F35A9516C2E16D2944FF}

Change the DNS type to TXT. Then, send a DNS request.

</details>

<details>

<summary>What is the numerical priority value for the MX record?</summary>

30

Change the DNS type to MX. Then, send a DNS request.

</details>

<details>

<summary>What is the IP address for the A record of www.website.thm?</summary>

10.10.10.10

Change the DNS type to A. Then, send a DNS request.

</details>

***

[Home](https://app.gitbook.com/o/0kO27okC5uVB9ALX3rho/s/036xtfEIzcEdGegONXWM/) ⋅ [Work](https://app.gitbook.com/o/0kO27okC5uVB9ALX3rho/s/WaFS755Q4sf02CxLcghQ/) ⋅ [Thoughts](https://app.gitbook.com/o/0kO27okC5uVB9ALX3rho/s/s4QQPMntQ25hmJToKSOu/)
