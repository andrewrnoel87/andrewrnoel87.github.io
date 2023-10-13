---
layout: default
title:  "Properties"
date:   2023-10-13 10:53:00 -0400
categories: blog
---

Today, I cover __Properties__ from the [programmingexpert.io][course-site] course.

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

[course-site]: https://www.programmingexpert.io/index