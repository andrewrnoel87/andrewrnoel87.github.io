---
layout: default
title:  "Programming Fundamentals Assessment Part 3"
date:   2023-10-06 10:42:00 -0400
categories: blog
---
Today, I cover the last exercise from the Programming Fundamentals Assessment from the [programmingexpert.io][course-site] course.

""""""

# """Exercise Six"""

""""""

Create Strings From Characters

Write a function that accepts a dictionary called frequencies and two strings named string1 and string2. The frequencies dictionary contains character keys and integer values, the value associated with each character represents its frequency. The function should return 0, 1 or 2 according to the cases below.

- The function should return 2 if the frequency of characters in the dictionary is sufficient to create both string1 and string2 without reusing any characters.

- The function should return 1 if the frequency of characters in the dictionary is sufficient to create either string1 or string2 without reusing any characters.

- The function should return 0 if the frequency of characters in the dictionary is not sufficient to create either string1 or string2 without reusing any characters.

Sample Input:

frequencies = {"h": 2, "e": 1, "l": 2, "r": 4, "a": 3, "o": 2, "d": 1, "w": 1}

string1 = "hello"

string2 = "world"

Sample Output:

1  # The string "world" and "hello" can be created but they cannot both be created without reusing any characters. This is because there is not enough "l"'s.

""""""

- My Solution for Exercise Six -

""""""

def create_strings_from_characters(frequencies, string1, string2):

    # Write your code here.

    pass #

""""""

""""""

- Provided Solution for Exercise Six -

""""""

def create_strings_from_characters(frequencies, string1, string2):

    # Write your code here.

    pass

""""""

""""""

[course-site]: https://www.programmingexpert.io/index