---
layout: default
title:  "Decorators"
date:   2023-11-28 11:05:00 -0400
categories: blog
---

Today, I cover __Decorators__ from the [programmingexpert.io][course-site] course.

""""""

# Key Terms

<u>Decorator<u>

__Decorators__ describe a special kind of function that is meant to __wrap__ another function. The canonical example is to write a decorator that is meant to print out the time it took for a given function to execute whenever it is called.

A particular __@__ notation is used to indicate that a function should be wrapped by one or more __decorators__:

    1 | @timer
    2 | def run_simulation():
    3 |     ...

""""""

# Notes

- __\___ is a syntax feature in Python, known as an anonymous variable. It is a "place holder" for a variable.

Anonymous Variable Example:

    def loop():
        for _ in range(10000):
            pass

Timer Decorator Example:

    import time

    def timer(func):
        def wrapper(*args, **kwargs):
            start_time = time.time()
            result = func(*args, **kwargs)
            end_time = time.time()

            total_time = end_time - start_time
            print("Time taken to execute: ", total_time)
            return result

        return wrapper

- The __purpose__ of a decorator is to enforce some type of behaviour or to do something before or after a function is called. 

- Make sure the decorator will work for any function passed to it. This often involves the use of __*args__, __**kwargs__ and __returning the result__ of the function passed to the decorator.

- When using multiple decorators the modifications of the second decorator (one furthest to the function) will be applied to the modifications of the first decorator (one closest to the function). 

Here is an example of a function that uses multiple decorators:

    1 | @timer
    2 | @log_output
    3 | def func():
    4 |     ...
    5 |
    6 | # This is the same as making this call... timer(log_output(func()))

""""""

# Exercise One

""""""

In Python, the following function is considered a decorator?:

    1 | def a(func):
    2 |     def b():
    3 |         print("start")
    4 |         func()
    5 |         print("end")

<u>Answer<u>

__False__

<u>Explanation<u>

The formal definition of a decorator is "a function that takes another function and extends the behavior of the latter function without explicitly modifying it". This function is _almost_ a decorator but is missing an important feature, the __return__ statement. This function does not return the inner function and therefore is not a proper decorator. It can still be used as a decorator but any function decorated with it will not be executable.

""""""

# Exercise Two

""""""

Write a decorator function named __add_one__ that simply adds one to the return value of any function it decorates. Then use this function to decorate the __add_values__ function. Assume the arguments passed to __add_values__ will always be integers.

Sample Out put:

    1 | >>> add_values(2, 2)
    2 | 5

<u>Answer<u>:

    def add_one(func):
        def wrapper(*args, **kwargs):
            result = func(*args, **kwargs)
            return result + 1
        return wrapper

    @add_one
    def add_values(x, y):
        return x + y

""""""

# Exercise Three

""""""

Write a decorator function named __print_return_value__ that prints the return value of any function it decorates. The decorator should work on any function, regardless of the number of parameters.

<u>Answer<u>:

    def print_return_value(func):
        def wrapper(*args, **kwargs):
            result = func(*args, **kwargs)
            print(result)
            return result
        return wrapper

""""""

[course-site]: https://www.programmingexpert.io/index