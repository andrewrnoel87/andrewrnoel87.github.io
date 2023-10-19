---
layout: default
title:  "Abstract Classes and Interfaces"
date:   2023-10-19 12:24:00 -0400
categories: blog
---

Today, I cover __Abstract Classes__ and __Interfaces__ from the [programmingexpert.io][course-site] course.

""""""

# Abstract Classes Key Terms

<u>Abstract Method<u>

An __abstract method__ is a method that is defined in an interface or abstract class and does not provide an implementation. Abstract methods are designed to be overriden by base or subclasses that extend the class or implement the interface they're defined in.

<u>Abstract Class<u>

An __abstract class__ is a class that contains at least one abstract method and is not meant to be instantiated. Abstract classes are meant to act as the parent or base class in an inheritance hierarchy. Typically abstract classes implement some functionality that can be used commonly by all child or subclasses.

""""""

# Abstract Class Notes

- An __abstract class__ is designed to act as the base class in an inheritance hierarchy and is not designed to be instantiated. Abstract classes usually contain abstract methods that are meant to be implemented by classes that inherit from them.

- All method types are allowed in an abstract class. Abstract classes usually contain some concrete methods (ones that provide an implementation) while also defining abstract methods that must be implemented by child classes that inherits from it.

- In many other programming languages it is enforced that a subclass of an abstract class must implement any abstract methods it contains. However, in Python this behavior is not enforced and although it is conventional for subclasses of an abstract class to do so it is not required.

- An abstract class should not be instantiated and is meant to function as a base class that provides already implemented behavior that can be extended by any subclasses to create a full implementation. Abstract classes often contain abstract methods that are meant to be implemented by any subclasses to create a full implementation of the abstract class.

""""""

# Abstract Class Example

""""""

import random

class AbstractGame:  # an abstract class, not to be instantiated

    def start(self):  # concrete instance method
        while True:
            start = input("Would you like to play? ")
            if start.lower() == "yes" or start.lower() == "y":
                break
        self.play()    
            

    def end(self):  # concrete instance method
        print("The game has ended.")
        self.reset()
    
    def play(self):  # abstract method
        raise NotImplementedError("play() has not been implemented yet")
    
    def reset(self):  # abstract method
        raise NotImplementedError("reset() has not been implemented yet")
    
class AnotherGame(AbstractGame):

    pass

class RandomGuesser(AbstractGame):

    def __init__(self, rounds):
        self.rounds = rounds
        self.round = 0

    def reset(self):  # implements reset()
        self.round = 0

    def play(self):  # implements play()
        while self.round < self.rounds:
            self.round += 1
            print(f"Welcome to round {self.round}. Let's Begin!")
            random_num = random.randint(1, 10)
            while True:
                guess = input("Enter a number between 1 - 10: ")
                if int(guess) == random_num:
                    print("You got it!")
                    break
        self.end()

<u>Sample Input<u>

\>>>games = [RandomGuesser(1), AnotherGame()]  # Will run until AnotherGame() is called. The system will throw an error because reset() and play() are not implemented in AnotherGame().

\>>>for game in games:

\>>>    game.start()  # each subclass of AbstractGame will inherit .start()

""""""

# Interfaces Key Terms

<u>Interface<u>

In Python, there is no formal definition for an __interface__ but we can still represent one by creating a class that only defines abstract methods. An interface is designed to be used as an abstract data type that enforces the following: the classes that implement it will define specific methods and behaviour.

""""""

# Interface Notes

""""""

- Interfaces, like abstract classes, should not be instantiated. There are meant to act as an abstract data type that classes will implement.

- Unlike abstract classes the only methods allowed in an interface are abstract. An interface does not provide any concrete methods or behavior.

- An interface is an abstract data type that is meant to be implemented by a class. Any class that implements (in Python, inherits) an interface must implement all of the methods defined in the interface. This makes the interface act like a blueprint for the class. Interfaces provide no concrete implementations and do not reduce the amount of code needed for classes implementing them.

""""""

# Interface Example

""""""

import math

class ShapeInterface:  # The suffix Interface is used to denote an interface. Interface in python is a convention, does not enforce anything.

    def get_area(self):
        raise NotImplementedError()

    def get_perimeter(self):
        raise NotImplementedError()


class Square(ShapeInterface):  # Implements all methods inherited from interface

    def __init__(self, side_length):
        self.side_length = side_length

    def get_area(self):
        return self.side_length * self.side_length

    def get_perimeter(self):
        return self.side_length * 4


class Circle(ShapeInterface):  # Implements all methods inherited from interface

    def __init__(self, radius):
        self.radius = radius

    def get_area(self):
        return math.pi * (self.radius ** 2)

    def get_perimeter(self):
        return 2 * math.pi * self.radius

""""""

[course-site]: https://www.programmingexpert.io/index