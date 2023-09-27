---
layout: default
title:  "Mutability"
date:   2023-09-27 15:43:00 -0400
categories: blog
---
Today I covered Mutability in Python from the [programmingexpert.io][course-site] course.

""""""

Objects/data types in Python are mutable or immutable.

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


""""""

[course-site]: https://www.programmingexpert.io/index