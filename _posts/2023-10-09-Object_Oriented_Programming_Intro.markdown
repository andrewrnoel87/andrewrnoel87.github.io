---
layout: default
title:  "Object Oriented Programming Intro"
date:   2023-10-09 16:04:00 -0400
categories: blog
---

Today, I cover the Object Oriented Programming Intro from the [programmingexpert.io][course-site] course.

""""""

# Key Terms

Object

In Python, object is the class that all other classes inherit from, even if it wasn't declared explicitely by the programmer. Almost everything in Python is an object, including function's, list's, int's and all other instances of built in data types. An objects type is defined by the class that was used to instantiate it. For example, the assignment x = 1 creates a new object with type int containing the value 1.

Class

In programming, a class can be thought of a template or blueprint for the creation of objects. The type of an object is the class that was used to create it. Classes define the attributes and methods (i.e. the behavior) of objects that are instantiated using them.

""""""

- In Python, an object is an instance of any class. The class can be created by you, the programmer, or can be built into the language already.

- In Python, the term instantiation refers to the creation of an object based on a class.

- In Python, the type of an object is the class used to instantiate it. For example, if an object is instantiated from a user defined class called Animal, then that object's type is Animal.

- In object oriented programming, an objects behavior is defined by the attributes and methods it possesses. Objects of different types behave differently based on the logic defined in the class that was used to instantiate them. 

- In object oriented programming, a method is simply a function that is defined inside of a class and typically acts on an instance of that class. Methods that accept the self parameter are instance methods and can access the attributes and methods of the instance they are called on. Methods are typically called using the . (dot) notation. For example, "str".count("s"), [1, 2, 1].sort() and "str".upper() are all examples of methods. The method comes after the . (dot) and the instance that they act on is to the left of the . (dot).

""""""

[course-site]: https://www.programmingexpert.io/index