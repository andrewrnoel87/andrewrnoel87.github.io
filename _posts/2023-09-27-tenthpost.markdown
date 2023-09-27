---
layout: default
title:  "Mutability"
date:   2023-09-27 15:43:00 -0400
categories: blog
---
Today I covered Mutability in Python from the [programmingexpert.io][course-site] course.

""""""

Objects/data types in Python are mutable or immutable. The "is" keyword will return True if variable references are pointing to the same object in the memory. Which is different than checking for equivalency. The id() function actually returns the memory address location of the object. We can modify mutable objects in place. Usually with the help of a funtion. We can copy a mutable object so as to not change the original. We usually make shallow copies of mutable objects, but deep copies are possible. Mutable objects can store immutable objects and immutable objects can store mutable objects.

""""""

In Python, an immutable object is one that cannot be modified once created. The following are examples of immutable data types:

int

float

str

bool

tuple

In Python, a mutable object is one that can modified once created. The following are examples of mutable data types:

list

set

dict

"""Mutability Exercise One"""

Write a function named replace that takes in three parameters: lst (a list of strings), target (a string), and swap_value (another string). The function should replace all instances of target in lst with swap_value, and it shouldn't return anything; in other words, your function should mutate the input list.

"""My Solution for One"""

def replace(lst, target, swap_value):

    for index in range(len(lst)):

        element = lst[index]

        if element == target:

            lst[index] = swap_value

""""""

[course-site]: https://www.programmingexpert.io/index