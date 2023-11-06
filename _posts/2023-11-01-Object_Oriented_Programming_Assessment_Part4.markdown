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

class FileSystem:

    def __init__(self):
        self.root = Directory("/")

    def create_directory(self, path):

        before_last_node, new_directory_name = FileSystem.parse_node_path(self, path)
        
        new_directory = Directory(new_directory_name)  # create a new directory

        before_last_node.add_node(new_directory)  # add new directory as a child of the before_last_node

    def create_file(self, path, contents):

        before_last_node, new_file_name = FileSystem.parse_node_path(self, path)
        
        new_file = File(new_file_name)  # Create a new file
        new_file.write_contents(contents)  # Write the contents to the file

        before_last_node.add_node(new_file)  # Add the file node to the direct parent directory node

    def read_file(self, path):

        before_last_node, file_name = FileSystem.parse_node_path(self, path)

        if file_name not in before_last_node.children:  # make sure file_name is a child of before_last_node
            raise ValueError(f"File not found: {file_name}.")

        return before_last_node.children[file_name].contents

    def delete_directory_or_file(self, path):

        before_last_node, node_to_delete_name = FileSystem.parse_node_path(self, path)

        if node_to_delete_name not in before_last_node.children:  # make sure node_to_delete_name is a child of before_last_node
            raise ValueError(f"File not found: {node_to_delete_name}.")
        
        before_last_node.delete_node(node_to_delete_name)

    def size(self):

        size = 0
        nodes = [self.root]
        while len(nodes) > 0:
            current_node = nodes.pop()
            if isinstance(current_node, Directory):  # if the current_node is a Directory add its children to the list of nodes we are checking for files
                children = list(current_node.children.values())  # make a list of nodes out of the current_node's children. The children's values are nodes.
                nodes.extend(children)  # adding the children list to the node list
                continue
            if isinstance(current_node, File):
                size += len(current_node)  # if the current_node is a File add its len to the size
        return size

    def __str__(self):
        return f"*** FileSystem ***\n" + self.root.__str__() + "\n***"
    
    @staticmethod
    def _validate_path(path):
        if not path.startswith("/"):
            raise ValueError("Path should start with `/`.")
        
    def parse_node_path(self, path):  # returns the node before the node we are adding and the name of the new node

        FileSystem._validate_path(path)

        path_node_names = path[1:].split("/")  # Take the path string, skip the first element which should be a /, and split the string by /'s, return the list
        middle_node_names = path_node_names[:-1]  # The node names except the last one
        new_node_name = path_node_names[-1]  # The last node name, which is the new one we are creating

        before_last_node = self._find_bottom_node(middle_node_names)  # Get the node before the node you are adding

        if not isinstance(before_last_node, Directory):  # make sure before_last_node is a Directory
            raise ValueError(f"{before_last_node.name} isn't a directory.")
        
        return before_last_node, new_node_name


    def _find_bottom_node(self, node_names):

        current_node = self.root
        for node_name in node_names:
            if not isinstance(current_node, Directory):  # Make sure the current node is a directory
                raise ValueError(f"{current_node.name} isn't a directory.")
            
            if node_name not in current_node.children:  # make sure the node_name is a child of the current_node
                raise ValueError(f"Node not found: {node_name}.")
            
            current_node = current_node.children[node_name]  # move to the next node

        return current_node
            
class Node:

    def __init__(self, name):
        self.name = name

    def __str__(self):
        return f"{self.name} ({type(self).__name__})"


class Directory(Node):

    def __init__(self, name):
        super().__init__(name)
        self.children = {}

    def add_node(self, node):
        self.children[node.name] = node

    def delete_node(self, name):
        del self.children[name]

    def __str__(self):
        string = super().__str__()

        children_strings = []
        for child in list(self.children.values()):
            child_string = child.__str__().rstrip()
            children_strings.append(child_string)

        children_combined_string = indent("\n".join(children_strings), 2)
        string += "\n" + children_combined_string.rstrip()
        return string


class File(Node):

    def __init__(self, name):
        super().__init__(name)
        self.contents = ""

    def write_contents(self, contents):
        self.contents = contents

    def __len__(self):
        return len(self.contents)

    def __str__(self):
        return super().__str__() + f" | {len(self)} characters"


def indent(string, number_of_spaces):

    spaces = " " * number_of_spaces
    lines = string.split("\n")
    indented_lines = [spaces + line for line in lines]
    return "\n".join(indented_lines)

""""""

[course-site]: https://www.programmingexpert.io/index