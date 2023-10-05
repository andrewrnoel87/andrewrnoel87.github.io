---
layout: default
title:  "Programming Fundamentals Assessment Part 1"
date:   2023-10-04 14:52:00 -0400
categories: blog
---
Today, I covered the Programming Fundamentals Assessment from the [programmingexpert.io][course-site] course.

""""""

# """Exercise One"""

""""""

Random Number Guesser

Write a program that asks the user to enter two integers representing the start and the end of a range. The program should then generate a random number within this range (inclusively) and ask the user to guess numbers until they guess the randomly generated number. Once the user guesses the random number, the program should tell them how many attempts it took them to guess it. Your program needs to ensure that the range of numbers given is valid. For example, if the user enters a number for the end of the range that is less than the start of the range your program needs ask them to enter a valid number. Your program must also handle any other errors that might occur, like the user entering a string instead of an integer.

Note:You may assume the start of the range will never be negative (i.e. you don't need to handle
negative values).

""""""

- My Solution for One -

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

I like the way the instructor handled the plural with a suffix.

""""""

# """Exercise Two"""

""""""

Caesar Cipher

Write a function that accepts a string and returns the caesar cipher encoding of that stringaccording to a secondary input parameter named offset.

The caesar cipher encoding of a string involves shifting each character in the string a set number of positions previous in the alphabet. For example, if you were performing a caesar cipher of the string "tim" with offset=2 you would get "rgk". "t" is shifted two positions to "r", "i" is shifted two positions to "g" and "m" is shifted two positions to "k".

In the situation where the shift of a character results in it being a position before "a" the positions wrap and the next character should be "z". For example, the caesar cipher of "ab" with offset=2 would be "yz".

offset will always be a positive integer that is no greater than 26 and the input string will only contain lowercase letters.

""""""

- My Solution for Two -

""""""

def caesar_cipher(string, offset):

    string_list = [i for i in string]

    alphabet = 'abcdefghijklmnopqrstuvwxyz'

    shifted_alphabet = [i for i in alphabet]

    for i in range(len(shifted_alphabet)):  # creating the shifted alphabet

        shifted_alphabet[i] = alphabet[i - offset]

    for i in range(len(string_list)):  # swaping the string char with the shifted char

        char = string_list[i]

        target_char = shifted_alphabet[alphabet.index(char)]

        string_list[i] = target_char

    coded_string = ""

    for elem in string_list:  # changing the coded list back into a string

        coded_string += elem
    
    return coded_string

""""""

""""""

- Provided Sample Solution for Two -

""""""

def caesar_cipher(string, offset):

    alphabet = ['a', 'b', 'c', 'd', 'e', 'f', 'g', 'h', 'i', 'j', 'k', 'l',

                'm', 'n', 'o', 'p', 'q', 'r', 's', 't', 'u', 'v', 'w', 'x', 'y', 'z']

    encoded_string = ''

    for character in string:

        position = alphabet.index(character)

        offset_position = position - offset

        # No need to handle negative positions because of negative indexing

        encoded_character = alphabet[offset_position]

        encoded_string += encoded_character

    return encoded_string

""""""

After going over the provided solution, I see my solution could have been more elegant. It looks like the exercise could have been solved without making a whole shitfted alphabet list. 

""""""

[course-site]: https://www.programmingexpert.io/index