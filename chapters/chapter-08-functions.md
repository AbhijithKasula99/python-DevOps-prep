# Chapter 8 — Functions

Based on *Python Crash Course, 3rd Edition* by Eric Matthes.

## Functions

Functions are named blocks of code designed to do one specific job. They let us reuse code.

```python
def greet_user():
    print("Hello!")

greet_user()
```

## Parameters and Arguments

A parameter is a variable in the function definition. An argument is the actual value passed when calling the function.

```python
def greet_user(username):
    print(f"Hello, {username}!")

greet_user("Abhijith")
```

## Positional Arguments

Arguments are matched to parameters according to their position.

```python
def describe_person(name, age):
    print(f"name: {name}")
    print(f"age: {age}")

describe_person("Abhijith", 27)
```

## Keyword Arguments

Arguments can be passed using parameter names.

```python
describe_person(age=27, name="Abhijith")
```

## Default Values

A parameter can have a default value.

```python
def describe_person(name, age=0):
    print(f"name: {name}")
    print(f"age: {age}")

describe_person("Abhijith")
```

## Passing Lists to Functions

Lists can be passed to functions.

```python
def greet_users(names):
    for name in names:
        print(f"Hello, {name}")

users = ["Abhijith", "Alice", "Brian"]
greet_users(users)
```

To pass a copy so the original list is unchanged:

```python
greet_users(users[:])
```

## Returning Values

`return` sends a value back to the code that called the function.

```python
def get_formatted_name(first_name, last_name):
    full_name = f"{first_name} {last_name}"
    return full_name

name = get_formatted_name("Abhijith", "Kasula")
print(name)
```

A function without a `return` statement returns `None`.

## Optional Parameters

```python
def get_formatted_name(first_name, last_name, middle_name=""):
    if middle_name:
        full_name = f"{first_name} {middle_name} {last_name}"
    else:
        full_name = f"{first_name} {last_name}"
    return full_name
```

## Returning Dictionaries

```python
def build_person(first_name, last_name, age=None):
    if age:
        person = {"first": first_name, "last": last_name, "age": age}
        return person
    else:
        person = {"first": first_name, "last": last_name}
        return person
```

## `*args`

`*args` collects an arbitrary number of positional arguments into a tuple.

```python
def make_pizza(*toppings):
    for topping in toppings:
        print(f"Adding {topping}")
```

A regular parameter can come before `*args`:

```python
def make_pizza(size, *toppings):
    print(f"Making a {size}-inch pizza.")
    for topping in toppings:
        print(f"Adding {topping}")
```

A list can be unpacked into separate arguments with `*`:

```python
ing = ["Egg", "Lettuce", "Cheese", "Honey Mustard"]
make_sandwich(*ing)
```

## `**kwargs`

`**kwargs` collects an arbitrary number of keyword arguments into a dictionary.

```python
def build_profile(first, last, **user_info):
    user_info["first"] = first
    user_info["last"] = last
    return user_info
```

## Modules

A module is a Python file containing reusable code that can be imported into another program.

```python
from pizza import make_pizza
```

Other import styles practiced:

```python
import pizza
from pizza import make_pizza, make_drink
from pizza import make_pizza as mp
import pizza as p
```

## Docstrings

A docstring gives a short description of what a function does.

```python
def make_pizza(size, *toppings):
    """Summarize the pizza we're about to make."""
```

## Exercises Completed

8-1 through 8-17, including functions, arguments, lists, return values, arbitrary arguments, modules, imports, and styling.

## Interview Notes

- **Parameter vs argument:** parameter is defined in the function; argument is the actual value passed during the call.
- **`return` vs `print()`:** `print()` displays a value; `return` sends a value back to the caller.
- **No `return`:** the function returns `None`.
- **Positional vs keyword arguments:** positional arguments are matched by position; keyword arguments use parameter names.
- **`*args`:** arbitrary positional arguments collected into a tuple.
- **`**kwargs`:** arbitrary keyword arguments collected into a dictionary.
- **`messages[:]`:** passes a copy so the original list is not altered.
- **Modules:** store reusable code so it can be imported instead of rewritten.
- **Docstrings:** briefly describe what a function does.
- **Functions:** let us define code once and reuse it, making programs easier to write, read, test, and fix.

**Chapter 8 complete.**
