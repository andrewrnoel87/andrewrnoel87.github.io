---
layout: default
title:  "The Whole Set"
date:   2023-09-20 13:46:00 -0400
categories: blog
---
Today I covered Sets from the [programmingexpert.io][course-site] course. 

""""""

Sets.

"""The Set Exercise"""

Write a program that continually asks the user to enter characters until the user enters a previously entered character or more than one character ar a time. After, the program should print the number of unique characters that were entered. Use a set to accomplish this.

"""My Solution"""

character_set = set()

while True:

    input_character = input("Enter a character: ")

    if (input_character in character_set) or len(input_character) > 1:

        break

    character_set.update(input_character)

num_characters = len(character_set)

print(f"Number of unique characters entered: {num_characters}")

""""""

[course-site]: https://www.programmingexpert.io/index