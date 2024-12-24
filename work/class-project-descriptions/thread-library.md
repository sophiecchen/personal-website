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
* CPU: constructor, destructor
* Thread: constructor, destructor, `void join()` and `void yield()` where `join` waits for the thread to finish and `yield` yields the CPU to the next thread
* Mutex: constructor, destructor, `void lock()`, and `void unlock()` where `lock` locks the mutex and `unlock` unlocks the mutex
* Condition Variable: constructor, destructor, `void wait(mutex &)`, `void signal()`, and `void broadcast()`, where `wait` waits on a condition variable with the associated mutex, `signal` wakes up one thread associated with the condition variable, and `broadcast` wakes up all threads associated with the condition variable

*This project was completed for my operating systems class and is stored in a private GitHub. If you would like to see the code for this project, please contact me.*

***

[Home](https://app.gitbook.com/o/0kO27okC5uVB9ALX3rho/s/036xtfEIzcEdGegONXWM/) ⋅ [Work](https://app.gitbook.com/o/0kO27okC5uVB9ALX3rho/s/WaFS755Q4sf02CxLcghQ/) ⋅ [Thoughts](https://app.gitbook.com/o/0kO27okC5uVB9ALX3rho/s/s4QQPMntQ25hmJToKSOu/)