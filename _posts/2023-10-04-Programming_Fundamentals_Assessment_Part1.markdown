---
layout: default
title:  "Programming Fundamentals Assessment Part 1"
date:   2023-10-04 14:52:00 -0400
categories: blog
---
Today, I covered the Programming Fundamentals Assessment from the [programmingexpert.io][course-site] course.

""""""

"""Exercise One"""

""""""

Random Number Guesser

Write a program that asks the user to enter two integers representing the start and the end of a range. The program should then generate a random number within this range (inclusively) and ask the user to guess numbers until they guess the randomly generated number. Once the user guesses the random number, the program should tell them how many attempts it took them to guess it. Your program needs to ensure that the range of numbers given is valid. For example, if the user enters a number for the end of the range that is less than the start of the range your program needs ask them to enter a valid number. Your program must also handle any other errors that might occur, like the user entering a string instead of an integer.

Note:You may assume the start of the range will never be negative (i.e. you don't need to handle
negative values).

""""""

- My Solution -

""""""

import random

start_range = None

end_range = None

while True:  

    try:

        start_range = int(input("Enter the start of the range: "))

        if (start_range < 0):

            raise ValueError("This is not a vaild number.")

    except:

        print("Please enter a valid number.")

    if str(start_range).isdigit():

        break

while True:

    try:

        end_range = int(input("Enter the end of the range: "))

        if (end_range < start_range):

            raise ValueError("This is not a vaild number.")

    except:

        print("Please enter a valid number.")
    
    if str(end_range).isdigit() and (start_range <= end_range):

        break

guess_target = random.randint(start_range, end_range)

guess_current = None

guess_count = 0

while True:

    try:

        guess_current = int(input("Guess a number: "))

        guess_count += 1
       
    except:

        print("Please enter a valid number.")

    if guess_current == guess_target:

        break

if guess_count == 1:

    print("You guessed the number in 1 attempt")
        
else:

    print(f"You guessed the number in {guess_count} attempts")


""""""

- Provided Sample Solution for One -

""""""

import random

start = input('Enter the start of the range: ')

while not start.isdigit():

    print('Please enter a valid number.')

    start = input('Enter the start of the range: ')

end = input('Enter the end of the range: ')

while not end.isdigit() or int(end) < int(start):

    print('Please enter a valid number.')

    end = input('Enter the end of the range: ')

random_number = random.randint(int(start), int(end))

guess = None

attempts = 0

while guess != random_number:

    guessed_number = input("Guess a number: ")

    if not guessed_number.isdigit():

        print("Please enter a valid number.")

        continue
    
    attempts += 1

    guess = int(guessed_number)

suffix = ""

if attempts > 1:

    suffix = "s"

print(f'You guessed the number in {attempts} attempt{suffix}')

""""""



[course-site]: https://www.programmingexpert.io/index