---
layout: default
title:  "Static Methods"
date:   2023-10-17 15:23:00 -0400
categories: blog
---

Today, I cover __Static Methods__ from the [programmingexpert.io][course-site] course.

""""""

# Key Terms

<ins>Static Method<ins>

A __static__ method is defined within a class but should not reference anything relevant to that class specifically, except for other static methods. For the most part, static methods should only be used for __pure__ functions, which do not use temporary variables outside of their own scope and exclusively transform a set of inputs into some outputs. For instance, a method that converts a distance from kilometers to miles should most likely be __static__. Static methods are denoted using the __@staticmethod__ decorator.

""""""

# Notes

- A static method is a method that sits inside a class but does not have access to the __cls__ keyword or the __self__ keyword. It does not act on the class or an instance of the class. It is a function that belongs to the class.

- Static methods are used to better organize code and keep related code together.

- Static methods tend to be utility functions in essence.

- __Static attributes__ are the same as class attributes in Python.

- Static methods cannot modify class or instance attributes while instance methods can modify both class and instance attributes.

- Static methods are denoted with the @staticmethod decorator and take no mandatory parameters. You can think of them as utility functions that are defined inside of a class. They have no access to instance attributes, class attributes or methods.

- Static methods should be declared using the @staticmethod decorator.

- Static methods can be thought of as functions belonging to a class. They do not act on objects.

- Static methods are only used when they do not need to access instance or class attributes.

- Static methods can be thought of as utility functions that are defined inside of a class. They do not have any mandatory parameters and cannot access instance attributes, class attributes or methods. Static methods can be called from an instance or by using the class name directly.

""""""

# Instance vs Static vs Class Methods Example

""""""

class Student:

    grade_bump = 2.0

    def __init__(self, name, grades=[]):

        self.name = name

        self.grades = grades

    def average(self):  # an Instance Method

        return sum(self.grades) / len(self.grades)

    @classmethod  # a Class Method

    def average_from_grades_plus_bump(cls, grades):

        average = cls.average_from_grades(grades)

        return min(average + cls.grade_bump, 100)

    @staticmethod  # a Static Method

    def average_from_grades(grades):

        return sum(grades) / len(grades)

""""""

[course-site]: https://www.programmingexpert.io/index