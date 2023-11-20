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

A __lambda__ is an anonymous function that can be defined in-line without the use of the __def__ keyword. This is extremely useful when defining a custom sort ordering for a collection. Example:

     1 | # Here we have a list of tuples,
     2 | # each representing a food and its price.
     3 | lst = [
     4 |    ('cake', '30'),
     5 |    ('orange', '3'),
     6 |    ('pasta', '20')
     7 | ]
     8 |
     9 | # This lambda function lets us sort
    10 | # by the price of the items.
    11 | lst.sort(key=lambda x:x[1]) 

""""""

# Notes

- In Python, __lambda__ functions can have any number of arguments. 

Here is an example of a __lambda__ function with multiple parameters:

    lambda x, y: x + y + 5

- In Python, __lambda__ functions can have optional parameters. 

Here is an example of a __lambda__ with an optional parameter:

    lambda x, y=1: x + y + 5

- In Python, __lambda__ functions can accept positional arguments. 

Here is an example of calling a __lambda__ function using a keyword argument:

    func = lambda x, y: x + y + 5
    func(y=1, x=1)  # this will return 7

""""""

# Exercise One

""""""

In Python, what expression would result in __ab\|__ being printed to the screen?:

    1 | a = lambda y: lambda x: lambda z: print(x + y, end=z)

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