---
layout: default
title:  "Defensibility"
date:   2024-01-10 11:05:00 -0400
categories: blog
---

Today, I cover __Defensibility__ from the [programmingexpert.io][course-site] course.

""""""

# Notes

- Write code in a way, such that it defends against its misuse.

- Assume someone else is going to be using your code.

- Assume the user knows nothing about your code.

- Limit the ways your code can be misused.

- Make code that gives good error messages and prevents the user from using the code the wrong way.

- Example. Do not let the user pass a string when we are expecting an int.

- Perform a precondition. This means check the validity of the input to a function. Raise an exception if the input is invalid.

- Detailed error messages are better.

- Custom error messages can be helpful.

- Example. Let the user know if methods are being used in the wrong order.

- Writing defensive code can be time consuming upfront, but it can save time down the road. Especially for those using the code.

""""""

[course-site]: https://www.programmingexpert.io/index