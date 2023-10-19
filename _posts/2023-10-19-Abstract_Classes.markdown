---
layout: default
title:  "Abstract Classes"
date:   2023-10-19 12:24:00 -0400
categories: blog
---

Today, I cover __Abstract Classes__ from the [programmingexpert.io][course-site] course.

""""""

# Key Terms

<u>Abstract Method<u>

An __abstract method__ is a method that is defined in an interface or abstract class and does not provide an implementation. Abstract methods are designed to be overriden by base or subclasses that extend the class or implement the interface they're defined in.

<u>Abstract Class<u>

An __abstract class__ is a class that contains at least one abstract method and is not meant to be instantiated. Abstract classes are meant to act as the parent or base class in an inheritance hierarchy. Typically abstract classes implement some functionality that can be used commonly by all child or subclasses.

""""""

# Notes

- An __abstract class__ is designed to act as the base class in an inheritance hierarchy and is not designed to be instantiated. Abstract classes usually contain abstract methods that are meant to be implemented by classes that inherit from them.

- All method types are allowed in an abstract class. Abstract classes usually contain some concrete methods (ones that provide an implementation) while also defining abstract methods that must be implemented by child classes that inherits from it.

- In many other programming languages it is enforced that a subclass of an abstract class must implement any abstract methods it contains. However, in Python this behavior is not enforced and although it is conventional for subclasses of an abstract class to do so it is not required.

- An abstract class should not be instantiated and is meant to function as a base class that provides already implemented behavior that can be extended by any subclasses to create a full implementation. Abstract classes often contain abstract methods that are meant to be implemented by any subclasses to create a full implementation of the abstract class.

""""""

# Abstract Class Example

""""""

pass

""""""

[course-site]: https://www.programmingexpert.io/index