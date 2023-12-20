---
layout: default
title:  "Asynchronous Programming"
date:   2023-12-11 11:05:00 -0400
categories: blog
---

Today, I cover __Asynchronous Programming__ from the [programmingexpert.io][course-site] course.

""""""

# Key Terms

<u>Asynchronous Programming<u>

__Asynchronous programming__ in Python is a programming paradigm that enables better concurrency, that is, multiple threads running concurrently. In Python, __asyncio__ module provides this capability. Multiple tasks can run concurrently on a single thread, which is scheduled on a single CPU core. __Coroutines__ are usually functions with an __async__ definition. __Tasks__ let you run a coroutine in an event loop; that simplifies managing the execution of several coroutines.

<u>Coroutine<u>

__Coroutine__ is any function that has the __async__ keyword before it. It is called a coroutine because it is capable of cooperatively running with other __tasks__ and __coroutines__. It is able to pause its execution in the middle before returning some value and give control to another coroutine. Coroutines can be scheduled as a __task__. That __task__ will need to be __awaited__.

""""""

# Notes

- All coroutines must be __awaited__ in some way.

- In Python, an asynchronous program that does not explicitly define other threads runs in one thread. The async paradigm enables better concurreny and simpler programs and is recommended to use over standard multithreading.

- The most straightforward definition of a coroutine is a function that can suspend its execution and resume later. Coroutines are functions that can yield their control periodically or when in idle to allow other coroutines to run. This is how concurrency is implemented in a single thread.

- The __await__ keyword can only be used inside of a function that is defined with __async__/ a coroutine.

- In asynchronous programming, you no longer need to run code strictly based off of the clock speed of the processor. You setup an event loop.

- An __event loop__ lets you schedule tasks to fun in the future. It allows you to await one block of code before doing another block.

- Async was introduced in Python as an alternative to threading. Async is preferred when applicable because async tends to be more understandable.

- Async code runs in __one__ thread.

- Use the __async__ keyword when you want to define a __coroutine__.

- Only use the __await__ keyword inside an __async__ function.

- The entry point of an async function is __asyncio.run(function_name())__. A coroutine needs to be run with this. This sets up the event loop.

- __Tasks__ and __coroutines__ are __awaitable__.

- __ayncio.gather(*args)__ schedules its arguments as tasks and runs them concurrently.

- Creating a __task__ is known as creating a __future__.

- You can create an __asynchronous generator__ by using an __async for__ keyword.

- You do not get values from __coroutines__ until they are __awaited__.

Async __await__ Example:

    import asyncio

    async def print_something():
        await asyncio.sleep(1)
        print ("something")

    async def main():
        print("main")
        await print_something()
        print("main again")

    asyncio.run(main())

    # output:
    #           main
    #           something
    #           main again

Async __task__ Example:

    import asyncio

    async def print_something():
        await asyncio.sleep(1)
        print ("something")

    async def main():
        print("main")

        task = asyncio.create_task(print_something())

        print("main again")
        await task
        print("awaited")

    asycio.run(main())

    # output:
    #           main
    #           main again
    #           something
    #           awaited

Async awaiting a __returned__ value Example:

    import asyncio

    async def print_something():
        await asyncio.sleep(1)
        print("something")
        return "finished"

    async def main():
        print("main")

        task = asyncio.create_task(print_something())

        print("main again")
        result = await task
        print(result)

    asyncio.run(main())

    # output:
    #           main
    #           main again
    #           something
    #           finished

Async __scheduling__ tasks Example:

    import asyncio

    async def print_values(values, delay):
        for item in values:
            print(item)
            await asyncio.sleep(delay)

    async def main():
        task1 = asyncio.create_task(print_values([1, 3, 5], 0.2))
        task2 = asyncio.create_task(print_values([2, 4], 0.3))

        await task1
        await task2

    asyncio.run(main())

    # output:
    #           1
    #           2
    #           3
    #           4
    #           5

""""""

# Exercise One - Add One Asynchronous

""""""

Write a function named __add_one__ that accepts a coroutine as a mandatory parameter then calls the coroutine and returns the coroutines return value plus one.

<u>Answer<u>:

    async def add_one(coroutine):
        result = await coroutine()  # 
        return result + 1

""""""

# Exercise Two - Asynchronous Concurrency

""""""

Schedule the existing function to run multiple times such that __lst = [1, 3, 2, 4, 6, 5]__ at the end of the program. Run all the function calls concurrently using __asyncio__. The code should not take longer than __1__ second to run.
     
<u>Answer<u>:

    import asyncio

    async def append_two_values(lst, value1, value2):
        lst.append(value1)
        await asyncio.sleep(0.5)
        lst.append(value2)

    lst = []

    async def main(lst):
        await asyncio.gather(append_two_values(lst, 1, 4), append_two_values(lst, 3, 6), append_two_values(lst, 2, 5))

    asyncio.run(main(lst))

""""""

[course-site]: https://www.programmingexpert.io/index