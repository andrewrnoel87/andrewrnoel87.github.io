---
layout: default
title:  "Refreshing the Fundamentals / Lists"
date:   2023-09-13 14:30:00 -0400
categories: blog
---
Studying from the [programmingexpert.io][course-site] course today. The course is teaching using Python. I am using the course to refresh many of the things I learned in college. 

Before I started this blog, I went through __Data Types__, __Comments__, __Variables__, __Printing__, __Console Input__, and __Arithmetic Operators__.

Today, I covered __Type Conversions__, __Conditions__, __Compound Conditions__, __Conditionals__, and __Lists__.

""""""

A List is a collection data type. Common methods used with Lists are .append(), .pop(), .count(), .index(), .remove(), and .extend(). The 'in' operator and the len() function are commonly used as well. Negative indexing and List Concatenation are also possible.

""""""

I enjoyed this problem from today's exercises.

The objective was to write a program that asks the user to input five strings and store them in a list.
Then, the program should ask the user to input three numbers in the range 0 to 4, inclusive (these numbers represent the list indices).
Finally, the program should use these numbers to access the three strings at the corresponding indices in the previously created list, concatenate them, and print out the resulting string.

- My Solution -

lst = []

index = []

output = ""

for i in range(5):

    lst.append(input("Enter a string: "))

for i in range(3):

    index.append(int(input("Enter a number: ")))

for i in range(len(index)):

    output = output + lst[index[i]]

print(output)

""""""

I want to rewrite this in java at some point. Going to stay focused on the lesson for now.

Here are example solutions the course provide.

""""""

- Solution 1 -

string1 = input("Enter a string: ")

string2 = input("Enter a string: ")

string3 = input("Enter a string: ")

string4 = input("Enter a string: ")

string5 = input("Enter a string: ")

strings = [string1, string2, string3, string4, string5]

num1 = int(input("Enter a number: "))

num2 = int(input("Enter a number: "))

num3 = int(input("Enter a number: "))

final_string = strings[num1] + strings[num2] + strings[num3]

print(final_string)

""""""

- Solution 2 -

string1 = input("Enter a string: ")

string2 = input("Enter a string: ")

string3 = input("Enter a string: ")

string4 = input("Enter a string: ")

string5 = input("Enter a string: ")

strings = []

strings.append(string1)

strings.append(string2)

strings.append(string3)

strings.append(string4)

strings.append(string5)

num1 = int(input("Enter a number: "))

num2 = int(input("Enter a number: "))

num3 = int(input("Enter a number: "))


final_string = strings[num1] + strings[num2] + strings[num3]

print(final_string)

""""""

- Solution 3 -

strings = [

    input("Enter a string: "),

    input("Enter a string: "),

    input("Enter a string: "),

    input("Enter a string: "),

    input("Enter a string: "),

]

num1 = int(input("Enter a number: "))

num2 = int(input("Enter a number: "))

num3 = int(input("Enter a number: "))

final_string = strings[num1] + strings[num2] + strings[num3]

print(final_string)

""""""

I find it interesting that there are multiple solutions. Based on the solutions provided, I feel like I wasn't
supposed to be using 'for' loops yet.

""""""

[course-site]: https://www.programmingexpert.io/index