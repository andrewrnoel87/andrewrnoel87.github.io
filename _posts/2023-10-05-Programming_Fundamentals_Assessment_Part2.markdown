---
layout: default
title:  "Programming Fundamentals Assessment Part 2"
date:   2023-10-05 10:42:00 -0400
categories: blog
---
Today, I covered more exercises from the Programming Fundamentals Assessment from the [programmingexpert.io][course-site] course.

""""""

"""Exercise Three"""

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

[course-site]: https://www.programmingexpert.io/index