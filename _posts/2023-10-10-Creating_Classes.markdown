---
layout: default
title:  "Creating Classes"
date:   2023-10-10 15:39:00 -0400
categories: blog
---

Today, I cover the Creating Classes from the [programmingexpert.io][course-site] course.

""""""

# Key Terms

<ins>Attribute<ins>

An attribute is an object that belongs either to a class, or to an instance of that class. Attributes of an object can be referenced using the . notation: print(person.name). Class attributes are attributes that are shared by all instances of that class, while instance attributes may have a different value for each and every instance that was created.

<ins>Constructor<ins>

The constructor of a class is a function defined within the class definition that will be called when a new instance is created. In Python, the constructor is implemented with the __init__ method. Typically, the constructor is responsible for initializing any instance variables, and essentially prepares the instance for use by the rest of the program.

<ins>Instance<ins>

An instance of a class is an object created from that class's "blueprint". For example, Person("Tim") will return an instance of the Person class.

<ins>Encapsulation<ins>

Encapsulation, in Object Oriented Programming, refers to how a programmer might prevent outside access to the details of a class in order to simplify the way the class might be used, or to make it harder to misuse the functionality that is exposed through certain methods or properties.

""""""

# Wisdom Nuggets

- In Python, the __init__ method is considered a classes constructor. Note that there are two underscores prefixing and suffixing the init. The __init__ method is called immediately after an instance of a class is created and is usually responsible for defining instance attributes and performing any required set up steps.

- self is always the first parameter in a class constructor. The self parameter refers to the instance of the class in which the method or constructor is being called on. The first parameter in the class constructor (a.k.a the __init__ method) is implicitly passed during the instantiation of a object and is mandatory. Note that the name self is a recommended convention in Python but not the mandatory name for this first parameter.

- Note that the self parameter will be implicitly passed to the constructor and does not need to be manually passed during instantiation.

- In Python object oriented programming an attribute is any data/objects associated with a class or an instance of a class. Attributes are not always defined inside of the class constructor and can be added to an instance after it's creation.

- According to PEP-8 (the style guide for Python) the proper casing for class names is PascalCase. Note that this is also commonly referred to as CapitalCamelCase.

- In Python, attributes can be accessed from outside of a class. So long as you have a reference to an instance you can access it's attributes. For example:

class Dog:

    def __init__(self, name):

        self.name = name
      
dog = Dog("Tim")

print(dog.name)  # this prints "Tim"

- In Python, attributes can be created outside of a class by defining them directly on an instance. For example:

class Dog:

    def __init__(self, name):

        self.name = name  # name is an attribute defined in the constructor
      
dog = Dog("Tim")

dog.age = 10  # this creates a new attribute called age on this dog instance

- Example of a class and two instaniated instances of it:

class ContactInformation:

    def __init__(self, first_name, last_name, email, phone_number):

        self.first_name = first_name

        self.last_name = last_name

        self.email = email

        self.phone_number = phone_number

        self.country = None

person1 = ContactInformation("Andrew", "Knoll", "andrewrnoel87@gmail.com", "563-639-3131")

person2 = ContactInformation("Tom", "Green", "tomgreen@hotmail.com", "563-285-3456")

""""""

[course-site]: https://www.programmingexpert.io/index