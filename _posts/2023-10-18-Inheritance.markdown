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

__Polymorphism__ is a term originating from biology, where _poly_ means many and _morphism_ means forms (this is a simplification). In programming, polymorphism refers to the ability for an object to behave in differnet ways and exhibit different behaviour based on the context it's used in. __Polymorphism__ allows us to treat our objects differently and have different behaviour based on the situation or context we use them in.

<u>Method Overriding<u>

Method __overriding__ is when a programmer re-defines a method on a class that was already defined in its parent class(es).

""""""

# Notes

- __Inheritance__ is important because one class can inherit the functionality of another class. Common functionality makes it easier to change and apply updates in the future.

- Child class, subclass and derived class are all synonymous for a class that inherits from another class.

- Parent class, superclass and base class are all synonymous for a class that is inherited from.

- __super().__ gives access to the parent class.

- When overriding a constructor (the \__init__), you need to manually call the parent constructor, because the parent constructor could be doing things you do not know about. If you do not call the parent \__init__ the methods/attributes in the parent class might not function properly. 

- __isinstance(obj, class)__ returns whether an object is an instance of a class or of a subclass thereof. This helps track inheritance.

- The __IS A__ rule in Python is theoretical. It is a way to check inheritance relationships. For example, it states that if _owner_ inherits from _person_, then _owner_ __is a__ a _person_. If _owner_ is __not__ a _person_ then the class Owner(Person) is an incorrect inheritance. The __IS A__ rule helps decide inheritance.

- Python uses a Method Resolution Order or MRO to make __Multiple Inheritance__ possible. This gives a way to know which superclass to look in when using multiple inheritance. Python's MRO tells the compiler to look in the main class, then look in the first listed superclass, then the second listed superclass, and so on for the constructor, the method, or other attributes it is looking for. Example below.

- Duck Typing is the philosophy that, in python, if something acts like a duck, walks like a duck, quacks like a duck, it must be a duck. Which leads code to working or blowing up at runtime. This keeps thing from getting held up at the complier. Example below.

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
        super().__init__(age, weight, height)  # calling the constructor of the superclass
        self.sex = sex

class Reptile(Animal):

    def __init__(self, age, weight, height, leg_count):
        super().__init__(age, weight, height)  # the self parameter is automatically passed to the constructor
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

# Multiple Inheritance Example

""""""

class A:

    def __init__(self):
        print("A")

class B:

    def __init__(self):
        print("B")

class C(A, B):  # A and B are parents to C; MRO checks C, does not find anything, so it checks A, if nothing was in A, it would move unto B.

    pass

\>>> c = C()  # this outputs... A

""""""

# Duck Typing Example

""""""

class Duck:

    def swim(self):
        print('Swimming duck')

    def fly(self):
        print('Flying duck')

class Whale:

    def swim(self):
        print('Swimming whale')

<u>Input:<u>

\>>> animals = [Duck(), Duck(), Whale()]

\>>> for animal in animals:

        animal.swim()

        animal.fly()  #  Runs until it cannot. Does not get stopped by compiler.

<u>Output:<u>

Swimming duck

Flying duck

Swimming whale

AttributeError: 'Whale object has no attribute 'Fly'

""""""

[course-site]: https://www.programmingexpert.io/index