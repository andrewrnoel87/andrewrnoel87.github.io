---
layout: default
title:  "Math, Random, Sorting, and Misc. Python Syntax"
date:   2023-10-03 10:23:00 -0400
categories: blog
---
Today I covered __Math__, __Sorting__, and __Misc. Python Syntax__ in Python from the [programmingexpert.io][course-site] course.

""""""

The standard library of a language are the libraries that the language comes with by default. In Python, this includes modules like os, math, threading and many more.

""""""

"""Math"""

""""""

import math

The math module is part of the Python standard library, and it has many nice functions that we may need. For instance, math.sin(x), math.cos(x), math.tan(x) and math.pi are available for the math module.

""""""

import random

The random module is part of the Python standard library, and provides many functions that can used to generate random numbers or make random choices. random.randint(start,stop), random.randrange(start, stop, step) and random.choice(iterable) are a few commonly used functions from the random module.

""""""

The following are math functions in Python that do not need to be imported.

abs(x) - returns the absolute value of the argument.

max(x) - returns its biggest item in an iterable object. If the iterable is a string, the function returns the character in the string with the highest ASCII value.

min(x) - returns its smallest item in an iterable object. Note that the min() function can take in any iterable—not just lists. For example, min((1, 2)), min(1, 2), and min("foo", "bar") are all fine usages of min(). When passing strings to min(), the strings are compared lexicographically, as they are when using the > or < operators.

sum(x) - returns the sum of a 'start' value (default: 0) plus an iterable of numbers. When the iterable is empty, return the start value. This function is intended specifically for use with numeric values and may reject non-numeric types.

round(number, ndigits=None) - Rounds a number to a given precision in decimal digits. The return value is an integer if ndigits is omitted or None.  Otherwise, the return value has the same type as the number.  ndigits may be negative. 

""""""

"""Sorting"""

""""""

sorted(iterable, /, *, key=None, reverse=False) - Returns a new list containing all items from the iterable in ascending order. A custom key function can be supplied to customize the sort order, and the reverse flag can be set to request the result in descending order.

.sort() - sorts and modifies the object in place. In Python, the .sort() method sorts a list in place (it mutates the list), and it takes two optional parameters: reverse (a boolean) and key (a function). When reverse is True, the method sorts the relevant list in descending order.

When sorted(tup) is called on a tuple it is returned as a new sorted list. tup.sort() will not work on a tuple because a tuple is immutable.

- Example One of Sorting by Key -

def sort_second_index(item):

    return item[1]

lst = [[1,-2], [3,-4], [5,-6], [-1,-2], [0,0]]

lst.sort(reverse=True, key=sort_second_index)

print(lst)

""""""

- Example Two of Sorting by Key -

Question - What does the following Python code output?

""""""

people = {"Tim": 21, "Joe": 18, "Sarah": 25, "Jennie": 26, "Bill": 34}

result = sorted(people, key=people.get)

print(result)

""""""

Answer - ['Joe', 'Tim', 'Sarah', 'Jennie', 'Bill']

""""""

Explanation - In Python, the sorted() function takes in an iterable object and returns a new list containing the object's elements in sorted order. It also takes in two optional parameters: reverse (a boolean) and key (a function).

By default, passing a dictionary to the sorted() function returns a list of the dictionary's keys sorted according to their actual value (i.e., the value "Tim" in the provided code). However, if the key argument is passed to sorted(), the function will sort the dictonary's keys by the result of each dictionary key passed to the passed key function (the key function must return a comparable object).

In the provided code, we use people.get as the key function. This means that the keys in the dictionary will be sorted based on their values, which are integers. Therefore, result will be equal to ["Joe", "Tim", "Sarah", "Jennie", "Bill"], and that will be printed by the program.

""""""

"""Misc. Python Syntax"""

""""""

Comprehensions are a way to initialize a data type/structure in one line of code.

- Comprehension Examples -

lst = [i * j for i in range(1,11) for j in range(5)]  # works with lists

s = {i * j for i in range(1,11) for j in range(5)}  # works with sets

dict = {i:j for i in range(1,11) for j in range(5)}  # works with dictionaries

*Tuple comprehensions produce generator objects. A work around to producing tuples is to do a list comprehension and convert it to a tuple.

lst = tuple([i * j for i in range(1,11) for j in range(5)])

""""""

Multiple Assignment is assigning one value to multiple variables or multiple variables to multiple values.

- Multiple Assignment Examples -

x = y = z = 2

print(x, y, z)  # output will be 2 2 2

x, y = 1, 2

print(x, y)  # output will be 1 2

""""""

Unpacking is taking an iterable object and unpacking it into individual values. To unpack, define a number of variables equal
to the number of items corresponding to their postion.

- Unpacking Example -

x, y, z = [1, 2, 3]

print(x, y, z)  # output will be 1 2 3

""""""

docstrings are multiline strings/comments that describe what a function does. They are typically found at the top of a function's code.

- docstring example -

def foo():

    """

    This is the foo function.

    """

    pass  # pass is a placeholder for future code.

""""""

help(object) function brings up the docstring.

- help(object) example -

help(foo)  # output will be: foo() This is the foo function.

""""""

[course-site]: https://www.programmingexpert.io/index