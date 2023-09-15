---
layout: default
title:  "The Mighty 'For' loop"
date:   2023-09-15 14:03:00 -0400
categories: blog
---
Today I covered 'For' Loops from the [programmingexpert.io][course-site] course. 

"""Exercise 1"""

Here is some code I wrote for an exercise. The goal of the exercise was to use a single for loop to iterate through the two strings, and print all of their matching characters(i.e., the characters that are the same index and that are equal to each other), each on a separate line.

""""""

string1 = "aabbcsdw"

string2 = "abbbcsdd"

for i, char in enumerate(string1):

    if string1[i] == string2[i]:

        print(char)

"""Exercise 2"""

Use a single for loop to iterate through the provided list, and print the elements that are both divisible by 2 and located at an odd index, each on a separate line.

""""""

lst = [45, 24, 22, 1, 45, 2, 12, 13, 16, 10, 0, -7]

for i, elem in enumerate(lst):

    if (elem % 2 == 0) and (i % 2 != 0):

        print(elem)

"""Exercise 3"""

Use nested for loops to iterate through the provided list, which contains other lists, and print the respective sums of the inner lists, each on a separate line.

""""""

lst = [[2, 3, 4], [-2, -4, 0], [1, 2], [1, 1, 1, 5, 6], [0, 9, 8, 7]]

for elem in lst:

    sum = 0

    for inner_elem in elem:

        sum += inner_elem

    print(sum)

"""Exercise 4"""

Use a single for loop to iterate through the provided list of numbers, and for each number, print the sum of the number and the one directly to its right. Since the last number in the list has no number to the right of it, skip it.

""""""

lst = [-2, 0, 4, 5, 1, 2]

for i in range(len(lst) - 1):

    print(lst[i] + lst[i + 1])

""""""

[course-site]: https://www.programmingexpert.io/index