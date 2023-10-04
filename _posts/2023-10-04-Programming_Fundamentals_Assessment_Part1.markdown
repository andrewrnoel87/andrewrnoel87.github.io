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



""""""

[course-site]: https://www.programmingexpert.io/index