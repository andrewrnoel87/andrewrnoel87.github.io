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

pass

""""""

[course-site]: https://www.programmingexpert.io/index