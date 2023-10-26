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

<u>Student Class<u>

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

# """Exercise Three"""

""""""

<u>Geometry Inheritance<u>

Create 4 classes: __Polygon__, __Triangle__, __Rectangle__ and __Square__. The _Triangle_ and _Rectangle_ class should be subclasses of _Polygon_, and _Square_ should be a subclass of _Rectangle_.

The __Polygon__ class should raise a __NotImplementedError__ when the __get_area()__ and __get_sides()__ methods are called. However, it should correctly return the perimeter of the polygon when __get_perimeter()__ is called. Treat __Polygon__ class as an abstract class.

The __Triangle__ class should have a constructor that takes in 3 arguments, which will be the lengths of the 3 sides of the triangle. You may assumethe sides passed to the constructor will always form a valid triangle.

The __Rectangle__ class should have a constructor that takes in 2 arguments, which will be the __width__ and __height__ of the __Rectangle__.

The __Square__ class should have a constructor that takes in 1 argument, which will be the length of each side of the __Square__.

The __Triangle__ and __Rectangle__ classes should both implement the following methods: 

- __get_sides()__: This method returns a list containing the lengths of the sides of the shape.

- __get_area()__: This method returns the area of the polygon.

The __Square__ class should only have an implementation for its constructor, and rely on the __Rectangle__ superclass for the implementations of __get_sides()__ and __get_area()__.

Note: To calculate the area of a triangle given three lengths (x, y and z) you can use the following formula. First calculate the semi perimeter s using: s = (x + y + z) / 2. Then calculate the area A using: A = math.sqrt(s * (s - x) * (s - y) * (s - z)).

See below for an example of how these classes should behave:

    >>> triangle = Triangle(2, 5, 6)
    >>> triangle.get_area()
    4.68
    >>> Square(4).get_perimeter()
    16
    >>> Rectangle(3, 5).get_sides()
    [3, 5, 3, 5]
    
""""""

# My Solution for Exercise Three -

""""""

import math


class Polygon:  # Treat as an abstract class

    def get_area(self):
        raise NotImplementedError
    
    def get_sides(self):
        raise NotImplementedError

    def get_perimeter(self):
        return sum(self.get_sides())

class Triangle(Polygon):

    def __init__(self, side1, side2, side3):
        self.side1 = side1
        self.side2 = side2
        self.side3 = side3

    def get_sides(self):
        return [self.side1, self.side2, self.side3]
    
    def get_area(self):
        return get_triangle_area(self.side1, self.side2, self.side3)


class Rectangle(Polygon):

    def __init__(self, width, height):
        self.width = width
        self.height = height

    def get_sides(self):
        return [self.width, self.height, self.width, self.height]

    def get_area(self):
        return get_rectangle_area(self.width, self.height)

class Square(Rectangle):

    def __init__(self, side):
        super().__init__(side, side)

def get_triangle_area(side1, side2, side3):  # Static Method

    semi_perimeter = (side1 + side2 + side3) / 2
    return math.sqrt(
        semi_perimeter *
        (semi_perimeter - side1) *
        (semi_perimeter - side2) *
        (semi_perimeter - side3)
    )

def get_rectangle_area(width, height):  # Static Method

    return width * height

""""""

The following is the instructor's implementation of the Triangle class:

    class Triangle(Polygon):
        def __init__(self, side1, side2, side3):
            self.sides = [side1, side2, side3]

        def get_sides(self):
            return self.sides

        def get_area(self):
            side1, side2, side3 = self.sides
            return get_triangle_area(side1, side2, side3)

I wanted to note the way the instructor assigned the variables.

""""""

[course-site]: https://www.programmingexpert.io/index