---
layout: default
title:  "Abstraction"
date:   2023-12-29 11:05:00 -0400
categories: blog
---

Today, I cover __Abstraction__ from the [programmingexpert.io][course-site] course.

""""""

# Notes

- Increasing abstraction is making programming coding systems more general.

- Something that is __abstract__ is __general__, something that is __concrete__ is a __specific implementation__.

- You want abstraction to __hide__ or defer __complexity/detail__ from people that are trying to understand and read your code. 

- Example. An iterable object is very abstract. All we need to know is... if it is iterable it has the iter() and next() methods. We do not need to know exactly how those work.

- sort(), max(), min() are abstract in python. This makes them easy to use.

- __for__ loops are abstract. It is general enough to work with many things.

- The __more general__ the code the __better__.

""""""

[course-site]: https://www.programmingexpert.io/index