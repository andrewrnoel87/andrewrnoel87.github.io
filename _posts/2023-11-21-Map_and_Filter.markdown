---
layout: default
title:  "Map and Filter"
date:   2023-11-21 08:05:00 -0400
categories: blog
---

Today, I cover __Map and Filter__ from the [programmingexpert.io][course-site] course.

""""""

# Key Terms

<u>Map<u>

__map(func, *iterables)__ makes an iterator that computes the function using arguments from each of the iterables. It stops when the shortest iterable is exhausted. In other words, __map__ applies a function to each element in an iterable object.

<u>Filter<u>

__filter(function or None, iterable)__ returns an iterator yielding those items of iterable for which function(item) is true. If function is None, return the items that are true. In other words, __filter__ applies a specific constraint to each element in an iterable object and returns the elements that returned True.

""""""

# Notes

- We can loop through iterable objects.

""""""

# Exercise One

""""""

What does the following code print?:

    1 | lst = ["algoexpert", "is", "the", "best"]
    2 | x = map(len, lst)
    3 | print(list(x))

<u>Answer<u>

- [10, 2, 3, 4]

<u>Explanation<u>

The __map__ function takes two arguments, a function and an iterable object. In this case the function we passed was __len__ and the iterable was __lst__. The __map__ function then generates a new iterable object that maps all of the values from the iterable to the passed function. The new iterable will have elements equal to the return value of the function called on each element. Since our function is __len__ we get an iterable containing the lengths of all of the strings in __lst__.

""""""

# Exercise Two

""""""

What does the following code print?:

    1 | lst = [[2, 3, 4], [4, 5, 6], [1, 1, 1], [0, 0], [-5, -7]]
    2 | x = filter(lambda a: abs(sum(a)) > 10, lst)
    3 | print(list(x))

<u>Answer<u>

- [[4, 5, 6], [-5, -7]]

<u>Explanation<u>

The __filter__ function works similarily to the __map__ function and accepts as arguments a function and an iterable. In this case the function we passed was __lambda a: abs(sum(a)) > 10__ and the iterable was __lst__. The __filter__ function then generates a new iterable object that contains only the elements that when passed to the function returned __True__.

To determine what elements will be in the iterable returned by the __filter__ function we need to first understand what the passed function does. In this example the function we passed will take the absolute value of the sum of the element passed (which will be a list of numbers) and determine if it is greater than __10__. The only elements in our list where the function returns __True__ are __[4, 5, 6]__ and __[-5, -7]__.

""""""

# Exercise Three

""""""

Use the __map__ and __filter__ functions to create an iterable that contains the even squares of all elements in the __lst__ list. Once you've created this iterable print out all of its values on separate lines.

Use __lambda__'s for any functions you create.

Sample Output:

    4
    16
    36
    64
    100

Solution:

    lst = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]

    even_squares = map(lambda x: x ** 2, filter(lambda y: y % 2 == 0, lst))

    for item in even_squares:
        print(item)


""""""

[course-site]: https://www.programmingexpert.io/index