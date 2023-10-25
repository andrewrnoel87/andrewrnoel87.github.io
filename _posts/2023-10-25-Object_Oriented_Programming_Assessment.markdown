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

__Inventory Class__

Write an Inventory class, as defined below, that handles the management of inventory for a company. All instances of this class should be initialized by passing an integer value named max_capacity that indicates the maximum number of items that can be stored in inventory. The Inventory class will need to store items that are represented by a _name_, _price_ and _quantity_.

The class should implement the following methods.

- __add_item(name, price, quantity)__: This method should add an item to the inventory and return __True__ if it was successfully added. If adding an item results in the inventory being over apacity your method should return __False__ and omit adding this item to the inventory. Additionally, if an item with the passed _name_ already exists in inventory this method should return __False__ to indicate the item could not be added.

- __delete_item(name)__: This method should delete an item from the inventory and return __True__ if the item was successfully deleted. If there is no item with the passed _name_ this method should return __False__.

- __get_most_stocked_item()__: This method should return the name of the item that has the highest quantity in the inventory, and return __None__ if there are no items in the inventory. You may assume there will always be exactly one item with the largest quantity, except for the case where the inventory is empty.

- __get_items_in_price_range(min_price, max_price)__: This method should return a list of the names of items that have a price within the specified range(inclusively).

Note: You may assume all input/arguments to your class will be valid and the correct types. For example, the max_capacity will always be greater than or equal to 0 and a valid integer. 

See below for an example of how the Inventory class should behave:

    >>> i = Inventory(4)
    >>> i.add_item('Chocolate', 4.99, 1)
    True
    >>> i.add_item('Cereal', 6.99, 1)
    True
    >>> i.add_item('Milk', 3.99, 2)
    True
    >>> i.add_item('Butter', 2.99, 1)
    False
    >>> i.delete_item('Bread')
    False
    >>> i.delete_item('Cereal')
    True
    >>> i.get_items_in_price_range(4.50, 6.50)
    ['Chocolate']

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
            self.items[name] = {'name': name, 'price': price, 'quantity': quantity}  # Creating a nested dictionary to hold our items
            self.item_count += quantity
            return True 
        
        return False

    def delete_item(self, name: str):
        if name not in self.items:
            return False
      
        self.item_count -= self.items[name]['quantity']  # need to update our item_count
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

[course-site]: https://www.programmingexpert.io/index