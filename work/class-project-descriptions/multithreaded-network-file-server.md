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

# Multithreaded Network File Server

This network file server, implement in C++, is crash-consistent and supports multiple users and nested directories and files. It uses POSIX sockets for client communication and Boost threads and upgradable reader-writer locks for concurrency.

The server supports functionality for reading a block of data (specified by pathname and offset), writing a block of data (specified by pathname and offset), creating a new file or directory "pathname", and deleting an existing file or directory "pathname".

*This project was completed for my operating systems class and is stored in a private GitHub, as per my university's honor code. If you are a involved in recruitment or hiring and would like to see the code for this project, please contact me.*

***

[Home](https://app.gitbook.com/o/0kO27okC5uVB9ALX3rho/s/036xtfEIzcEdGegONXWM/) ⋅ [Work](https://app.gitbook.com/o/0kO27okC5uVB9ALX3rho/s/WaFS755Q4sf02CxLcghQ/) ⋅ [Thoughts](https://app.gitbook.com/o/0kO27okC5uVB9ALX3rho/s/s4QQPMntQ25hmJToKSOu/)