---
layout: default
title:  "Modules and Packages"
date:   2023-11-13 14:14:00 -0400
categories: blog
---

Today, I cover __Modules and Packages__ from the [programmingexpert.io][course-site] course.

""""""

# Key Terms

<u>Main Module<u>

In Python, the __main__ module is the one that is invoked or run directly. Python will automatically set the __\_\_name\_\___ variable of that module to the string __"\_\_main\_\_"__. All modules that are imported from that main package will have their own values for the __\_\_name\_\___ variable.

When writing your modules in Python, it is best practice to run some parts of the code conditionally based on that __\_\_name\_\___ variable:

    if __name__ == "__main__":
        print("This code will only run if this is the main package!")

<u>Module<u>





""""""

""""""

[course-site]: https://www.programmingexpert.io/index