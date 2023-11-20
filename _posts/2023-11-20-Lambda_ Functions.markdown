---
layout: default
title:  "Lambda Functions"
date:   2023-11-20 12:25:00 -0400
categories: blog
---

Today, I cover __Lambda Functions__ from the [programmingexpert.io][course-site] course.

""""""

# Key Terms

<u>Lambda<u>

""""""

# Notes

- In Python, __lambda__ functions can have any number of arguments. 

Here is an example of a __lambda__ function with multiple parameters:

    lambda x, y: x + y + 5

- In Python, __lambda__ functions can have optional parameters. 

Here is an example of a __lambda__ with an optional parameter:

    lambda x, y=1: x + y + 5

- In Python, lambda functions can accept positional arguments. 

Here is an example of calling a lambda function using a keyword argument:

    func = lambda x, y: x + y + 5
    func(y=1, x=1)  # this will return 7

""""""

# Exercise One

""""""

<u>Answer<u>

__a("b")("a")("\|")__

<u>Explanation<u>

__a__ holds a complicated __lambda__ function because it returns a __lambda__ that returns a __lambda__. This means we'll need three subsequent function calls to execute the __print__ statement.

- When we call __a("b")__ a __lambda__ that looks like the following is returned __lambda x: lambda z: print(x + "b", end=z)__.
- When we call __a("b")("a")__ a __lambda__ that looks like the following is returned __lambda z: print("a" + "b", end=z)__.
- When we call __a("b")("a")("\|")__ we execute the print statement with __y = "b"__, __x = "a"__ and __z = "\|"__.

""""""

# Exercise Two

""""""

""""""

[course-site]: https://www.programmingexpert.io/index