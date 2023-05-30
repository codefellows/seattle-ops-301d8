# Ops Challenge - Directory Creation

## Demo Code

The demo code below introduces concepts necessary to complete the challenge.

```python
#!/usr/bin/env python3

# These examples can be accessed at https://www.w3schools.com/python/python_functions.asp

# How to define a function

def my_function():
  print("Hello from a function")

# How to call a function

my_function()

# How to pass arguments into functions

def my_function(fname):
  print(fname + " Refsnes")

my_function("Emil")
my_function("Tobias")
my_function("Linus")

# How to read input (refer to https://www.w3schools.com/python/python_user_input.asp)

username = input("Enter username:")
print("Username is: " + username)

```

## Alternate Demo using a tuple

```python
#!/usr/bin/env python3

# Script Name:              Ops Challenge 07
# Author:                   Hexx King
# Date of last revision:    5/11/23
# Description of purpose:   Functions in Python

# Declaration of functions
def make_a_sandwich(user_name):

  print(f"Hi {user_name}!")

  # Prompt the user to enter sandwich ingredients
  bread = input("What bread do you want on your sandwich? ")
  cheese = input("What cheese do you want on your sandwich? ")
  meat = input("What meat do you want on your sandwich? ")
  vegetables = input("What vegetables do you want on your sandwich? ")
  condiments = input("What condiments do you want on your sandwich? ")

  # initalize a tuple with the sandwich ingredients
  sandwich_ingredients = (bread, cheese, meat, vegetables, condiments)

  print(f"\nThis is {user_name}'s ultimate sandwich: ")
  print("=====")

  # Unpack the tuple in a for loop and print each ingredient
  for bread, cheese, meat, vegetables, condiments in (sandwich_ingredients,):
    print(bread)
    print(cheese)
    print(meat)
    print(vegetables)
    print(condiments)
    print("=====")

# Main
user = input("What is your name? ")
make_a_sandwich(user)
user = input("What is your friend's name? ")
make_a_sandwich(user)

# End


```

Download the [template](TEMPLATE.md) to get started.
