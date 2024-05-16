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

HTTP (HyperText Transfer Protocol) is a protocol, or set of rules, used to communicate with web servers and transmit webpage data. HTTPS, the S standing for secure, is the encrypted version of HTTP.

<details>
<summary>What does HTTP stand for?</summary>

HyperText Transfer Protocol
</details>

<details>
<summary>What does the S in HTTPS stand for?</summary>

Secure

HTTPS is the secure and encrypted version of HTTP.
</details>

<details>
<summary>On the mock webpage on the right there is an issue, once you've found it, click on it. What is the challenge flag?</summary>

THM{INVALID\_HTTP\_CERT}

Notice the lock with the red slash on the left of the URL. This means that your connection is insecure.
</details>

## Task 2: Requests And Responses

A uniform resource locator (URL) is an instruction on how to access a resource on the Internet. Consider the url `http://user:password@tryhackme.com:80/view-room?id=1#task3`.
* **http**: This is the scheme, which instructs what protocol to use for accessing the resource
* **user:password**: This is the user since logging in may be necessary to access the resource 
* **tryhackme.com**: This is the host, the domain name or IP address of the resource
* **80**: This is the port to connect to
* **view-room**: This is the path, the file name or location of the resource
* **?id=1**: This is the query string, which includes extra bits of information that can be sent to the requested path
* **#task3**: This is the fragment, a reference to a location on the actual page that is only viewable to the client

HTTP uses a series of requests and responses to transmit data.

Consider this request:

```HTTP
GET / HTTP/1.1
Host: tryhackme.com
User-Agent: Mozilla/5.0 Firefox/87.0
Referer: https://tryhackme.com/

```

Line 1 says that we are making a GET request using HTTP/1.1 to the home page with /. Lines 2-4 are optional. Host indicates that we want `tryhackme.com`. User-agent indicates that we are using Firefox version 87 Browser, and referer indicates that we came from `tryhackme.com`. HTTP requests end with a blank line, meaning the request has finished.

Consider this response:

```HTTP
HTTP/1.1 200 OK
Server: nginx/1.15.8
Date: Fri, 09 Apr 2021 13:34:03 GMT
Content-Type: text/html
Content-Length: 98

<html>
<head>
    <title>TryHackMe</title>
</head>
<body>
    Welcome To TryHackMe.com
</body>
</html>
```

Line 1 indicates that the protocol used was HTTP 1.1 and that the request was successfully completed. Lines 2-5 indicate information about the server software, server date and time, the content type, and the length of the content. Following these lines is a blank line signalling the end of the HTTP response and the content sent by the server.

<details>
<summary>What HTTP protocol is being used in the above example?</summary>

HTTP/1.1

The HTTP protocol being used can be found on the first line of the request or response.
</details>

<details>
<summary>What response header tells the browser how much data to expect?</summary>

Content-Length

This header specifies the length of the content included in the response.
</details>

## Task 3: HTTP Methods

We can express our intended action when making an HTTP request using different methods.
* **GET**: Used for getting information from a web server
* **POST**: Used for submitting data to a web server, potentially creating new records
* **PUT**: Used for submitting data to a web server to update information
* **DELETE**: Used for deleting information from a web server

<details>

<summary>What method would be used to create a new user account?</summary>

POST

POST is used when we want to create a new record, such as a new user account.

</details>

<details>

<summary>What method would be used to update your email address?</summary>

PUT

PUT is used for updating information.

</details>

<details>

<summary>What method would be used to remove a picture you've uploaded to your account?</summary>

DELETE

DELETE is used for removing information.

</details>

<details>

<summary>What method would be used to view a news article?</summary>

GET

GET is used for receiving information, which can then be viewed.

</details>

## Task 4: HTTP Status Codes

When an HTTP server responds, the first line contains a status code informing the client of the outcome of their request.

