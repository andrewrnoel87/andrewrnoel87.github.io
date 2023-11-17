---
layout: default
title:  "Slice and Dictionary"
date:   2023-09-18 13:03:00 -0400
categories: blog
---
Today I covered __Slices__, and __Dictionaries__ from the [programmingexpert.io][course-site] course. 

""""""

# Slice Notes

- Slices provide a new subset of a collection(i.e., list, string, tuple, etc.). Slices use the following format... 
__collection[start:stop:step]__. 

- __Negative indexing__ can be used and the stop point is not included. 

- __[:]__ will make a _copy_ of the collection.

- __[::-1]__ is a shortcut for _reversing_ the collection.

""""""

# Slice Exercise

""""""

Modify the w, x, y, and z variables such that the program outputs [8, 6, 4].

Solution:

    w = 2  # <- Changed this to 2
    x = 2 # <- Changed this to 2
    y = 7  # <- Changed this to 7
    z = -1  # <- Changed this to -1

    lst = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
    first_slice = lst[::z]  # first reverse the list
    second_slice = first_slice[:y]  # pick a stop point that cuts off the elements smaller than 4
    third_slice = second_slice[x:]  # pick a start point that cuts off the elements greater than 8
    last_slice = third_slice[::w]  # pick every other element in the list

    print(last_slice)

""""""

# Dictionary Notes

- A __Dictionary__ is an unordered collection of __key:value__ pairs. The key is immutable. When concerned with presence or frequency of items in a collection but do not care about the order, use a dictionary due to its speed benefits. 

- Common methods used with dictionaries are __.values()__, __.keys()__, __.items()__ and __.get()__. The 'in' operator and the len() function are commonly used as well.

- __.get(key, default_value)__ gets the the value of the key and if the key doesn't exist, it creates it and sets it value to default_value.

""""""

# Dictionary Exercise

""""""

Write a program that asks the user to enter a string and prints the string's characters and their frequencies in any order and in the following format: key: frequency.

My Solution: 

    counts = {}  # Initialize the dictionary
    user_input = input("Enter a string: ")

    for char in user_input:
        counts[char] = counts.get(char, 0) + 1  # Add keys and update their count values

    for key in counts:
        print(f"{key}: {counts[key]}")

""""""

Alternate Solution Provided:

    string = input("Enter a string: ")
    character_frequencies = {}

    for character in string:
        if character not in character_frequencies:
            character_frequencies[character] = 0

        character_frequencies[character] += 1

    for key in character_frequencies:
        frequency = character_frequencies[key]
        print(f"{key}: {frequency}")

This solution does not use the .get() method.

""""""

[course-site]: https://www.programmingexpert.io/index