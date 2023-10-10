---
layout: default
title:  "Creating Classes"
date:   2023-10-10 15:39:00 -0400
categories: blog
---

Today, I cover the Creating Classes from the [programmingexpert.io][course-site] course.

""""""

# Key Terms

Attribute

An attribute is an object that belongs either to a class, or to an instance of that class. Attributes of an object can be referenced using the . notation: print(person.name). Class attributes are attributes that are shared by all instances of that class, while instance attributes may have a different value for each and every instance that was created.

Constructor

The constructor of a class is a function defined within the class definition that will be called when a new instance is created. In Python, the constructor is implemented with the __init__ method. Typically, the constructor is responsible for initializing any instance variables, and essentially prepares the instance for use by the rest of the program.

Instance

An instance of a class is an object created from that class's "blueprint". For example, Person("Tim") will return an instance of the Person class.

Encapsulation

Encapsulation, in Object Oriented Programming, refers to how a programmer might prevent outside access to the details of a class in order to simplify the way the class might be used, or to make it harder to misuse the functionality that is exposed through certain methods or properties.

""""""



""""""

[course-site]: https://www.programmingexpert.io/index