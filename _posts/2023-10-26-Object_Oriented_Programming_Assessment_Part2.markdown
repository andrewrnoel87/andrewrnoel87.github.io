---
layout: default
title:  "Object-Oriented Programming Assessment Part 2"
date:   2023-10-26 11:06:00 -0400
categories: blog
---
Today, I covered the __Object-Oriented Programming Assessment__ from the [programmingexpert.io][course-site] course.

""""""

# """Exercise Two"""

""""""

__Student Class__

Write a Student class, as defined below, that keeps track of all created students.

The class should implement the following methods, class variables and properties:

- An instance attribute called _name_.

- A property called _grade_ that returns the grade of that student. Trying to set the grade should raise a ValueError if the new grade is not a number between 0 and 100.

- A static method called __calculate_average_grade(students)__ that accepts a list of _Student_ objects and returns the average grade for those students. If there are no students in the list, it should return -1.

- A class variable called __all_students__ that stores all of the student objects that have been created in a list.

- A class method named __get_average_grade()__ which returns the average grade of all created students.

- A class method named __get_best_student()__ which returns the student object with the best grade out of all the currently created students. If there are no students created this method should return __None__. You may assume there will always be one student with the best grade, except in the case where there are no students created.

See below for an example of the behavior of the Student class:

    >>> Student.get_average_grade()
    -1
    >>> student1 = Student("Antoine", 75)
    >>> student1.name
    "Antoine"
    >>> student1.grade
    75
    >>> student1.grade = 150
    Traceback (most recent call last):
        File "<stdin>", line 1, in <module>
    ValueError: New grade not in the accepted range of [0-100].
    >>> student1 == Student.get_best_student()
    True

""""""

# My Solution for Exercise Two -

""""""

class Student:

    all_students = []

    def __init__(self, name, grade):
        self.name = name
        self._grade = grade
        Student.all_students.append(self)

    @property
    def grade(self):
        return self._grade

    @grade.setter
    def grade(self, new_grade):
        if new_grade < 0 or new_grade > 100:
            raise ValueError("New grade not in the accepted range of [0-100].")
        self._grade = new_grade

    @classmethod
    def get_best_student(cls):
        best_student = None
        for student in cls.all_students: 
            if best_student == None or student.grade > best_student.grade:
                best_student = student
        return best_student

    @classmethod
    def get_average_grade(cls):
        return cls.calculate_average_grade(cls.all_students)

    @staticmethod
    def calculate_average_grade(students):
        total_num_students = len(students)
        if total_num_students == 0:
            return -1
            
        grade_sum = 0
        for student in students:  # add up the student grades
            grade_sum += student.grade

        return grade_sum / total_num_students

""""""
""""""

[course-site]: https://www.programmingexpert.io/index