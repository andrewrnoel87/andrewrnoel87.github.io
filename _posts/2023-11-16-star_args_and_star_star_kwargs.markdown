---
layout: default
title:  "*args And **kwargs"
date:   2023-11-16 13:25:00 -0400
categories: blog
---

Today, I cover __*args And **kwargs__ from the [programmingexpert.io][course-site] course.

""""""

# Key Terms

<u>*args and **kwargs<u>

Oftentimes, especially when writing __decorators__, you need to write a function that can accept any number of arguments (positional and keyword), and perform actions on these arguments no matter how many of them there are. By using __*args__ and __**kwargs__ as arguments to your function, you can ensure that the variable __args__ and __kwargs__ will contain all of the previously unused arguments that were passed into your function.

Remember that __args__ will be a tuple containing all postional arguments that were passed, and __kwargs__ will be a dictionary containing all of the keyword arguments. For instance:

    1 | def add_all_args(*args):
    2 |     return sum(list(args))
    3 |
    4 | print(add_all_args(1, 2, 3, 4, 5))  # 15

""""""

# Notes

""""""

# Exercise One

""""""

What does the following code print?:

    1 | print(*"hello")

<u>Answer<u>

- h e l l o

<u>Explanation<u>

This is the case because the __*__ operator unpacks an iterable object (in this case a string) into it's individual elements and passes the elements as positional arguments to the function. Since the __print__ function takes any number of positional arguments and prints them seperated by spaces we get __h e l l o__.

""""""

# Exercise Two

""""""

What does the following code print?:

    1 | print(*[1, 2, 3, 4], **{'end': "|", 'sep': "*"})

<u>Answer<u>

- 1*2*3*4|

<u>Explanation<u>

The __*__ operator unpacks an iterable object (in this case a list) into it's individual elements and passes the elements as positional arguments to a function. This means the print function gets passed __1__, __2__, __3__ and __4__ as positional arguments.

The __\*\*__ operator unpacks items from a dictionary into keyword arguments that are passed to a function. This means the __print__ function gets passed __end="|"__ and __sep="*"__ as keyword arguments. The __sep__ keyword argument defines the seperator between individual items, by default it is a space. The __end__ keyword argument defines the last character to be printed, by default it is a __\n__.

If we break down the code after the __\*__ and __\*\*__ are applied we get the following: __print(1, 2, 3, 4, end="|", sep="\*")__. This results in __1*2*3*4|__ being printed.

""""""

# Exercise Three

""""""

Write a function named __get_args_and_kwargs__ that accepts an unlimited number of positional and keyword arguments. The function should return __True__ if there are at least __4__ total arguments and if the keyword argument __num__ exists, is a number and is larger than __5__. Otherwise, it should return __False__.

The function should handle any errors that may occur.

Sample Output:

     1 | >>> get_args_and_kwargs("a", [2], 3, num=4)
     2 | False
     3 | >>> get_args_and_kwargs("a", [2], 3, num=6)
     4 | True
     5 | >>> get_args_and_kwargs("a", [2], num=6, x=True)
     6 | True
     7 | >>> get_args_and_kwargs(2, 3, a=1, b=2, num="6")
     8 | False
     9 | >>> get_args_and_kwargs(2, 3, a=1, b=2, number=7)
    10 | False

Solution:

    def get_args_and_kwargs(*args, **kwargs):
        number_of_args = len(args) + len(kwargs)
        if number_of_args >= 4:
            if "num" in kwargs.keys():
                if kwargs["num"] > 5:
                    return True
        return False

Instructor Solution:

    # Copyright © 2022 AlgoExpert LLC. All rights reserved.

    def get_args_and_kwargs(*args, **kwargs):
        number_of_args = len(args) + len(kwargs)
        num = kwargs.get("num", 0)

        if not isinstance(num, int) and not isinstance(num, float):
            return False

        return number_of_args >= 4 and num > 5

""""""

[course-site]: https://www.programmingexpert.io/index