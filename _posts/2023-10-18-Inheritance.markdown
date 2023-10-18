---
layout: default
title:  "Inheritance"
date:   2023-10-18 13:36:00 -0400
categories: blog
---

Today, I cover __Inheritance__ from the [programmingexpert.io][course-site] course.

""""""

# Key Terms

<u>Child Class<u>

When a class __A__ inherits from class __B__, we say that class __A__ is a _child class_ of __B__.

<u>Parent Class<u>

When a class __A__ inherits from class __B__, we say that class __B__ is a _parent class_ of __A__.

<u>Polymorphism<u>

__Polymorphism__ is a term originating from biology, where _poly_ means many and _morphism_ means forms (this is a simplification). In programming, polymorphism refers to the ability for an object to behave in differnet ways and exhibit different behaviour based on the context it's used in.

<u>Method Overriding<u>

Method __overriding__ is when a programmer re-defines a method on a class that was already defined in its parent class(es).

""""""

# Notes

- __Inheritance__ is important because one class can inherit the functionality of another class. Common functionality makes it easier to change and apply updates in the future.

- Child class, subclass and derived class are all synonymous for a class that inherits from another class.

- Parent class, superclass and base class are all synonymous for a class that is inherited from.

""""""

# Inheritance Example

""""""

class Animal:

    def __init__(self, age, weight, height):
        self.age = age
        self.weight = weight
        self.height = height

class Mammal(Animal):

    def __init__(self, age, weight, height, sex):
        super().__init__(age, weight, height)
        self.sex = sex

class Reptile(Animal):

    def __init__(self, age, weight, height, leg_count):
        super().__init__(age, weight, height)
        self.leg_count = leg_count

class Monkey(Mammal):

    fingers = 5
    def __init__(self, age, weight, height, sex, color):
        super().__init__(age, weight, height, sex)
        self.color = color

class Lizard(Reptile):

    tail = True
    def __init__(self, age, weight, height, leg_count, color):
        super().__init__(age, weight, height, leg_count)
        self.color = color

""""""

[course-site]: https://www.programmingexpert.io/index