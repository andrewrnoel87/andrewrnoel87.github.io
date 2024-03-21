---
layout: default
title:  "Users and Sudo"
date:   2024-01-16 11:05:00 -0400
categories: blog
---

Today, I cover __Users and Sudo__ from the [programmingexpert.io][course-site] course.

""""""

# Notes

- Specific to a Linux operating system.

- A __User__ is simply someone who is using your operating system.

- Users exist to manage different people using the operating system and to give permissions to different people based on what they need to be able to do.

- On a Linux machine, the first user that is created is the __root user__.

- The __root user__ is a kind of __Super Admin__. It is the administrator account. It is known as a super user. It can do everything by default.

- When you create another user, by default, they are not given permission to do anything more than interact with their home directory.

- You can make other users into __super users__ with the __sudo__ command. Example: localhost:/$ sudo ls root

- sudo does not work on windows because permissions are handled differently. If denied on Windows, run GitBash as an administrator. Mac should have the sudo command.

""""""

# Exercise One

""""""

What does the command __sudo__ stand for?

<u>Answer<u>

- Superuser Do

<u>Explanation<u>

__sudo__ is used as a prefix before commands requiring administator privellages.

On Linux based operating systems to use the __sudo__ command your user must be listed in the __/etc/sudoers__ file or be the root user.

""""""

# Exercise Two

""""""

On a Linux based operating system what is the _root_ user?

<u>Answer<u>

- A user that by default has access to all commands.

<u>Explanation<u>

The root user is like the administator user on Mac and Windows based computers. It is the user with the highest privilege level on a Linux machine. By default it has access to all commands and can create new users as well as give them permissions to use commands like __sudo__.

""""""

[course-site]: https://www.programmingexpert.io/index