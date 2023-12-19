---
layout: default
title:  "Threads and Processes"
date:   2023-12-05 11:05:00 -0400
categories: blog
---

Today, I cover __Threads and Processes__ from the [programmingexpert.io][course-site] course.

""""""

# Key Terms

<u>Thread<u>

A __thread__ is a flow of execution of your program. By default, Python will run your program in a single thread, the __main__ thread, which will execute your Python code line by line.

When trying to speed up certain programs using __concurrency__, many programs choose to run multiple threads at the same time. The __threading__ package that comes pre-installed contains functions and classes that allow you to create new threads and coordinate them.

The most important elements of this library are: __Thread__ and __Lock__.

<u>Process<u>

A __process__ is an application or program that is running on your computer. Processes are allocated their own memory space and always contain at least one thread, but may be split into multiple threads that are executing concurrently.

<u>Concurrency<u>

__Concurrency__ refers to the ability for parts of a program, application or algorithm (i.e. multiple threads) to be executed simultaneously.

<u>Parallelism<u>

__Parallelism__ refers to several computations occuring at the same time. Parallel programs utilize multiple logical processing cores of your CPU to increase speed. This is different from a concurrent program that may only utilize a single logical CPU core.

""""""

# Notes

- Processes are executable programs that contain multiple threads. Threads execute part of a program and can be thought of as light weight processes. Threads share data and memory with other threads attached to their process. Operating systems have special thread management systems that can allow for multiple threads to be run at the same time.

- Most modern day processors have more logical cores than they do physical cores due to a technology called hyperthreading (for intel CPU's) and clustered multithreading (for AMD CPU's). This allows each physical core to perform 2 operations at the same time, hence why a 4 core CPU with hyperthreading is said to have 8 logical cores. The number of logical cores determines how many operations can be performed in parallel.

- All operations performed by the CPU are a part of a thread and only one operation per thread can be ran at anytime. Therefore, a processor with 8 logical cores can run 8 threads at a time, or more specifically work on 8 operations in 8 different threads simultaneously.

- Threads running concurrently do not operate simultaneously, only one thread is ran at a time. You typically run threads concurrently (as opposed to in parallel) when the operations in one thread depend on results or computations from another or there is a chance a thread may be hanging (waiting on an external operation).

- For example, you may divide an application in two concurrent threads as such. One thread sends a user an email and another handles the user interface or front-end of the application. Sending a user an email would rely on a network bound operation which is not controlled by the application or local machine. This means while the email is sending the current thread would be hanging, not performing any operations, simply waiting for the email to send. When the thread is idling the program would allow the user interface thread to run such that the user does not notice any delay or lag in the interface while the email is waiting to send. If this program was not divided into two threads then while the email was sending the user interface would be unusable as the current active thread would be waiting on an operation and couldn't perform any other tasks.

- __Hyperthreading__ splits __physical__ cores into twice as many __logical__ cores.

""""""

[course-site]: https://www.programmingexpert.io/index