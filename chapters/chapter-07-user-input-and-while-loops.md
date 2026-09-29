# Chapter 7 — User Input and while Loops

## Overview

Chapter 7 covers how Python programs can accept input from users and use `while` loops to repeat code while a condition remains true.

## 1. Getting Input with `input()`

`input()` pauses the program, waits for the user to enter text, and stores that text in a variable.

```python
name = input("What is your name? ")
print(f"Hello, {name}!")
```

A prompt can be built across multiple lines:

```python
prompt = "If you share your name, we can personalize the messages you see."
prompt += "\nWhat is your first name? "
name = input(prompt)
print(f"\nHello, {name}!")
```

## 2. Numerical Input with `int()`

`input()` returns text. Use `int()` when the entered value needs to be treated as an integer.

```python
age = input("How old are you? ")
age = int(age)
age += 5
print(age)
```

A shorter form is also possible:

```python
age = int(input("How old are you? "))
```

## 3. The Modulo Operator `%`

The modulo operator returns the remainder of a division.

```python
num = int(input("Please enter a number: "))
op = num % 10
print(op)
```

For example, `27 % 10` produces `7`.

Modulo can be used to determine whether a number is a multiple of another number:

```python
if num % 10 == 0:
    print(f"{num} is a multiple of 10.")
```

# while Loops

A `while` loop continues executing while its condition is true.

```python
current_number = 1

while current_number <= 5:
    print(current_number)
    current_number += 1
```

The variable controlling the condition must change appropriately, otherwise the loop can become infinite.

## 4. Quit Values

A loop can continue until the user enters a specific value.

```python
message = ""

while message != "quit":
    message = input("Message: ")
```

The initial value is important because Python needs `message` to exist before it evaluates the `while` condition.

To avoid printing the quit value:

```python
message = ""

while message != "quit":
    message = input("Message: ")

    if message != "quit":
        print(message)
```

String comparisons are case-sensitive. For example, `"Quit"` and `"quit"` are different strings.

## 5. Flags

A flag is a variable used to control whether a loop remains active.

```python
active = True

while active:
    message = input("Message: ")

    if message == "quit":
        active = False
    else:
        print(message)
```

Changing `active` to `False` causes the loop condition to become false.

## 6. `break`

`break` immediately exits the loop.

```python
while True:
    message = input("Message: ")

    if message == "quit":
        break

    print(message)
```

## 7. `continue`

`continue` skips the rest of the current iteration and returns to the beginning of the loop.

```python
current_number = 0

while current_number < 10:
    current_number += 1

    if current_number % 2 == 0:
        continue

    print(current_number)
```

Output:

```text
1
3
5
7
9
```

## 8. Infinite Loops

A loop becomes infinite when its condition never becomes false.

```python
x = 1

while x <= 5:
    print(x)
```

`x` never changes, so the condition remains true and `1` keeps printing.

A running infinite loop can be interrupted with `Ctrl+C`, producing `KeyboardInterrupt`.

# while Loops with Lists and Dictionaries

The chapter shows using a `while` loop when modifying a list as you work through it.

## 9. Moving Items Between Lists

```python
unconfirmed_users = ["Alice", "Brian", "Candace"]
confirmed_users = []

while unconfirmed_users:
    current_user = unconfirmed_users.pop()
    confirmed_users.append(current_user)

print(confirmed_users)
```

The condition `while unconfirmed_users:` continues while the list contains items.

## 10. Removing All Occurrences from a List

```python
pets = ["dog", "cat", "dog", "cat", "cat"]

while "cat" in pets:
    pets.remove("cat")

print(pets)
```

Output:

```text
['dog', 'dog']
```

## 11. Polling with a Dictionary

A `while` loop can collect responses from multiple users.

```python
responses = {}

polling_active = True

while polling_active:
    name = input("What is your name? ")
    response = input("Which mountain would you like to climb someday? ")

    responses[name] = response

    repeat = input("Would you like to let another person respond? (yes/no) ")

    if repeat == "no":
        polling_active = False
```

The dictionary stores each person's response, and the flag controls when polling ends.

# Chapter 7 Exercises

## 7-1 Rental Car

Ask the user what kind of rental car they would like and print a response.

```python
ask = input("What kind of rental car would you like? ")
print(f"Let me see if I can find you a {ask}.")
```

## 7-2 Restaurant Seating

Ask how many people are in the dinner group. If more than eight people are waiting, otherwise indicate that the table is ready.

```python
ask = int(input("Table for how many? "))

if ask > 8:
    print("Unfortunately, you might have to wait for the table!")
else:
    print("Table is ready!")
```

## 7-3 Multiples of Ten

```python
ask = int(input("Enter a number: "))

if ask % 10 == 0:
    print(f"{ask} is a multiple of 10.")
else:
    print(f"{ask} is not a multiple of 10.")
```

## 7-4 Pizza Toppings

Keep asking for pizza toppings until the user enters `"quit"`.

```python
prompt = "Enter a pizza topping: "
valid = True

while valid:
    top = input(prompt)

    if top == "quit":
        valid = False
    else:
        print(f"Added, {top}!")
```

## 7-5 Movie Tickets

Ask for the user's age and determine the ticket price according to the exercise requirements:

- Under 3: free
- 3–12: $10
- Over 12: $15

The loop should provide a way for the user to stop entering ages.

## 7-6 Three Exits

Practice different ways of ending a loop:

- A quit value
- A flag
- `break`

## 7-7 Infinity

```python
while True:
    print("This is an infinite loop.")
```

Interrupt it with `Ctrl+C`.

# Interview Notes

### `while` vs `for`

A `while` loop keeps executing as long as its condition is true. A `for` loop iterates over items in a sequence or range.

### Infinite `while` loop

If the condition never becomes false, the loop continues indefinitely.

### `break`

Immediately exits the loop.

### `continue`

Skips the remaining code in the current iteration and returns to the beginning of the loop.

### Flag

A flag such as `active = True` controls whether a loop continues. Changing it to `False` causes a loop such as `while active:` to stop when its condition is evaluated again.

### Why initialize a loop variable?

For `message = ""` followed by `while message != "quit":`, `message` must already exist before Python evaluates the condition for the first time.

### Modifying lists with `while`

Use a `while` loop when you need to modify a list as you work through it.

# Chapter 7 Completion

Chapter 7 practice covered user input, numerical input, modulo, `while`, quit values, flags, `break`, `continue`, infinite loops, lists with `while`, dictionaries with `while`, polling, exercises 7-1 through 7-7, and interview-style questions.
