---
layout: default
title:  "Advanced Programming Assessment Part 4"
date:   2023-12-20 10:06:00 -0400
categories: blog
---
Today, I covered the __Advanced Programming Assessment__ from the [programmingexpert.io][course-site] course.

""""""

# Exercise Four - Thread Safe Counter

""""""

Write a __WordCounter__ class that is meant to be able to count words in large texts, so that a user of that class can quickly calculate how many times a specific word occurs in a string.

__WordCounter__ should implement the following methods.

- __process_text(text)__ should take in a string, __text__, and update the internal attributes of __WordCounter__ in a thread-safe manner. You may assume naively that __text.split(" ")__ is good enough to return the list of words in the passed __text__.

- __get_word_count(word)__ should take in a string, __word__, and check how many times that word has been seen in all the texts that this __WordCounter__ has processed. If this word has never been seen, you should return __0__.

NOTE: This class must be thread-safe; meaning that many threads should be able to use the __WordCounter__ at the same time, and the calculations must remain accurate as if only a single thread was using the instance of __WordCounter__.

NOTE: Do __not__ use the __Counter__ class of the __collections__ standard library.

Sample:

    1 | >>> wc = WordCounter()
    2 | >>> wc.process_text("the cat is in the bag")
    3 | >>> wc.get_word_count("the")
    4 | 2
    5 | >>> wc.get_word_count("bag")
    6 | 1
    7 | >>> wc.get_word_count("dog")
    8 | 0

""""""

My Solution for Exercise Four:

    import threading

    class WordCounter:
        def __init__(self):
            self.lock = threading.Lock()
            self.word_counts = {}

        def process_text(self, text):
            for word in text.split(" "):
                self.lock.acquire()
                self.word_counts[word] = self.word_counts.get(word, 0) + 1
                self.lock.release()

        def get_word_count(self, word):
            self.lock.acquire()
            count = self.word_counts.get(word, 0)  # word is the key to the dictionary with the counts
            self.lock.release()
            return count

""""""

[course-site]: https://www.programmingexpert.io/index