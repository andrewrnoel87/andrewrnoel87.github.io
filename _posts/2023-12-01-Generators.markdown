---
layout: default
title:  "Generators"
date:   2023-12-01 11:05:00 -0400
categories: blog
---

Today, I cover __Generators__ from the [programmingexpert.io][course-site] course.

""""""

# Key Terms

<u>Generator<u>

A __generator__ is a special kind of __iterator__ that uses the __yield__ keyword to return the next value in the sequence.

""""""

# Notes

- In Python, the presence of the __yield__ keyword in a function makes that function a generator.

- Many iterators can be done with a generator.

- The __yield__ keyword is similar to the __return__ keyword. __yield__ will pause the execution of a function. __return__ ends the function.

- The __yield__ keyword creates a generator object.

- 

Generator Example:

    def fib(n):
        last = 1
        second_last = 1
        current = 3

        while current <= n:
            num = last + second_last
            yield num  #  creates the generator object

            second_last = last
            last = num
            current += 1

    for val in fib(10):
        print(val)

""""""

# Exercise One

""""""

What is the output of the following code?:

     1 | def a(lst, power):
     2 |    for element in lst:
     3 |        if element % 2 == 0:
     4 |            yield element ** power
     5 |
     6 | gen = a([1, 2, 3, 4, 5, 6, 7, 8], 2)
     7 | next(gen)
     8 | next(gen)
     9 | next(gen)
    10 | print(next(gen))

<u>Answer<u>

__64__

<u>Explanation<u>

When the __a__ function is called it returns a generator that allows for the use of the __next__ method. Generators works exactly like iterators and will maintain their internal state until they are reset or run out of elements to iterate through.

In this code, our generator __yields__ all of the even element squares from the input list. This results in the calls to __next__ returning __4__, __16__, __36__ and __64__ respectively; we only __print__ __64__.

""""""

# Exercise Two

""""""

Write a generator named __new_range__ that is intialized by passing three integer values, a start, stop and step. The generator should mimic the __range__ function in functionality but always accept three integer values.

Assume all three of these initialization values will always be integers and that the step will never be zero.

Sample Output:

     1 | >>> r = new_range(2, 5, 1)
     2 | >>> for x in r:
     3 |         print(x)   
     4 | 2
     5 | 3
     6 | 4
     7 | >>> r = new_range(-2, -5, -1)
     8 | >>> for x in r:
     9 |         print(x)   
    10 | -2
    11 | -3
    12 | -4 
     
<u>Answer<u>:

    def new_range(start, stop, step):
        current = start
        if step > 0 and current <= stop:
            while current < stop:
                yield current
                current += step
        if step < 0 and current >= stop:
            while current > stop:
                yield current
                current += step

   

""""""

[course-site]: https://www.programmingexpert.io/index