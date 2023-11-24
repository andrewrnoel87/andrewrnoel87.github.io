---
layout: default
title:  "Function Closures"
date:   2023-11-24 08:05:00 -0400
categories: blog
---

Today, I cover __Function Closures__ from the [programmingexpert.io][course-site] course.

""""""

# Key Terms

<u>Closures<u>

A __closure__ is the combination of a function bundled together (enclosed) with references to its surrounding state (the lexical environment). In other words, a closure gives you access to an __outer function__'s scope from an __inner function__.

<u>Free Variable<u>

A __free variable__ is a variable __not local__ to the scope of an inner function.

""""""

# Notes

- Functions are objects.

- Closures are a form of nested functions.

- A closure could replace a class.

Closure Example of counter():

    def counter(start):
        count = start

        def increment(value):
            nonlocal count
            count += value
            return count

        return increment

    count = counter(2)
    print(count(1))

Class Example of Counter():

    class Counter:
        def __init__(self, start):
            self.count = start
        def count_increment(self, value):
            self.count += value
            return self.count

    count = Counter(2)
    print(count.count_increment(1))

""""""

# Exercise One

""""""

What does the following code print?:

    1 | def a(x):
    2 |     def b(x):
    3 |         print(x)
    4 |
    5 |     return b
    6 |
    7 | a("b")("a")

<u>Answer<u>:

    a

<u>Explanation<u>

This is because when calling function __a__, function __b__ will be returned. Function __b__ uses the parameter __x__ which is a name that exists in the outer function scope in function __a__. However, since function __b__ defines its own __x__ parameter locally it will use that value, not the value from the outer scope. Therefore, the value passed as parameter __x__ to function __b__ will be printed which has the value __"a"__.

""""""

# Exercise Two

""""""

What does the following code print?:

     1 | def foo(x):
     2 |    def bar():
     3 |        nonlocal x
     4 |        print(x)
     5 |        x = 1
     6 |
     7 |    print(x)
     8 |    return bar
     9 |
    10 | foo(3)()

<u>Answer<u>:

    3
    3

<u>Explanation<u>

1. The __foo__ function is called with __x = 3__.
2. The __bar__ function is created but not executed.
3. The __foo__ function prints the value of __x__ at the current point in time, which is still __3__; the code __x = 1__ has not be executed yet.
4. The __bar__ function is returned.
5. The __bar__ function is called (denoted by the second set of paranthesis on the call __foo(3)()__).
6. The __bar__ function defines __nonlocal x__ which means it will be referencing and changing the __x__ in it's outer scope which comes from function __foo__.
7. The __bar__ function prints the value of __x__ which is still __3__.
8. The __bar__ function changes the value of __x__ to __1__ which has no effect on what has already been printed.

""""""

# Exercise Three

""""""

What does the following code print?:

     1 | def foo(x, y):
     2 |    def bar():
     3 |        nonlocal y
     4 |        x = 3
     5 |        y *= 5
     6 |
     7 |    bar()
     8 |    return x, y
     9 |
    10 | print(foo(4, 5))

<u>Answer<u>:

    (4, 25)

<u>Explanation<u>

1. When __foo(4, 5)__ is called __x = 4__ and __y = 5__ and the body of __foo__ is executed.
2. The __bar__ function is then called from inside of __foo__ and declares __nonlocal y__. Now __y__ will be referenced and modified from the outer scope.
3. The first line of the __bar__ function is __x = 3__ which declares a new local variable in the __bar__ scope. This does not modify the parameter __x__ from the outer scope.
4. Next, __y__ is multiplied by __5__ which does modify the value of the parameter __y__ from the outer scope. This is because __y__ was declared as __nonlocal__.
5. The __bar__ function then terminates and when __x__ and __y__ are returned from the __foo__ function their values are __4__ and __25__ respectively.

""""""

[course-site]: https://www.programmingexpert.io/index