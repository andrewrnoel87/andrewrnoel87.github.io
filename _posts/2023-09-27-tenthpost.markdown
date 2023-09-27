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

"""Function Exercise One"""

Question

"""My Solution for One"""

def replace(lst, target, swap_value):

    for index in range(len(lst)):

        element = lst[index]

        if element == target:
        
            lst[index] = swap_value

""""""


""""""

[course-site]: https://www.programmingexpert.io/index