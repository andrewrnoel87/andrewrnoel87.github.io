---
layout: default
title:  "Introduction to Bash"
date:   2024-01-15 11:05:00 -0400
categories: blog
---

Today, I cover __Introduction to Bash__ from the [programmingexpert.io][course-site] course.

""""""

# Key Terms

<u>CLI<u>

A __CLI__ is a __Command Line Interface__. Command line interfaces are simply programs or software that are designed to be used from the command line and accept textual data or commands.

<u>Shell<u>

A __shell__ is a program that presents a __Command Line Interface (CLI)__ that allows you to interface with a computer using commands.

<u>Bash<u>

__Bash__ is a Unix shell and command language commonly used on Linux operating systems as the default shell.

<u>Git Bash<u>

__Git Bash__ is a source control management system for Windows that provides a bash like interface. It allows you to run Git commands and most bash commands on Windows.

""""""

# Notes

- The __~__ (tilda) represents the home directory of the current user.

- Pressing the __up or down arrow__ cycles through previously typed commands in Bash.

- When using __cd__, __tab__ can be used to autocomplete directory names.

<u>Bash Commands<u>

- __pwd__ stands for Print Working Directory and gives us the path to the current directory we are in.

- __cd__ stands for Change Directory. Example. __cd path/directory_name__ or __cd ../__(takes us to parent directory). One period stands for the current directory. The second period represents the parent directory.

- __ls__ lists the current directory contents alphabetically by default. A directory path/name can be passed to it. Example. __ls ../Users/andrew__

- __clear__ clears the screen.

""""""

# Exercise One

""""""

Given the following directory structure, what does the __pwd__ command output?:

    dir/
        code/
            python_files/
                django_code/
                flask_code/
            javascript_files/
                node_modules/ <- You are here
        home/
            Tim/
            Clement/
            Antoine/
        main/
            tests/
            temp/

<u>Answer<u>

__dir/code/javascript_files/node_modules__

<u>Explanation<u>

__pwd__ stands for "Print Working Directory" and will output the full path to the directory you are currently in.

In this example you are in the __node_modules__ directory which has parent and ancestor (directories above the parent directory) directories. Therefore, __pwd__ will output __dir/code/javascript_files/node_modules__.

""""""

# Exercise Two

""""""

Given the following directory structure, how would you navigate to the __flask_code__ directory using bash commands?:

    dir/
        code/
            python_files/
                django_code/
                flask_code/
            javascript_files/
                node_modules/
        home/
            Tim/
            Clement/
            Antoine/
        main/ <- You are here
            tests/
            temp/

Your current working directory is __main/__.

<u>Answer<u>

__cd ../code/python_files/flask_code__

<u>Explanation<u>

1. The __..__ is important to navigating to the correct directory and indicates that you want to look in the directory above the current directory (the parent directory) for the path that follows. Note that a single __.__ references the current directory.

2. Next you can simply write the path you want to navigate to because __code/python_files/flask_code__ is accessible from the parent directory which you have indicated you want to look for the path from.

""""""

# Exercise Three

""""""

Given the following directory structure, what does the __ls__ command output?:

    home/
        Tim/ <- You are here
            code.py
            code.js
            temp/
                log-10-09-27.txt
            db/
                users.db

Your current working directory is __Tim__.

<u>Answer<u>

__code.js code.py db/ temp/__

<u>Explanation<u>

The __ls__ commands lists all files and directories within the current working directory.

In this example our current working directory is __Tim__ so __ls__ outputs: __code.js code.py db/ temp/__. It only shows us the files and directories within the __Tim__ directory, it does not show us anything nested within other directories. Also note the order of the items; __ls__ outputs files and directories in alphabetical order.

""""""

# Exercise Four

""""""

The command __cd ~__ navigates to what directory?

<u>Answer<u>

The current user's home directory.

<u>Explanation<u>

The __~__ (tilda) represents the home directory of the current user.

Each operating system may define a different location for the users home directory. On a Windows operating system a users home directory will be within __C:/Users__. On a MacOSX operating system a users home directory will be located in __/Users__.

On a Linux based operating system each user will have a different home directory and with the exception of the root user the current users home directory will be located in __/home__.

""""""

[course-site]: https://www.programmingexpert.io/index