---
layout: default
title:  "Scope"
date:   2023-09-29 15:53:00 -0400
categories: blog
---
Today I covered Scope in Python from the [programmingexpert.io][course-site] course.

""""""

The global keyword is typically considered bad practice and should be avoided. The reason for this is that the global keyword adds side-effects to a function and makes it dependent on something referenced outside the function scope. This means changes to the globally referenced object can change the behaviour of the function and be difficult to detect, especially if a bug or issue arises. In summary, the global keyword often introduces unnecessary complexity and can almost always be avoided.

Functions check local scope before looking at the global scope.

Mutability is an important factor when dealing with scope.

""""""

"""Scope Example"""

What does the following program print?

x = "global"

def foo():

    global x

    print(x, end=",")

    x = "local"

    print(x, end=",")

foo()

print(x, end="")

"""Scope Example Answer"""

global,local,local

""""""

"""Explanation"""

The first call to the print function that gets executed is the first one inside of the foo function. This call prints global,, because at that execution point in the program, x has only been defined as "global" in the global scope.

However, after this first print statement, we assign x to the new value of "local", meaning that when x is printed again right after, we print "local". We do not create a new x in the local scope, instead we change the value of the x in the global scope.

Finally, the last call to print takes in the x defined in the global scope, which was modified in the foo function because of the presence of the global keyword. Therefore, this call prints "local".

""""""

[course-site]: https://www.programmingexpert.io/index