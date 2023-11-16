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

[course-site]: https://www.programmingexpert.io/index