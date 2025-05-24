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

# Thread Library

This thread library is a kernel library on Unix written in C++. This library uses timer interrupts, atomicity, and a FIFO scheduling order. It can be initialized with multiple CPUs. 

My partner and I were responsible for implementing the following functionality for the following objects:
* CPU:
  * Constructor, destructor
* Thread:
  * Constructor, destructor
  * `void join()`: waits for the thread to finish
  * `void yield()`: yields the CPU to the next thread
* Mutex:
  * Constructor, destructor
  * `void lock()`: locks the mutex
  * `void unlock()`: unlocks the mutex
* Condition Variable:
  * Constructor, destructor
  * `void wait(mutex &)`: waits on a condition variable with the associated mutex
  * `void signal()`: wakes up one thread associated with the condition variable
  * `void broadcast()`: akes up all threads associated with the condition variable

*This project was completed for my operating systems class and is stored in a private GitHub as per my university's honor code. If you are a involved in recruitment or hiring and would like to see the code for this project, please contact me.*

***

[Home](https://app.gitbook.com/o/0kO27okC5uVB9ALX3rho/s/036xtfEIzcEdGegONXWM/) ⋅ [Work](https://app.gitbook.com/o/0kO27okC5uVB9ALX3rho/s/WaFS755Q4sf02CxLcghQ/) ⋅ [Thoughts](https://app.gitbook.com/o/0kO27okC5uVB9ALX3rho/s/s4QQPMntQ25hmJToKSOu/)