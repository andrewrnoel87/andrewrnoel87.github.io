---
layout: default
title:  "Object-Oriented Programming Assessment Part 1"
date:   2023-10-25 14:28:00 -0400
categories: blog
---
Today, I covered the __Object-Oriented Programming Assessment__ from the [programmingexpert.io][course-site] course.

""""""

# """Exercise One"""

""""""

""""""

- My Solution for Exercise One -

""""""

class Inventory:

    def __init__(self, max_capacity: int):
        self.max_capacity = max_capacity
        self.item_count = 0
        self.items = {}

    def add_item(self, name: str, price: float, quantity: int):
        if (self.item_count + quantity <= self.max_capacity) and (name not in self.items):
            self.items[name] = {'name': name, 'price': price, 'quantity': quantity}
            self.item_count += quantity
            return True 
        
        return False

    def delete_item(self, name: str):
        if name not in self.items:
            return False
      
        self.item_count -= self.items[name]['quantity']
        del self.items[name]
        return True
        
    def get_items_in_price_range(self, min_price: float, max_price: float):
        items_in_price_range = []

        for name in self.items:
            if min_price <= self.items[name]['price'] <= max_price:
                items_in_price_range.append(name)

        return items_in_price_range

    def get_most_stocked_item(self):
        most_stocked_item = None 
        most_stocked_item_qty = 0
       
        for name in self.items:
            if self.items[name]['quantity'] > most_stocked_item_qty:
                most_stocked_item = name
                most_stocked_item_qty = self.items[name]['quantity']

        return most_stocked_item

""""""

""""""

[course-site]: https://www.programmingexpert.io/index