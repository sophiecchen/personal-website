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

# 1 Setting Up

***

## Kali Linux and VirtualBox

I use a laptop that runs Windows 11. To setup my system for this lab, I used the first method listed in the README of the Github repository. I followed Method 1: Importing customized Kali VM image because it appeared to be the most reliable way to setup all the tools I needed.

I already had VirtualBox downloaded on my laptop, so I proceeded by downloading the Kali VM provided in the README. I clicked File -> Import Appliance and choose the Kali VM file I downloaded. This VM's default settings gave the VM too many cores and too much base memory for my laptop to handle, so I had to reduce the amount of resources dedicated to the VM. I also had a "No NAT Network name is currently specified" error. I resolved this error by clicking Tools -> NAT Networks -> Create.

I powered up the machine and used the [default credentials](https://www.kali.org/docs/introduction/default-credentials/) for Kali Linux to login. I noticed that I had some installation errors with this VM. In particular, [Volatility](https://www.volatilityfoundation.org/) failed to download. Furthermore, it appeared that Python 2.7 was being used, which is a deprecated version (as of February 2024, when I am completing this lab). I attempted to run the `install.sh` executable included with the VM, but this did not resolve all installation errors. I took note of these errors and decided that I would install these tools manually when they were needed.

I took a snapshot of my machine in VirtualBox by pressing clicking the hamburger menu (☰) -> Snapshots -> Take.

#### Up Next: [2.1 Number Systems](2-basic-computer-skills-for-digital-forensics/2.1-number-systems.md)

***

[Home](https://app.gitbook.com/o/0kO27okC5uVB9ALX3rho/s/036xtfEIzcEdGegONXWM/) ⋅ [Work](https://app.gitbook.com/o/0kO27okC5uVB9ALX3rho/s/WaFS755Q4sf02CxLcghQ/) ⋅ [Thoughts](https://app.gitbook.com/o/0kO27okC5uVB9ALX3rho/s/s4QQPMntQ25hmJToKSOu/)
