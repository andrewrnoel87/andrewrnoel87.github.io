---
layout: default
title:  "Functions"
date:   2023-09-26 15:33:00 -0400
categories: blog
---
Today I covered Functions from the [programmingexpert.io][course-site] course.

""""""

Functions are a reusable block of code. Function names in Python cannot start with a number, can have no spaces, and no special characters other than underscore.

""""""

"""Function Exercise One"""

Write a function named add that takes in two parameters x and y, both expected to be numbers. The function should add the two numbers and return the result.

"""My Solution for One"""

def add(num1, num2):

    return num1 + num2

""""""

"""Function Exercise Two"""

Write the function find_all_odds(lst), which takes in a list of integers and returns a new list containing all of the odd numbers of the original list, in the order in which they appear. You can assume that lst will only contain integers.

"""My Solution for Two"""

def find_all_odds(lst):

    new_lst = []

    for num in lst:

        if (num % 2) != 0:

            new_lst.append(num)
    
    return new_lst

""""""

"""Function Exercise Three"""

Write the function string_lengths(strings), which takes in a list of strings and returns a new list containing the lengths of the strings, in their relevant order. You can assume that strings will only contain strings.

"""My Solution for Three"""

def string_lengths(strings):

    lengths = []

    for elem in strings:

        lengths.append(len(elem))
        
    return lengths

""""""

"""Function Exercise Four"""

[course-site]: https://www.programmingexpert.io/index