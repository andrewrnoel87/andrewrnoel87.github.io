---
layout: default
title:  "Modules and Packages"
date:   2023-11-13 14:14:00 -0400
categories: blog
---

Today, I cover __Modules and Packages__ from the [programmingexpert.io][course-site] course.

""""""

# Key Terms

<u>Main Module<u>

In Python, the __main__ module is the one that is invoked or run directly. Python will automatically set the __\_\_name\_\___ variable of that module to the string __"\_\_main\_\_"__. All modules that are imported from that main package will have their own values for the __\_\_name\_\___ variable.

When writing your modules in Python, it is best practice to run some parts of the code conditionally based on that __\_\_name\_\___ variable:

    if __name__ == "__main__":
        print("This code will only run if this is the main package!")

<u>Module<u>

In Python, a __module__ is simply any Python file (something ending in __.py__). Modules provide a way to split code into multiple files and make programs easier to understand. One Python module is able to import code from another Python module.

<u>Package<u>

A Python __package__ is simply a directory/folder that contains a special file named __\_\_init\_\_.py__, and typically a collection of other Python modules. Packages provide a way to organize Python modules. When importing a Python package the code inside of the __\_\_init\_\_.py__ file will run once.

""""""

# Notes

- A Python package is a collection of Python modules where Python modules are individual Python files. Modules can import other modules and packages and packages may contain initialization code that imports other packages or modules.

- Python packages are any directories that contain a __\_\_init\_\_.py__ file, packages may be nested in other packages.

- __print(\_\_name\_\_)__ will print out the name of the module you are in.

- Imported modules will _not_ be named \_\_main\_\_.

- When naming modules it is best practice to use lower case and snake_case. Do not use special characters or spaces. Avoid naming a module the same as a built-in module.

- When you do an __import__, the imported code is ran once.

- By convention, __import__ statements should be located at the top of a file.

- __Avoid__ circular imports.

- __\_\_init\_\_.py__ has code to run when the package is imported.

- When we specify the direct import path, it is an __absolute import__. Absolute imports are prefered over relative imports.

- __Relative imports__ are based on where you are when you import. Example: __from . import module_name__. This says from the current package/directory import module_name.

""""""

# Import Examples

""""""

Importing with modules in the same directory:

    import module_name  # will allow module_name.function() to work

Importing a module and changing the reference to that module:

    import module_name as m  # will allow m.function() to work

- This is useful if the module name is long or already in use.

Multiple imports:

    import module_name as m
    import module_name  
    
    # will allow module_name.function() and m.function() to both work

Import specific objects:

    from module_name import foo, bar

    # will allow foo() and/or bar() to work

Import everything:

    from module_or_package import *

    # this is usually bad practice if you do not need everything, but it does import everything from the module or package
    



""""""

# Importing Functions Exercise

""""""

Examine the following directory structure:

    x/
        __init__.py
        main.py <- you are here
        a/
            __init__.py
            b/
                __init__.py
                c.py

If you wanted to import a function named __foo__ from the __c.py__ file and you were in the __main.py__ file what would your import statement look like?

__from a.b.c import foo__

- In Python, when __from__ is used it always appears before __import__. In this case we are importing __foo__ from the __c__ module in the __b__ package which is in the __a__ package.

""""""

# Importing Packages, Modules And Functions Exercise

""""""

Examine the following directory structure and file contents:

    x/
        main.py <- you are here
        a/
            __init__.py
            b.py

\# x/main.py:

    import a

\# x/a/\_\_init\_\_.py:

    from .b import foo

\# x/a/b.py:

    def foo(): 
        print("a")

    print("b")
    if __name__ == "__main__":
        foo()

What will be printed when the __main.py__ file is run?

__b__

- In Python, when you import a package the code inside of the package's __\_\_init\_\_.py__ file runs once. This means when we import the a package the line __from .b import foo__ will run. Similarly to packages, when you import a module the code inside of that module runs once. That means when we import __b__ from the __x/a/\_\_init\_\_.py__ file the line __print("b")__ will run. The __if \_\_name\_\_ == "\_\_main\_\_":__ will also be ran but the condition  __\_\_name\_\_ == "\_\_main\_\_"__ will be __False__, meaning we will not call the foo() function. The reason this condition will be __False__ is because we did not direclty run this file, we imported it.

""""""

[course-site]: https://www.programmingexpert.io/index