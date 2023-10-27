---
layout: default
title:  "Object-Oriented Programming Assessment Part 3"
date:   2023-10-27 10:06:00 -0400
categories: blog
---
Today, I covered the __Object-Oriented Programming Assessment__ from the [programmingexpert.io][course-site] course.

""""""

# """Exercise Four"""

""""""

<u>Deck Class<u>

Create a __Deck__ class that represents a deck of _52_ playing cards. The __Deck__ should maintain which cards are currently in the deck and never contain duplicated cards. Cards should be represented by a string containing their value (2 - 10, J, Q, K, A) followed by their suit (D, H, C, S). For example, the jack of clubs would be represented by "JC" and the three of hearts would be represented by "3H".

The __Deck__ class should implement the following methods:

- __shuffle()__: This method shuffles the cards randomly, in place. You may use the __random.shuffle()__ method to do this.

- __deal(n)__: This method removes and returns the last __n__ cards from the deck in a list. If the deck does not contain enough cards it returns all the cards in the deck.

- __sort_by_suit()__: This method sorts the cards by suit, placing all the hearts first, diamonds second, clubs third and spades last. The order within each suit (i.e. the card values) does not matter. This method should sort the cards in place, it does not return anything.

- __copy()__: This method returns a new __Deck__ object that is a copy of the current deck. Any modifications made to the new __Deck__ object should not affect the __Deck__ object that was copied.

- __get_cards()__: This method returns all the cards in the deck in a list. Any modifications to the returned list should not change the __Deck__ object.

- __\_\_len()\_\_()__: This method returns the number of the cards in the __Deck__.

The deck should always start with exactly __52__ cards that are distibuted across __4__ suits and __13__ values where there are no duplicate cards.

See below for an example of how the __Deck__ class should behave:

    >>> d = Deck()
    >>> d.shuffle()
    >>> d.deal(3)
    ["AS", "2H", "4D"]
    >>> d.contains("4D")
    False
    >>> d.sort_by_suit()
    >>> d.deal(3)
    ["2S", "5S", "JS"]
    >>> len(d)
    46

""""""

# My Solution for Exercise Four -

""""""

from random import shuffle

class Deck:

    values = [str(i) for i in range(2, 11)] + ["J", "Q", "K", "A"]
    suits = ["D", "H", "C", "S"]  # Diamond, Heart, Club, Spade

    def __init__(self):
        self.deck = []
        self.fill_deck()
       

    def fill_deck(self):
        for value in Deck.values:
            for suit in Deck.suits:
                self.deck.append(value + suit)

    def shuffle(self):
        shuffle(self.deck)

    def deal(self, n):
        cards_dealt = []
        number_of_cards_to_deal = n
        number_of_cards_dealt = 0

        while number_of_cards_dealt < number_of_cards_to_deal:
            if len(self.deck) == 0:
                return cards_dealt
            
            cards_dealt.append(self.deck.pop())
            number_of_cards_dealt += 1

        return cards_dealt
    
    def sort_by_suit(self):  # This method was tricky
        cards_by_suit = {"H": [], "D": [], "C": [], "S": []}

        for card in self.deck:  # build lists of cards based on their suit, which is at index -1
            suit = card[-1]
            cards_by_suit[suit].append(card)

        self.deck = (  #put the lists back in the order we want
            cards_by_suit["H"] +
            cards_by_suit["D"] +
            cards_by_suit["C"] +
            cards_by_suit["S"]
        )

    def contains(self, card):
        if card in self.deck:
            return True
        return False

    def copy(self):
        new_deck = Deck()
        new_deck.deck = self.get_cards()
        return new_deck
    
    def get_cards(self):
        return self.deck[:]
    
    def __len__(self):
        return len(self.deck)

""""""

# """Exercise Five"""

""""""

<u>FileSystem Implementation<u>

In this question, implement a very simplistic __FileSystem__ works. A __FileSystem__ starts empty with only a root node which will always be a directory.

A __FileSystem__ is a tree-like structure composed of nodes, each of which is either a __File__ or __Directory__.

Files are simplest and only have __name__ and __contents__ as attributes; which correspond to the name of the file and its contents, respectively. Files also have a __write__ method, which sets the contents of that file to the argument passed in. Additionally, files override the \__len__ dunder method which returns the number of characters in the contents of that file.

Directories have a __name__ and a __children__ attribute. __children__ is a dictionary that stores the name of its children nodes as keys, and the nodes themselves as the values of that dictionary. Directories also have the __add__ and __delete__ methods which are used to add or delete nodes from its __children__ dictionary.

For convenience, the \__str__ methods of each class have been overridden so that one may debug the FileSystem more easily.

The task is to implement the following mwthods on the __FileSystem__ class:

- __create_directory(path)__: This method should create a __Directory__ inside the __FileSystem__ at the location specified. For instance, __create_directory("/dir1")__ should create a directory as a child of the root of the filesystem called __"dir1"__. Running __create_directory("/dir1/dir2")__ should create another, __dir2__, inside the one that was just created. If the path is malformed or the operation is impossible, it should raise a __ValueError__.

- 

""""""

[course-site]: https://www.programmingexpert.io/index