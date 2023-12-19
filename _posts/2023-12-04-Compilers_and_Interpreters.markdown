---
layout: default
title:  "Compilers and Interpreters"
date:   2023-12-04 11:05:00 -0400
categories: blog
---

Today, I cover __Compilers and Interpreters__ from the [programmingexpert.io][course-site] course.

""""""

# Key Terms

<u>Compiler<u>

A __compiler__ is a program that takes in source code(the code that we, humans, write) and transforms it into code that a machine can interpret (bytecode) or execute (binary code).

<u>Interpreter<u>

An __interpreter__ is a program that is capable of translating code (typically bytecode) into machine code that can be ran and executed by the CPU(central processing unit). Python code is first compiled into bytecode, that bytecode is then passed to the interpreter where it is interpreted and executed.

<u>Source Code<u>

The __source code__ is the code that the programmers write and read.

<u>Bytecode<u>

__Bytecode__ is program code that has been complied from source code into a lower level language that can be understood by an interpreter.

""""""

# Notes

- Python code in a __.py__ file is an example of __source code__. Source code is the code programmers write in high-level programming languages like Python. It is often very close to English in structure and syntax and is later translated into other forms of code that allow it to be executed by a computer.

- Although Python is known as an interpreted language it does still need to be compiled into bytecode to become executable.

- An interpreter is a virtual machine that translates code into target machine code during execution.

- The first step that occurs when Python is ran is the following. The compiler translates Python source code into bytecode that is then read and executed by the interpreter. Before the interpreter can execute any code it must first be translated into bytecode. The compiler translates Python source code into bytecode which is lower-level code that can be interpreted by the interpreter. The interpreter then executes bytecode in it's execution environment.

- A compiler or interpreter is simply an implementation of the Python programming language. Many different compilers and interpreters exist that have slight differences in code compilation and run-time efficiency. Some popular compilers and interpreters include: PyPy, CPython, JYthon, IronPython, Brython, Nuitka and PyJS.

""""""

[course-site]: https://www.programmingexpert.io/index