Status codes can be broken down into 5 different ranges:
* **100-199**: These codes inform the client that the first part of their request was accepted and that they should send the rest of their request
* **200-299**: These codes inform the client that their request was successful
* **300-399**: These codes redirect the client's request to another resource
* **400-499**: These codes indicate there was a client-side error with the request
* **500-599**: These codes indicate that there was a server-side error with the request

Common HTTP status codes include, 200-OK, 400-Bad Request, 403-Forbidden, 404-Page Not Found, and 500-Internal Service Error.

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

Headers can be used to send additional information when making a HTTP request.

Common request headers include:
* **Host**: Specifies which website on the server is wanted
* **User-Agent**: Specifies the client browser and version number
* **Content-Length**: Speciifes the length of the content sent to the server
* **Accept-Encoding**:  Specifies what data compression methods the browser supports
* **Cookie**: Specifies a piece of data remembered by the browser and used by the server to remember client information

Common response headers include:
* **Set-Cookie**: Specifies a piece of data sent by the server that the browser will remember for later requests
* **Cache-Control**: Specifies how long to store the content of the response in the browser's cache
* **Content-Type**: Specifies what type of content is being returned so that the browser can properly process the data
* **Content-Encoding**: Specifies what method was used to compress the data

<details>

<summary>What header tells the web server what browser is being used?</summary>

User-Agent

User-Agent specifies browser and verison number.

</details>

<details>

<summary>What header tells the browser what type of data is being returned?</summary>

Content-Type

Content-Type, as per its name, specifies the type of content returned by the web server.

</details>

<details>

<summary>What header tells the web server which website is being requested?</summary>

Host

Host is used to specify which website on a web server is wanted. This header is especially important if a web server hosts multiple websites.

</details>

## Task 6: Cookies

HTTP is a stateless protocol, meaning it does not keep track of previous requests. Thus, a server remembers a client by sending a cookie, a small piece of data that is stored by the browser, with the Set-Cookie header. Whenever the client queries the server in the future, the cookie is sent along with the request using the Cookie header. Cookies allows a server to keep track of clients.

<details>

<summary>Which header is used to save cookies to your computer?</summary>

Set-Cookie

Set-Cookie is a header included in HTTP responses that includes a cookie for the browser to save.

</details>

## Task 7: Making Requests

Practice making requests by viewing the site associated with this task.

<details>

<summary>Make a GET request to /room</summary>

THM{YOU'RE\_IN\_THE\_ROOM}

Change the request type to GET and type room into the search bar. Then, press go.

</details>

<details>

<summary>Make a GET request to /blog and using the gear icon set the id parameter to 1 in the URL field</summary>

THM{YOU\_FOUND\_THE\_BLOG}

Change the request type to GET and type blog into the search bar. Set the id parameter to 1 and press go.

</details>

<details>

<summary>Make a DELETE request to /user/1</summary>

THM{USER\_IS\_DELETED}

Change the request type to DELETE and type user/1 into the search bar.

</details>

<details>

<summary>Make a PUT request to /user/2 with the username parameter set to admin</summary>

THM{USER\_HAS\_UPDATED}

Change the request type to PUT and type user/2 into the search bar. Set the username parameter to admin and press go.

</details>

<details>

<summary>POST the username of thm and a password of letmein to /login</summary>

THM{HTTP\_REQUEST\_MASTER}

Change the request type to POST and type login into the search bar. Set the username parameter to thm, the password parameter to letmein, and press go.

</details>

***

[Home](https://app.gitbook.com/o/0kO27okC5uVB9ALX3rho/s/036xtfEIzcEdGegONXWM/) ⋅ [Work](https://app.gitbook.com/o/0kO27okC5uVB9ALX3rho/s/WaFS755Q4sf02CxLcghQ/) ⋅ [Thoughts](https://app.gitbook.com/o/0kO27okC5uVB9ALX3rho/s/s4QQPMntQ25hmJToKSOu/)
