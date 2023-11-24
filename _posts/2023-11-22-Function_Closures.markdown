---
layout: default
title:  "Function Closures"
date:   2023-11-24 08:05:00 -0400
categories: blog
---

Today, I cover __Function Closures__ from the [programmingexpert.io][course-site] course.

""""""

# Key Terms

<u>Function Closure<u>

pass

""""""

# Notes

- pass

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

<u>Answer<u>

- __a__

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

<u>Answer<u>

- :
    __3__
    __3__

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

    1 | pass

<u>Answer<u>

- pass

<u>Explanation<u>

pass

""""""

[course-site]: https://www.programmingexpert.io/index