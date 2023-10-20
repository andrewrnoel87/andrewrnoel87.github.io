---
layout: default
title:  "Operator Overloading"
date:   2023-10-20 13:26:00 -0400
categories: blog
---

Today, I cover __Operator Overloading__ from the [programmingexpert.io][course-site] course. Operator Overloading is our ability to implement custom operations on our own classes.

""""""

# Key Terms

<u>Dunder Method<u>

Dunder comes from double underscore. Dunder methods are also know as _magic methods_. Dunder methods are methods that are prefixed and suffixed by two underscores. The most important thing to know is the \__init__ dunder method, which is sometimes called the _constructor_ of the class, defines how a new instance is initialized after being created.

Implementing those methods will sometimes change how certain operators will behave (like + with \__add__ and == with \__eq__). Other examples include \__len__, \__str__, \__repr__ and many more.

""""""

# Notes

- Dunder methods are just like other methods except they can be triggered in unique ways. For example, the \__init__ dunder method will automatically be called when instantiating a new object.

- In Python, when calling the str() function on an instance of a class the \__str__ method will be called. The \__str__ is designed to return the string representation of an object.

- In Python, when calling the print() function on an instance of a class the \__str__ method will be called. This is because behind the scenes the print() function explicitly calls the str() function on all of it's arguments before printing them.

- In Python, the \__repr__ method is used for debugging and displaying meaningful information about the object. It is not designed to provide a string representation that is useful for printing.

""""""

# Core Dunder Methods

\__add__(self, other)       # add                              # __+__

\__sub__(self, other)       # subract                          # __-__

\__mul__(self, other)       # multiply                         # __*__

\__truediv__(self, other)   # division                         # __/__

\__floordiv__(self, other)  # integer division                 # __//__

\__len__(self)              # length                           # __len()__

\__eq__(self, other)        # equivalent to                    # __==__

\__ne__(self, other)        # not equal to                     # __!=__

\__gt__(self, other)        # greater than                     # __>__

\__ge__(self, other)        # greater than or equal to         # __>=__

\__lt__(self, other)        # less than                        # __<__

\__le__(self, other)        #less than or equal to             # __<=__

\__str__(self)              # string method                    # __str()__

\__repr__(self)             # internal representation method   # __repr()__

""""""

# Operator Overloading Example

""""""

class Vector:

    def __init__(self, a, b):
        self.a = a
        self.b = b

    def __eq__(self, vector):
        if self.a == vector.a and self.b == vector.b:
            return True
        return False

    def __repr__(self):
        return f"Vector({self.a}, {self.b})"

    def __add__(self, vector): 
        return Vector(self.a + vector.a, self.b + vector.b) 

    def __sub__(self, vector):
        return Vector(self.a - vector.a, self.b - vector.b)

    def __mul__(self, vector):
        a_operand = self.a * vector.a
        b_operand = self.b * vector.b
        return a_operand + b_operand

""""""

Because Vector() has overloaded the dunder methods with its own implementation of them, the following code is possible.

""""""



""""""

[course-site]: https://www.programmingexpert.io/index