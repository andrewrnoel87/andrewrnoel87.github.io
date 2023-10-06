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

    frequencies_copy = frequencies.copy()  # create copy of frequencies so we do not modify it

    string1_dict = string_to_dict(string1)  # create dictionaries for comparing frequencies

    string2_dict = string_to_dict(string2)

    string1_and_string2_dict = string_to_dict(string1 + string2) 

    frequencies_contains_string1 = dict1_contains_dict2(frequencies_copy, string1_dict)  # assign bool values based on a comparison of the frequencies

    frequencies_contains_string2 = dict1_contains_dict2(frequencies_copy, string2_dict)

    frequencies_contains_string1_and_string2 = dict1_contains_dict2(frequencies_copy, string1_and_string2_dict)
    
    if frequencies_contains_string1_and_string2:  # return a value based on the relationship between the strings and the original provided dictionary

        return 2
    
    if frequencies_contains_string1 or frequencies_contains_string2:

        return 1
    
    else:

        return 0

def string_to_dict(string):  # takes in a string and returns a dict with {'char': frequency} values made from the string

    string_dict = {}

    for i in string:

        string_dict[i] = string_dict.get(i, 0) + 1

    return string_dict

def dict1_contains_dict2(dict1, dict2):  #  returns False if the char frequencies in dict1 < frequencies in dict2

    for key in dict2:

        if dict1.get(key, 0) < dict2[key]:

            return False

    return True

""""""

It is so satisfying everytime the code finally works as intended.

""""""

- Provided Solution for Exercise Six -

""""""

Copyright © 2022 AlgoExpert LLC. All rights reserved.

def create_strings_from_characters(frequencies, string1, string2):

    can_create_string1 = can_create_string_from_frequencies(

        frequencies, string1)

    can_create_string2 = can_create_string_from_frequencies(

        frequencies, string2)

    if (not can_create_string1) or (not can_create_string2):

        if can_create_string1 or can_create_string2:

            return 1

        return 0

    for character in string1 + string2:

        if character not in frequencies or frequencies[character] == 0:

            return 1

        frequencies[character] -= 1

    return 2


def can_create_string_from_frequencies(frequencies, string):

    for character in set(string):

        if string.count(character) > frequencies.get(character, 0):
        
            return False

    return True

""""""

[course-site]: https://www.programmingexpert.io/index