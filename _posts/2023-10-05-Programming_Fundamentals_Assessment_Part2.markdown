---
layout: default
title:  "Programming Fundamentals Assessment Part 2"
date:   2023-10-05 10:42:00 -0400
categories: blog
---
Today, I covered more exercises from the Programming Fundamentals Assessment from the [programmingexpert.io][course-site] course.

""""""

# """Exercise Three"""

""""""

Sort Employees

Write a function that accepts a list of lists that contain the name, age and salary of specific employees and also accepts a string representing the key to sort employees by. The function should return a new list that contains the lists representing each employee sorted in ascending order by the given key.

The string parameter named sort_by will always be equal to one of the following values: "name", "age" or "salary".

Sample Input:

employees = [["John", 33, 65000], ["Sarah", 24, 75000], ["Josie", 29, 100000], ["Jason", 26, 55000], ["Connor", 25, 110000]]

sort_by = "age"

Sample Output:

[["Sarah", 24, 75000], ["Connor", 25, 110000], ["Jason", 26, 55000], ["Josie", 29, 100000], ["John", 33, 65000]]

""""""

- My Solution for Three -

""""""

def sort_employees(employees, sort_by):

    def sort_by_index_zero(iterable):

        return iterable[0]

    def sort_by_index_one(iterable):

        return iterable[1]

    def sort_by_index_two(iterable):

        return iterable[2]
    
    if sort_by == "name":

        return sorted(employees, key=sort_by_index_zero)
    
    if sort_by == "age":

        return sorted(employees, key=sort_by_index_one)
    
    if sort_by == "salary":

        return sorted(employees, key=sort_by_index_two)

""""""

""""""

- Provided Solution One for Exercise Three -

""""""

Copyright © 2022 AlgoExpert LLC. All rights reserved.

def sort_employees(employees, sort_by):

    sort_indices = ["name", "age", "salary"]

    sort_index = sort_indices.index(sort_by)

    sorted_employees = []

    # Copy the employees list so we don't modify it

    employees_copy = employees[:]

    while len(employees_copy) > 0:

        smallest_employee_index = 0

        for i, employee in enumerate(employees_copy):

            current_smallest_value = employees_copy[smallest_employee_index][sort_index]

            if employee[sort_index] < current_smallest_value:

                smallest_employee_index = i

        # After looking through all remaining employees we will have found the employee

        # with the smallest sort_by value so we add it to the sorted list

        next_sorted_employee = employees_copy[smallest_employee_index]

        sorted_employees.append(next_sorted_employee)

        employees_copy.pop(smallest_employee_index)

    return sorted_employees

""""""

- Provided Solution Two for Exercise Three -

""""""

Copyright © 2022 AlgoExpert LLC. All rights reserved.

def sort_employees(employees, sort_by):

    sort_indices = ["name", "age", "salary"]

    sort_index = sort_indices.index(sort_by)

    sorted_employees = sorted(employees, key=lambda x: x[sort_index])

    return sorted_employees


""""""

""""""

# """Exercise Four"""

""""""

Longest Unique Words

Write a function that accepts a list of strings that represent words and a positive integer n, representing the number of words to return. Your function should return a new list containing the n longest unique words from the input list. Words are unique if they only appear one time in the input list.

There will always be exactly n words to return and you may return the words in any order.

Note: all strings in the input list will not contain any special characters or spaces.

Sample Input:

words = ['Longer', 'Whatever', 'Longer', 'Ball', 'Rock', 'Rocky', 'Rocky']

n = 3

Sample Output:

['Whatever', 'Ball', 'Rock']

""""""

- My Solution for Four -

""""""
def get_n_longest_unique_words(words, n):

    frequency_dict = {}

    list_of_unique_words = []

    for word in words:  # make a dictionary that tracks the frequency of each word.

        frequency_dict[word] = frequency_dict.get(word, 0) + 1

    for key in frequency_dict:  # make a list of words with frequency 1.

        if frequency_dict.get(key) == 1:

            list_of_unique_words.append(key)

    list_of_unique_words.sort(key=len, reverse=True)  # sort the list by word length in descending order.

    n_words = list_of_unique_words[0:n]  # return a list of the first n words.

    return n_words

""""""

""""""

- Provided Solution One for Exercise Four -

""""""

Copyright © 2022 AlgoExpert LLC. All rights reserved.

def get_n_longest_unique_words(words, n):

    unique_words = get_unique_words(words)

    longest_words = []

    while len(longest_words) < n:

        current_longest = ""

        for word in unique_words:

            if len(word) > len(current_longest):

                current_longest = word

        unique_words.remove(current_longest)

        longest_words.append(current_longest)

    return longest_words


def get_unique_words(words):

    unique_words = []

    for word in words:

        if words.count(word) == 1:

            unique_words.append(word)

    return unique_words

""""""

- Provided Solution Two for Exercise Three -

""""""

Copyright © 2022 AlgoExpert LLC. All rights reserved.

def get_n_longest_unique_words(words, n):

    unique_words = get_unique_words(words)

    sorted_words = sorted(unique_words, key=len, reverse=True)

    return sorted_words[:n]


def get_unique_words(words):

    unique_words = []

    for word in words:

        if words.count(word) == 1:
        
            unique_words.append(word)

    return unique_words

""""""

[course-site]: https://www.programmingexpert.io/index