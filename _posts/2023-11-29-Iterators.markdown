---
layout: default
title:  "Iterators"
date:   2023-11-29 11:05:00 -0400
categories: blog
---

Today, I cover __Iterator__ from the [programmingexpert.io][course-site] course.

""""""

# Key Terms

<u>Iterator<u>

An __iterator__ is a special kind of object that implements a single function: __next()__. Iterators historically were created through class definitions which had to implement the __\_\_iter\_\_()__ method to create the iterator, in addition to the __\_\_next\_\_()__ method. However, most modern programmers opt to use the __generator__ syntax nowadays due to increased readability and conciseness.  

""""""

# Notes

- An iterator raises the __StopIteration__ excpetion when it runs out of elements. This exception is raised from the iterators __\_\_next\_\_()__ method.

""""""

# Exercise One

""""""

What is the output of the following code?:

    1 | string = "iterable"
    2 | string_itr = iter(string)
    3 | string.__iter__().__next__()
    4 | next(string_itr)
    5 |
    6 | for char in string_itr:
    7 |     print(char)
    8 |     break

<u>Answer<u>

__t__

<u>Explanation<u>

This is because the __iter__ function and the __\_\_iter\_\___ method return new iterator objects. This means __string_itr__ is a different iterator than __string.\_\_iter\_\_()__.

Since these are different objects when we call __next(string_itr)__ it advances that iterator to the next element which is __t__. That means when we continue looping through __string_itr__ in the for loop we start at element __t__ and immediately print it.

""""""

# Exercise Two

""""""

Write a class based iterator named __Range__ that is intialized by passing three integer values, a start, stop and step. The iterator should mimic the __range__ function in functionality but always accept three integer values.

Assume all three of these initialization values will always be integers and that the step will never be zero.

Sample Output:

     1 | >>> r = Range(2, 5, 1)
     2 | >>> for x in r:
     3 |        print(x)
     4 | 2
     5 | 3
     6 | 4
     7 | >>> r = Range(-2, -5, -1)
     8 | >>> for x in r:
     9 |        print(x)
    10 | -2
    11 | -3
    12 | -4
     
<u>Answer<u>:

    class Range:
        def __init__(self, start, stop, step):
            self.start = start
            self.stop = stop
            self.step = step

        def __iter__(self):
            self.current_value = self.start
            return self
    
        def __next__(self):
            if self.current_value >= self.stop and self.step > 0:
                raise StopIteration
            elif self.current_value <= self.stop and self.step < 0:
                raise StopIteration

            self.current_value += self.step  #  set the next next_value

            return self.current_value - self.step # return current next_value 

""""""

[course-site]: https://www.programmingexpert.io/index