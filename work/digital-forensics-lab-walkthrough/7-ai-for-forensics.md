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

# 7 AI For Forensics

[Digital Forensics Lab Walkthrough](./) ⋅ 7 AI For Forensics

***

## IP Addresses as Digital Forensic Evidence

Mobile devices contain multiple configuration files, and configuration files contains lots of potential digital evidence, such as server IP addresses. However, identifying the correct IP address of a mobile device is not as straigthforward as it sounds. Many strings, such as version numbers for example, look similar to IP addresses.

With the recent explosion of applications using AI, using AI techniques to IP addresses from configuration files seems plausible. This section will focus on evaluating how IP addresses from iOS configuration files using fine-tuned pre-trained language models.

TODO

Use regular expressions to identify possible IPs
Inputs: a text line from a configuration file contains all possible IPs 
output: all possible IPs (positive or negative)
false positives are included intentionally 
Utilize OpenAI language model to identify if the IP is correct
Binary classification
Inputs: the text line + IPs identified with regular expression
Output: the possible IP a real IP or not (positive or negative)

## Introduction to Object Identification with AI

At a high level, AI can be broken down into feeding TODO.

## Identifying IP Addresses via Fine-tuned Models

### Data Processing, Training, Testing, and Validation

## Summary

***

[Home](https://app.gitbook.com/o/0kO27okC5uVB9ALX3rho/s/036xtfEIzcEdGegONXWM/) ⋅ [Work](https://app.gitbook.com/o/0kO27okC5uVB9ALX3rho/s/WaFS755Q4sf02CxLcghQ/) ⋅ [Thoughts](https://app.gitbook.com/o/0kO27okC5uVB9ALX3rho/s/s4QQPMntQ25hmJToKSOu/)
