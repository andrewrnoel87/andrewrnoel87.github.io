---
layout: default
title:  "The Mighty 'For' loop"
date:   2023-09-15 14:03:00 -0400
categories: blog
---
Today I covered 'For' Loops from the [programmingexpert.io][course-site] course. 

""""""

Here is some code I wrote for an exercise.

""""""

string1 = "aabbcsdw"

string2 = "abbbcsdd"

for i, char in enumerate(string1):

    if string1[i] == string2[i]:

        print(char)

"""""""

lst = [45, 24, 22, 1, 45, 2, 12, 13, 16, 10, 0, -7]

for i, elem in enumerate(lst):

    if (elem % 2 == 0) and (i % 2 != 0):

        print(elem)

""""""

lst = [[2, 3, 4], [-2, -4, 0], [1, 2], [1, 1, 1, 5, 6], [0, 9, 8, 7]]

for elem in lst:

    sum = 0

    for inner_elem in elem:

        sum += inner_elem

    print(sum)

""""""

lst = [-2, 0, 4, 5, 1, 2]

for i in range(len(lst) - 1):

    print(lst[i] + lst[i + 1])

""""""
[course-site]: https://www.programmingexpert.io/index