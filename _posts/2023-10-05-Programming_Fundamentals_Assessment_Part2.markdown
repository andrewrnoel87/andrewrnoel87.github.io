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

[course-site]: https://www.programmingexpert.io/index