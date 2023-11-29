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

- Iterators allow us to loop through iterable objects.

- The iterator object is different than the original object.

- __iter(object)__ retrieves the iterator for an iterable object.

- The __next()__ function is used on an iterator to get the next item.

- __iter(x)__ is the same as __x.\_\_iter\_\_()__.

- __next(x_iter)__ is the same as __x_iter.\_\_next\_\_()__.

- An iterator raises the __StopIteration__ excpetion when it runs out of elements. This exception is raised from the iterators __\_\_next\_\_()__ method.

Iterator Example:

    class Numbers:
        def __init__(self, num1, num2, num3):
            self.num1 = num1
            self.num2 = num2
            self.num3 = num3

        def __iter__(self):
            return NumberIterator(self.num1, self.num2, self.num3)

    class NumberIterator:
        def __init__(self, one, two, three):
            self.one = one
            self.two = two
            self.three = three
            self.current = 0

        def __next__(self):
            self.current += 1
            if self.current == 1:
                return self.one
            elif self.current == 2:
                return self.two
            elif self.current == 3:
                return self.three
            else:
                raise StopIteration

    nums = Numbers(1, 2, 3)
    itr = iter(nums)
    print(itr)
    print(next(itr))  #  1
    print(next(itr))  #  2
    print(next(itr))  #  3
    print(next(itr))  #  StopIteration exception

    for num in nums:  #  Works because our NumberIterator has the __next__ method and Numbers has __iter__
        print(num)

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

This is because the __iter()__ function and the __.\_\_iter\_\_()__ method return new iterator objects. This means __string_itr__ is a different iterator than __string.\_\_iter\_\_()__.

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