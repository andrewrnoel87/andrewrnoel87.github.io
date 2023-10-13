---
layout: default
title:  "Properties, Class Methods, and Class Attributes"
date:   2023-10-13 10:53:00 -0400
categories: blog
---

Today, I cover __Properties__, __Class Methods__, and __Class Attributes__ from the [programmingexpert.io][course-site] course.

""""""

# Notes

- In Python, all attributes of an object are public. This means they can be accessed from outside of the class they are defined in.

- In Python, since there is no access modifiers (private, public or protected keywords) to denote an attribute as private you prefix it with a _. The attribute can still be accessed and modified like all other attributes but the _ prefix denotes that it should not be, this is a Python convention.

- In object oriented programming, getters are used to return the value of attributes while setters are used to set the value of attributes. Both allow you to hide complexity by providing a single method that can be used to validate data before assigning it to an attribute (setter) or mutate data (e.g. rounding a number) before returning it (getter). Setters may also constrain an attribute value by only allowing you to set it to something considered valid by the class (e.g. you can't set a negative salary for an employee).

""""""

# Legacy Property Example

""""""

class BankAccount:

    def __init__(self, account_holder_name):

        self.account_holder_name = account_holder_name

        self._balance = 0

    def get_balance(self):

        return round(self._balance, 0)

    def set_balance(self, balance):

        if type(balance) not in [int, float]:

            return

        if balance < 0 or balance >= 100000:

            return
      
        self._balance = balance

    balance = property(get_balance, set_balance)

""""""

# @decorator Property Example

""""""

class BankAccount:

    def __init__(self, account_holder_name):

        self.account_holder_name = account_holder_name

        self._balance = 0

    @property  # getter

    def balance(self):

        return round(self._balance, 0)

    @balance.setter  # setter

    def balance(self, balance):

        if type(balance) not in [int, float]:

            return

        if balance < 0 or balance >= 100000:

            return
      
        self._balance = balance

""""""

<u>Sample Code Usage<u>

account = BankAccount("Antoine")

account.balance = 56.2

""""""

""""""

# Key Terms

<u>Class Attribute<u>

An __attribute__ is an __object__ that belongs either to a class, or to an instance of that class. Attributes of an object can be referenced using the __.__ notation:  print(__person.name__).

A __class attribute__ is an attribute that is associated with a class, not an instance of a class. Class attributes can be modified and accessed by using the class name directly or by using an instance of the class. Typically class attributes are defined at the top of the class, inside the class body.

<u>Class Method<u>

A __class method__ is a method that has a mandatory __cls__ parameter and can only access class attributes and other class methods. It does not act on an instance of a class, but on the class itself. Class methods are denoted with the __@classmethod__ decorator.

""""""

# Notes

- In Python, class attributes are attributes associated with a class, not an instance of a class. Class attributes can be accessed by using the class name or from any instance of the class.

- Class methods accept a mandatory cls parameter and are denoted using the @classmethod decorator, while instance attributes accept a mandatory self parameter. Class methods don't have access to an instance and therefore, can only modify and access class attributes and can only call other class (or static) methods. Instance attributes have access to an instance and can modify and access both instance and class attributes as well as call any other methods defined in the class.

""""""

# Class Attribute Example

""""""

class Employee:

    number_of_employees = 0  # class attribute

    average_age = 0  # class attribute

    average_salary = 0  # class attribute

    def __init__(self, name, age, salary):

        self.name = name  # setting initial instance attribute

        self.age = age  # setting initial instance attribute

        self.salary = salary  # setting initial instance attribute

        total_age = Employee.average_age * Employee.number_of_employees

        total_salary = Employee.average_salary * Employee.number_of_employees

        Employee.average_age = (total_age + age) / (Employee.number_of_employees + 1)  # updating class attribute

        Employee.average_salary = (total_salary + salary) / (Employee.number_of_employees + 1)  # updating class attribute

        Employee.number_of_employees += 1  # updating class attribute

""""""

""""""

[course-site]: https://www.programmingexpert.io/index