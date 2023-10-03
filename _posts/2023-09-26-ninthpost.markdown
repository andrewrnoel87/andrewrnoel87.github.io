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

- My Solution for One -

def add(num1, num2):

    return num1 + num2

""""""

"""Function Exercise Two"""

Write the function find_all_odds(lst), which takes in a list of integers and returns a new list containing all of the odd numbers of the original list, in the order in which they appear. You can assume that lst will only contain integers.

- My Solution for Two -

def find_all_odds(lst):

    new_lst = []

    for num in lst:

        if (num % 2) != 0:

            new_lst.append(num)
    
    return new_lst

""""""

"""Function Exercise Three"""

Write the function string_lengths(strings), which takes in a list of strings and returns a new list containing the lengths of the strings, in their relevant order. You can assume that strings will only contain strings.

- My Solution for Three -

def string_lengths(strings):

    lengths = []

    for elem in strings:

        lengths.append(len(elem))
        
    return lengths

""""""

"""Function Exercise Four"""

Write a function named compare_lists that accepts two optional parameters, lst1 and lst2. The function should return the number of unique common elements between the two lists. If either of the lists is not passed as a parameter, it should be treated as an empty list. You can assume that the input lists will only contain integers.

- My Solution for Four -

def compare_lists(lst1=[], lst2=[]):

    common = set()

    for elem in lst1:

        if elem in lst2:

            common.add(elem)

    return len(common)

""""""

Based on the sample solution below, I did the intersection of two sets the hard way.

 - Sample Solution for Four -

def compare_lists(lst1=[], lst2=[]):

    lst1_set = set(lst1)

    lst2_set = set(lst2)

    set_intersection = lst1_set.intersection(lst2_set)

    return len(set_intersection)

""""""

"""Function Exercise Five"""

Write the function trim_list(lst, elements_to_trim), which takes in a list and returns a new version of the input list where the last elements_to_trim elements have been removed. You can assume that elements_to_trim will always be a positive integer that's smaller than the length of lst.

 - My Solution for Five -

def trim_list(lst, elements_to_trim):

    new_lst = []

    new_range = len(lst) - elements_to_trim

    for i in range(new_range):

        new_lst.append(lst[i])

    return new_lst

""""""

"""Function Exercise Six"""

Write the function running_sums(numbers), which takes in a list of integers and returns a new list of the same length as numbers, where the element at index i in the new list is equal to numbers[0] + numbers[1] + ... + numbers[i-1] + numbers[i]. You can assume that numbers will only contain integers.

- My Solution for Six -

def running_sums(numbers):

    new_list = []

    current_sum = 0

    for num in numbers:

        current_sum += num

        new_list.append(current_sum)

    return new_list

""""""

[course-site]: https://www.programmingexpert.io/index