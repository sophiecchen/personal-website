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

Task 1

<details>

<summary>What does DNS stand for?</summary>

Domain Name System

</details>

## Task 2: Domain Hierarchy

<details>

<summary>What is the maximum length of a subdomain?</summary>

63

</details>

<details>

<summary>Which of the following characters cannot be used in a subdomain ( 3 b _ - )?</summary>

\_

</details>

<details>

<summary>What is the maximum length of a domain name?</summary>

253

</details>

<details>

<summary>What type of TLD is .co.uk?</summary>

ccTLD

ccTLD stands for country code top-level domain.

</details>

## Task 3: Record Types

<details>

<summary>What type of record would be used to advise where to send email?</summary>

MX

</details>

<details>

<summary>What type of record handles IPv6 addresses?</summary>

AAAA

</details>

## Task 4: Making A Request

<details>

<summary>What field specifies how long a DNS record should be cached for?</summary>

TTL

TTL stands for Time to Live (ie how much time the DNS record should live in cache).

</details>

<details>

<summary>What type of DNS Server is usually provided by your ISP?</summary>

Recursive

</details>

<details>

<summary>What type of server holds all the records for a domain?</summary>

Authoritative

</details>

## Task 5: Practical

<details>

<summary>What is the CNAME of shop.website.thm?</summary>

shops.myshopify.com

</details>

<details>

<summary>What is the value of the TXT record of website.thm?</summary>

THM{7012BBA60997F35A9516C2E16D2944FF}

</details>

<details>

<summary>What is the numerical priority value for the MX record?</summary>

30

</details>

<details>

<summary>What is the IP address for the A record of www.website.thm?</summary>

10.10.10.10

</details>

***

[Home](https://app.gitbook.com/o/0kO27okC5uVB9ALX3rho/s/036xtfEIzcEdGegONXWM/) ⋅ [Work](https://app.gitbook.com/o/0kO27okC5uVB9ALX3rho/s/WaFS755Q4sf02CxLcghQ/) ⋅ [Thoughts](https://app.gitbook.com/o/0kO27okC5uVB9ALX3rho/s/s4QQPMntQ25hmJToKSOu/)
