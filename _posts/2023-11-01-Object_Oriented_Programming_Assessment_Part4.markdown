---
layout: default
title:  "Object-Oriented Programming Assessment Part 4"
date:   2023-11-01 10:06:00 -0400
categories: blog
---
Today, I covered the __Object-Oriented Programming Assessment__ from the [programmingexpert.io][course-site] course.

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

- __create_file(path, contents)__: This method should create a new file at the desired path, with the contents passed in. If the operation is impossible, it should raise a __ValueError__.

- __read_file(path)__: This method should return the contents of the file at the path parameter. If no such file exists, it should raise a __ValueError__.

- __delete_directory_or_file(path)__: This method should delete the node located at __path__. It should work on files and directories alike, and should raise a __ValueError__ if that file does not exist.

- __size()__: This method should return the number of characters across all files in your filesystem.

- __\_find_bottom_node(node_names)__: This is a private helper method of the __FileSystem__ class that takes in a list of node names and should traverse the filesystem downwards until the last node in the list. For instance, calling this with __["a", "b", "c"]__ should first look for a node __a__ inside the root node of the filesystem, then for a node __b__ inside node __a__, and then return the node __c__ which should be a child of node __b__.

Note: for all methods that accept a __path__ parameter you will need to first validate that path and then parse it. The __path__ will be a string, and from that string you'll need to do one of the following:

- Obtain the directory object used to create a new directory or file inside of.

- Obtain the directory object used to delete a directory or file.

- Obtain the file object to read the contents of.

This is non-trivial because you may need to distinguish between the name of the new node create and the path where this node should be created.

See below for an example of how these classes should behave:

    >>> fs = FileSystem()
    >>> fs.create_directory("/dir1")
    >>> fs.create_file("/file1.txt", "Hello World!")
    >>> print(fs)
    *** FileSystem ***
    / (Directory)
      dir1 (Directory)
      file1.txt (File) | 12 characters
    ***
    >>> fs.delete("/file2.txt")
    ValueError: file2.txt does not exist.

""""""

# My Solution for Exercise Five -

""""""



""""""

[course-site]: https://www.programmingexpert.io/index