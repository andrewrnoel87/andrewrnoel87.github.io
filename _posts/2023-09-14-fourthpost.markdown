---
layout: default
title:  "Fun with Strings"
date:   2023-09-14 15:15:00 -0400
categories: blog
---
Today I covered Strings from the [programmingexpert.io][course-site] course. 

Here is some code I wrote for an exercise. It uses various methods on strings and uses
an f string.

""""""
num = input("Enter an integer: ")
if num.isdigit():
    name = input("What is your name? ")
    print(f"Hello, {name.upper()}")
else:
    print(num.capitalize())

""""""
Another exercise. The prompt was designed to get us to use the 'in' operator.

""""""
word_one = input("Enter a word: ")

word_two = input("Enter another word: ")

if word_one in word_two:
    print("The first word is contained in the second one")
else:
    print("The first word isn't contained in the second one")


[course-site]: https://www.programmingexpert.io/index