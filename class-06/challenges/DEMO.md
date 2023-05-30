# Ops Challenge - Bash in Python

## Demo Code

The demo code below introduces concepts necessary to complete the challenge.

```python
#!/usr/bin/env python3
# the shebang line instructs the system to use the env command to locate the python3 interpreter and execute the script with it

# How to print to terminal
print("Hello World!")

# How to declare a variable
greeting = "Welcome to Python!"

# How to call a variable
print(greeting)

# MODULES
# Python provides a rich ecosystem of built-in and third-party modules that extend the language's capabilities and offer ready-to-use functionality for various tasks.
# In Python, a module is a file containing Python code that defines functions, classes, and variables that can be reused in other Python programs.
# A module can be as simple as a single Python file or a collection of related Python files organized within a directory.

import os
# The os module in Python is a built-in module that provides a way to interact with the operating system.
# It gives you Python code that is capable of interacting with the underlying operating system, enabling you to perform tasks related to file management, process handling, environment manipulation, and system information retrieval.

# The `os.system()` function in Python executes a shell command and returns the exit status of the command as an integer value.

# you can use os.system to execute the Bash command
os.system("ls")

# or assign the output to a variable
list = os.system("ls")
user = os.system("whoami")

# if you print the variable, you get a 0 or a 1
print(list)
print(user)
# The exit status represents the result of the executed command.
# Typically, a value of 0 indicates successful execution, while a non-zero value indicates an error or failure.
# The specific meaning of the exit status can vary depending on the command being executed.

# In order to capture the output of the os.system function, you can append the output to a new file.
os.system("ls > list.txt")
os.system("whoami > user.txt")

# a for loop in python
# pseudocode: for iterable in list:
# `for` and `in` are reserved words in Python
for file in ["list.txt", "user.txt"]:

  with open(file, "r") as f:
  # `file` is the filename you want to open
  # `r` specifies "read mode" indicating that the file will be opened for the purpose of reading its contents.
  # `as f` assigns the file object to the variable `f`. This allows you to refer to the file object within the indented block of code following the `with` statement.

    # Then read the contents of the file
    output = f.read()
    # read() is a method of the file object that reads the entire contents of the file as a string.

    # Lastly, we print the output to the console using an f-string
    print(f"\n🚩Command output: {output}")
    # f-string is short for "formatted string literals,"
    # It is a Python 3.6 feature that provides a convenient way to dynamically include the values of variables, expressions, or function calls directly within a string, making string formatting more readable.

    # If you wish to delete the file
    os.remove(file)
    print(f"Deleted {file} file 👍 \n")

```
