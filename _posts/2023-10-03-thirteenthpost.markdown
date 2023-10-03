---
layout: default
title:  "Math, Random, and Sorting"
date:   2023-10-03 10:23:00 -0400
categories: blog
---
Today I covered Math and Sorting in Python from the [programmingexpert.io][course-site] course.

""""""

The standard library of a language are the libraries that the language comes with by default. In Python, this includes modules like os, math, threading and many more.

""""""

"""Math"""

import math

The math module is part of the Python standard library, and it has many nice functions that we may need. For instance, math.sin(x), math.cos(x), math.tan(x) and math.pi are available for the math module.

""""""

import random

The random module is part of the Python standard library, and provides many functions that can used to generate random numbers or make random choices. random.randint(start,stop), random.randrange(start, stop, step) and random.choice(iterable) are a few commonly used functions from the random module.

""""""

The following are math functions in Python that do not need to be imported.

abs(x) - returns the absolute value of the argument.

max(x) - returns its biggest item in an iterable object.

min(x) - returns its smallest item in an iterable object.

sum(x) - returns the sum of a 'start' value (default: 0) plus an iterable of numbers. When the iterable is empty, return the start value. This function is intended specifically for use with numeric values and may reject non-numeric types.

round(number, ndigits=None) - Rounds a number to a given precision in decimal digits. The return value is an integer if ndigits is omitted or None.  Otherwise, the return value has the same type as the number.  ndigits may be negative. 

""""""

"""Sorting"""

sorted(iterable, /, *, key=None, reverse=False) - Returns a new list containing all items from the iterable in ascending order. A custom key function can be supplied to customize the sort order, and the reverse flag can be set to request the result in descending order.

.sort() sorts and modifies the object in place.

When sorted(tup) is called on a tuple it is returned as a new sorted list. tup.sort() will not work on a tuple because a tuple is immutable.

"""Example of Sorting by Key"""

def sort_second_index(item):

    return item[1]

lst = [[1,-2], [3,-4], [5,-6], [-1,-2], [0,0]]

lst.sort(reverse=True, key=sort_second_index)

print(lst)

""""""
[course-site]: https://www.programmingexpert.io/index