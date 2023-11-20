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

- The main use case for __lambda__ is defining a function where it is going to be used.

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

- Using a __lambda__ to return a __lambda__ is a form of __nested__ functions.

Example:

    mul = lambda x: lambda y: x * y
    result = mul(2)  #  Lambda y: 2 * y, is assigned to result here
    print(result(4))  #  8, is printed

Similar to:

    def mul(x):
        def mul2(y):
            return x * y
        return mul2

    result = mul(2)  #  2 * y, is assigned
    print(result(4))  #  8

    # chained calls can also be used

    result = mul(2)(4)
    print(result)  #  8, is printed

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

Write the following __lambda__ functions.

- A __lambda__ function that takes three integer of float parameters and returns their sum. You should store this __lambda__ function in the variable __add_values__.

- A __lambda__ function that takes two string parameters and returns the maximum of their lengths. You should store this __lambda__ function in the variable __max_length__.

- a __lambda__ function that takes two list parameters and returns a set containing the elements from both lists. You should store this __lambda__ function in the variable __create_set__.

Sample Output:

    1 | >>> add_values(3, 4, 5)
    2 | 12
    3 | >>> max_length("hello", "tim")
    4 | 5
    5 | >>> create_set([1, 2, 3, 4], [2, 3, 5])
    6 | {1, 2, 3, 4, 5}

Solution:

    add_values = lambda x, y, z: x + y + z
    max_length = lambda x, y: max(len(x), len(y))
    create_set = lambda x, y: set(x) | set(y)

""""""

[course-site]: https://www.programmingexpert.io/index