---
layout: default
title:  "Static Methods"
date:   2023-10-17 15:23:00 -0400
categories: blog
---

Today, I cover __Static Methods__ from the [programmingexpert.io][course-site] course.

""""""

# Key Terms

<ins>Static Method<ins>

A __static__ method is defined within a class but should not reference anything relevant to that class specifically, except for other static methods. For the most part, static methods should only be used for __pure__ functions, which do not use temporary variables outside of their own scope and exclusively transform a set of inputs into some outputs. For instance, a method that converts a distance from kilometers to miles should most likely be __static__. Static methods are denoted using the __@staticmethod__ decorator.

""""""

[course-site]: https://www.programmingexpert.io/index