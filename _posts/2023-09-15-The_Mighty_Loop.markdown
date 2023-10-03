---
layout: default
title:  "The Mighty Loop"
date:   2023-09-15 14:03:00 -0400
categories: blog
---
Today I covered 'For' Loops  and 'While' Loops from the [programmingexpert.io][course-site] course.

""""""

"""For Loop Exercise 1"""

Here is some code I wrote for an exercise. The goal of the exercise was to use a single for loop to iterate through the two strings, and print all of their matching characters(i.e., the characters that are the same index and that are equal to each other), each on a separate line.

- My Solution for One -

string1 = "aabbcsdw"

string2 = "abbbcsdd"

for i, char in enumerate(string1):

    if string1[i] == string2[i]:

        print(char)

""""""

"""For Loop Exercise 2"""

Use a single for loop to iterate through the provided list, and print the elements that are both divisible by 2 and located at an odd index, each on a separate line.

- My Solution for Two -

lst = [45, 24, 22, 1, 45, 2, 12, 13, 16, 10, 0, -7]

for i, elem in enumerate(lst):

    if (elem % 2 == 0) and (i % 2 != 0):

        print(elem)

""""""

"""For Loop Exercise 3"""

Use nested for loops to iterate through the provided list, which contains other lists, and print the respective sums of the inner lists, each on a separate line.

- My Solution for Three -

lst = [[2, 3, 4], [-2, -4, 0], [1, 2], [1, 1, 1, 5, 6], [0, 9, 8, 7]]

for elem in lst:

    sum = 0

    for inner_elem in elem:

        sum += inner_elem

    print(sum)

""""""

"""For Loop Exercise 4"""

Use a single for loop to iterate through the provided list of numbers, and for each number, print the sum of the number and the one directly to its right. Since the last number in the list has no number to the right of it, skip it.

- My Solution for Four -

lst = [-2, 0, 4, 5, 1, 2]

for i in range(len(lst) - 1):

    print(lst[i] + lst[i + 1])

""""""

"""While Loop Exercise 1"""

Write a program that continually asks the user to enter a number until they enter the number 5, at which point the program should print how many numbers the user has entered. Assume the user will only ever enter a number.

- My Solution for One -

input_count = 0

while True:

    num = int(input("Enter a number: "))

    input_count += 1

    if num == 5:

        print(f"You entered {input_count} numbers.")

        break

""""""

"""While Loop Exercise 2"""

Write a program that continually asks the user to enter a word until they enter the word "q" or "quit", at which point the program should print the average length of all of the entered words, excluding the "q" or "quit". If the user doesn't enter any words(i.e., immediately enters "q" or "quit"), the program should not print anything. 

This one was a bit of a challenge at first. I was over complicating the conditionals. Also, when to break the loop and when to update the variables needs to be handled carefully.

- My Solution for Two -

number_of_inputs = 0

total_char_count = 0


while True:

    user_input = input("Enter a word: ")

    if user_input == "q" or user_input == "quit":

        break

    total_char_count += len(user_input)

    number_of_inputs += 1
    
if number_of_inputs > 0:

    average_word_len = total_char_count / number_of_inputs

    print(f"The average word length is: {average_word_len}.")

""""""

"""While Loop Exercise 3"""

Use a while loop to print the squares of the numbers: 1, 3, 6, 10, 15 and 21.

- My Solution for Three -

lst = [1, 3, 6, 10, 15, 21]

index = 0

while index < len(lst):

    square = lst[index] * lst[index]
    print(square)
    index += 1

""""""

- An Interesting Solution for Three -

num = 1

step = 2

while num <= 21:

    print(num * num)

    num += step

    step += 1

""""""

[course-site]: https://www.programmingexpert.io/index