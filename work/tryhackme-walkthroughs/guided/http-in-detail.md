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

# HTTP in Detail

[TryHackMe Walkthroughs](./) ⋅ [Guided](../) ⋅ HTTP in Detail

***

## Task 1: What is HTTP(S)?

<details>
  <summary>What does HTTP stand for?</summary>
  HyperText Transfer Protocol
</details>

<details>

<summary>What does the S in HTTPS stand for?</summary>

Secure

</details>

<details>

<summary>On the mock webpage on the right there is an issue, once you've found it, click on it. What is the challenge flag?</summary>

THM{INVALID\_HTTP\_CERT}

</details>

## Task 2: Requests And Responses

<details>

<summary>What HTTP protocol is being used in the above example?</summary>

HTTP/1.1

</details>

<details>

<summary>What response header tells the browser how much data to expect?</summary>

Content-Length

</details>

## Task 3: HTTP Methods

<details>

<summary>What method would be used to create a new user account?</summary>

POST

</details>

<details>

<summary>What method would be used to update your email address?</summary>

PUT

</details>

<details>

<summary>What method would be used to remove a picture you've uploaded to your account?</summary>

DELETE

</details>

<details>

<summary>What method would be used to view a news article?</summary>

GET

</details>

## Task 4: HTTP Status Codes

<details>

<summary>What response code might you receive if you've created a new user or blog post article?</summary>

201

201 is the Created response code.

</details>

<details>

<summary>What response code might you receive if you've tried to access a page that doesn't exist?</summary>

404

404 is the Page Not Found response code.

</details>

<details>

<summary>What response code might you receive if the web server cannot access its database and the application crashes?</summary>

503

503 is the Service Unavailable response code.

</details>

<details>

<summary>What response code might you receive if you try to edit your profile without logging in first?</summary>

401

401 is the Not Authorized response code.

</details>

## Task 5: Headers

<details>

<summary>What header tells the web server what browser is being used?</summary>

User-Agent

</details>

<details>

<summary>What header tells the browser what type of data is being returned?</summary>

Content-Type

</details>

<details>

<summary>What header tells the web server which website is being requested?</summary>

Host

</details>

## Task 6: Cookies

<details>

<summary>Which header is used to save cookies to your computer?</summary>

Set-Cookie

</details>

## Task 7: Making Requests

<details>

<summary>Make a GET request to /room</summary>

THM{YOU'RE\_IN\_THE\_ROOM}

</details>

<details>

<summary>Make a GET request to /blog and using the gear icon set the id parameter to 1 in the URL field</summary>

THM{YOU\_FOUND\_THE\_BLOG}

</details>

<details>

<summary>Make a DELETE request to /user/1</summary>

THM{USER\_IS\_DELETED}

</details>

<details>

<summary>Make a PUT request to /user/2 with the username parameter set to admin</summary>

THM{USER\_HAS\_UPDATED}

</details>

<details>

<summary>POST the username of thm and a password of letmein to /login</summary>

THM{HTTP\_REQUEST\_MASTER}

</details>

***

[Home](https://app.gitbook.com/o/0kO27okC5uVB9ALX3rho/s/036xtfEIzcEdGegONXWM/) ⋅ [Work](https://app.gitbook.com/o/0kO27okC5uVB9ALX3rho/s/WaFS755Q4sf02CxLcghQ/) ⋅ [Thoughts](https://app.gitbook.com/o/0kO27okC5uVB9ALX3rho/s/s4QQPMntQ25hmJToKSOu/)
