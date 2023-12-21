---
layout: default
title:  "Advanced Programming Assessment Part 2"
date:   2023-12-14 10:06:00 -0400
categories: blog
---
Today, I covered the __Advanced Programming Assessment__ from the [programmingexpert.io][course-site] course.

""""""

# Exercise Two - Integer Sum

""""""

Write a function named __integer_sum__ that accepts any number of positional arguments, which are assumed to be integers. this function should return the sum of all of these integers.

To handle invalid input (arguments that are not integers) write the following decorators and use them to decorate the __integer_sum__ function.

- __flatten_lists__: this decorator should _flatten_ any __list__ arguments for the decorated function by extracting their elements and passing them as individual arguments instead of the list. For example, if __[1, 2, True]__ is an argument, then __1__, __2__ and __True__ should be extracted and passed as arguments instead of the __list__ to the decorated function.

- __convert_strings_to_ints__: this decorator should convert any string arguments that are valid integers to integers and pass them to the decorated function. Any string that is not a valid integer should be removed as an argument to the decorated function.

- __filter_integers__: this decorator should remove any argument that is not an integer and call decorated function with only integer arguments.

You may assume all arguments passed to __integer_sum__ will be of type __float__, __int__, __str__ or __list__.

Sample Input #1:

    args = ["1", "2", -0.9, 4, [5, "hi", "3"]]
    # arguments will be passed positionally to the function like this: integer_sum("1", "2", -0.9, 4, [5, "hi", "3"])

Sample Output #1:

    15  # The sum of "1", "2", 4, 5 and "3".

""""""

My Solution for Exercise Two:

    def flatten_lists(func):  # a list within a list within a list and deeper won't be counted
        def wrapper(*args):
            new_args = []
            for arg in args:
                if isinstance(arg, list):
                    new_args.extend(arg)
                else:
                    new_args.append(arg)

            result = func(*new_args)
            return result
        return wrapper

    def convert_strings_to_ints(func):
        def wrapper(*args):
            new_args = []
            for arg in args:
                if isinstance(arg, str) and arg.isdigit():
                    new_args.append(int(arg))
                else:
                    new_args.append(arg)
            result = func(*new_args)
            return result
        return wrapper

    def filter_integers(func):
        def wrapper(*args):
            new_args = []
            for arg in args:
                if isinstance(arg, int):
                    new_args.append(arg)
            result = func(*new_args)
            return result
        return wrapper

    @flatten_lists
    @convert_strings_to_ints
    @filter_integers
    def integer_sum(*args):
        return sum(args)

""""""

[course-site]: https://www.programmingexpert.io/index