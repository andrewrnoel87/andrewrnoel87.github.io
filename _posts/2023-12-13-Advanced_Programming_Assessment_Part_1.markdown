---
layout: default
title:  "Advanced Programming Assessment Part 1"
date:   2023-12-13 10:06:00 -0400
categories: blog
---
Today, I covered the __Advanced Programming Assessment__ from the [programmingexpert.io][course-site] course.

""""""

# Exercise One - Positive Even Squares

""""""

Write a function that accepts any number of positional arguments, all of which assume will be lists of integers. The function should filter all of these lists such that they only contain even positive integers and combine all of the lists into one list of integers. The function should then modify the combined list such that it contains the squares of all of the elements and return that list.

Use a combination of the __map__, __filter__ and __lambda__ functions/keywords to modify the lists.

See the sample input for an example.

Sample Input #1:

    *args = [[-5, 2, 3, 4, 5], [1, 3, 5, 6, 7], [-9, -8, 10]]

    # arguments will be passed postionally to the function like this: positive_even_squares([-5, 2, 3, 4, 5], [1, 3, 5, 6, 7], [-9, -8, 10])

Sample Output #1:

    [4, 16, 36, 100]  # The combined list of positive even integers is: [2, 4, 6, 10]. The result is the squares of all of these values.

""""""

My Solution for Exercise One:

    def positive_even_squares(*args):
        positive_even_list = []
        for lst in args:
                filtered_list = filter(lambda y: y > 0 and y % 2 == 0, lst)
                positive_even_list.extend(filtered_list)
    
        squares_list = map(lambda x: x**2, positive_even_list)

        return list(squares_list)

""""""

[course-site]: https://www.programmingexpert.io/index