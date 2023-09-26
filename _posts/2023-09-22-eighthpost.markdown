---
layout: default
title:  "Exceptions"
date:   2023-09-22 13:46:00 -0400
categories: blog
---
Today I covered Exceptions from the [programmingexpert.io][course-site] course.

""""""

Do not always surround code with try-except blocks. Use only when you know an error can occur.

"""The Exception Exercise"""

Write a program that asks a user for two numbers: a numerator and a denominator. Your program should divide the numerator by the denominator and handle any exceptions that might occur during the division. Specifically, your program should catch exceptions when either the numerator or the denominator is not a number and when the denominator is 0. All exceptions should be caught and handled, even when there are multiple. If the division does not raise any exceptions, the program should print the result of the division. And regardless of the outcome, the program should tell the user goodbye!

"""My Solution"""

numerator = input("Enter the numerator: ")

denominator = input("Enter the denominator: ")

try:

    numerator = float(numerator)

except Exception as e:

    print("The numerator is not a number.")

try:

    denominator = float(denominator)

    if denominator == 0:

        print("You cannot divide by 0.")

except Exception as e:

    print("The denominator is not a number.")


try:

    result = numerator / denominator

    print(f"The result of this division is {result}.")

except Exception as e:

    print("This division cannot be performed.")

finally:

    print("Goodbye!")

""""""

"""Alternate Solution Provided"""

""""""

numerator = input("Enter the numerator: ")

denominator = input("Enter the denominator: ")

try:

    numerator = float(numerator)

except Exception as e:

    print("The numerator is not a number.")

try:

    denominator = float(denominator)

except Exception as e:

    print("The denominator is not a number.")


try:

    result = numerator / denominator

    print(f"The result of this division is {result}.")

except ZeroDivisionError as e:

    print("You cannot divide by 0.")

    print("This division cannot be performed.")

except Exception as e:

    print("This division cannot be performed.")

finally:

    print('Goodbye!')

""""""

[course-site]: https://www.programmingexpert.io/index