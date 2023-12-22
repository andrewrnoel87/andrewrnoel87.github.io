---
layout: default
title:  "Advanced Programming Assessment Part 5"
date:   2023-12-22 10:06:00 -0400
categories: blog
---
Today, I covered the __Advanced Programming Assessment__ from the [programmingexpert.io][course-site] course.

""""""

# Exercise Five - Asynchronous Fetcher

""""""

Write a __BatchFetcher__ class that is meant to fetch lots of records from a database very quickly.

The constructor takes in a __database__ object that has an __async__ method called __async_fetch__. This method takes a record identifier (or __record_id__) and returns whatever the database has in storage for that record.

__BatchFetcher__ should implement the async method __fetch_records__, which takes in a list, __recod_ids__, and should return the list of records corresponding to those __record_ids__.

Sample:

    1 | >>> fetcher = BatchFetcher(database)
    2 | >>> fetcher.fetch_records(["A", "B", "C"])
    3 | [{"data": "data of record A"}, {"data": "data of record B"}, {"data": "data of record C"}]

""""""

My Solution for Exercise Five:

    import asyncio

    class BatchFetcher:
        # The `database` has an `async_fetch` method.
        # This method takes in a record id and returns a record.

        def __init__(self, database):
            self.database = database
      
        async def fetch_records(self, record_ids):
            list_of_records = []
            for record in record_ids:
                record_id = self.database.async_fetch(record)  #  creates coroutines
                list_of_records.append(record_id)

            return await asyncio.gather(*list_of_records) # wraps coroutines in a task and returns results in a list

Alternate Solution Provided:

    # Copyright © 2022 AlgoExpert LLC. All rights reserved.

    import asyncio


    class BatchFetcher:
        def __init__(self, database):
            self.database = database

        async def fetch_records(self, record_ids):
            pending_records = []
            for record_id in record_ids:
                task = asyncio.create_task(self.database.async_fetch(record_id))
                pending_records.append(task)

            records = []
            for pending_record in pending_records:
                records.append(await pending_record)
            return records

""""""

[course-site]: https://www.programmingexpert.io/index