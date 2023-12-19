---
layout: default
title:  "Python Global Interpreter Lock"
date:   2023-12-06 11:05:00 -0400
categories: blog
---

Today, I cover __Python Global Interpreter Lock__ from the [programmingexpert.io][course-site] course.

""""""

# Key Terms

<u>Mutex<u>

A __mutex__ is a __mutually exclusive lock__ that controls the access to a section of code. Mutex's are typically used in multi-threaded programs when a section of code should only be executed by one thread at a time. If one thread has aquired the mutex all other threads must wait until that thread releases it before they can execute that locked section of code.


""""""

# Notes

- The Python global interpreter lock __disallows__ multiple threads to run simultaneously (in parallel).

- In many other programming languages, the interpreter can be used by multiple threads at once, a.k.a. in parallel.

- Python threads can run concurrently.

- The Global Interpreter lock exists in Python for simplicity, efficiency, and memory management.

- Threads in parallel can perform conflicting operations on the same object in the computer's memory, which can lead to inconsistencies in the data.

- __C__ runs behind the scenes with Python.

- The Global Interpreter lock keeps reference count variables consistent.

""""""

[course-site]: https://www.programmingexpert.io/index