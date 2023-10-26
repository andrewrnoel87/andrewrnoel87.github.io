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

[course-site]: https://www.programmingexpert.io/index