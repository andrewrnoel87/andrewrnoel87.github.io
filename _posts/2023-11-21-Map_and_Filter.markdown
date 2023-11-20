---
layout: default
title:  "Map and Filter"
date:   2023-11-20 08:05:00 -0400
categories: blog
---

Today, I cover __Map and Filter__ from the [programmingexpert.io][course-site] course.

""""""

# Key Terms

<u>Map<u>

pass

<u>Filter<u>

pass

""""""

# Notes

- pass

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

    1 | pass

<u>Answer<u>

- [[4, 5, 6], [-5, -7]]

<u>Explanation<u>

The filter function works similarily to the map function and accepts as arguments a function and an iterable. In this case the function we passed was lambda a: abs(sum(a)) > 10 and the iterable was lst. The filter function then generates a new iterable object that contains only the elements that when passed to the function returned True.

To determine what elements will be in the iterable returned by the filter function we need to first understand what the passed function does. In this example the function we passed will take the absolute value of the sum of the element passed (which will be a list of numbers) and determine if it is greater than 10. The only elements in our list where the function returns True are [4, 5, 6] and [-5, -7].

""""""

# Exercise Three

""""""

pass

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