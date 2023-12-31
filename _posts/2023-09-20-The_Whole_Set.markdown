---
layout: default
title:  "The Whole Set"
date:   2023-09-20 13:46:00 -0400
categories: blog
---
Today I covered __Sets__ from the [programmingexpert.io][course-site] course. 

""""""

A Set is a collection that holds unique individual elements (not key-value pairs) in an unordered fashion. The set() function is used to create an empty set. Common methods used with Sets are .add(), .remove(), .clear(), .union(), .intersection(), .difference(), .symmetric_difference(), .update(), .difference_update(), .symmetric_difference_update(), .issubset(), and .issuperset(). The 'in' operator and the len() function are commonly used as well.

It is best to use a Set only if you care whether an element exists or does not exist in a collection. If information needs to be associated with the element, use a dictionary.

"""Shortcuts"""

z = x.union(y)  or  z = x \| y

z = x.intersection(y)   or  z = x & y

z = x.difference(y) or  z = x - y

z = x.symmetric_difference(y)   or  z = y ^ x

x.issubset(y)   or  x <= y

x.issuperset(y) or  x >= y

x < y       # is x a proper subset of y

x > y       # is x a proper superset of y

"""The Set Exercise"""

Write a program that continually asks the user to enter characters until the user enters a previously entered character or more than one character ar a time. After, the program should print the number of unique characters that were entered. Use a set to accomplish this.

- My Solution -

character_set = set()

while True:

    input_character = input("Enter a character: ")

    if (input_character in character_set) or len(input_character) > 1:

        break

    character_set.add(input_character)

num_characters = len(character_set)

print(f"Number of unique characters entered: {num_characters}")

""""""

[course-site]: https://www.programmingexpert.io/index