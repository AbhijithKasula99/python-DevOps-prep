# Chapter 5 — If Statements

> **Source:** *Python Crash Course, 3rd Edition* — Eric Matthes  
> **Repository:** `python-DevOps-prep`

## 1. Chapter Overview

Conditional logic allows a Python program to make decisions.

```python
if condition:
    # run this code when condition is True
```

Python evaluates a condition and decides which block of code to execute.

---

## 2. Basic `if` Statements

```python
age = 25

if age >= 18:
    print("Adult")
```

Output:

```text
Adult
```

If the condition is false, Python skips the block.

```python
age = 15

if age >= 18:
    print("Adult")
```

Output:

```text
(no output)
```

The colon starts the block, and indentation determines which statements belong to it.

---

## 3. `if-else`

```python
age = 15

if age >= 18:
    print("Adult")
else:
    print("Minor")
```

Output:

```text
Minor
```

Pattern:

```python
if condition:
    # True
else:
    # False
```

---

## 4. `if-elif-else`

```python
age = 12

if age < 4:
    price = 0
elif age < 18:
    price = 10
else:
    price = 20

print(price)
```

Output:

```text
10
```

Python checks an `if / elif / else` chain from top to bottom and executes the **first true branch**.

---

## 5. Multiple Independent `if` Statements

Separate `if` statements are evaluated independently.

```python
age = 25

if age >= 18:
    print("Adult")

if age >= 21:
    print("Can legally drink in the US")

if age >= 65:
    print("Senior")
```

Output:

```text
Adult
Can legally drink in the US
```

Unlike an `if / elif / else` chain, multiple independent `if` statements can all execute.

---

## 6. Comparison Operators

| Operator | Meaning |
|---|---|
| `==` | Equal to |
| `!=` | Not equal to |
| `>` | Greater than |
| `<` | Less than |
| `>=` | Greater than or equal to |
| `<=` | Less than or equal to |

Example:

```python
age = 25

print(age == 25)
print(age != 25)
print(age > 18)
print(age < 18)
print(age >= 25)
print(age <= 25)
```

Output:

```text
True
False
True
False
True
True
```

### `=` vs `==`

```python
a = 2
```

means **assignment**.

```python
a == 2
```

means **comparison**.

Mental model:

> `=` puts a value somewhere.  
> `==` asks a question.

---

## 7. `and`

`and` requires **both** conditions to be true.

```python
age = 25

if age >= 18 and age <= 30:
    print("Age is between 18 and 30")
```

For `age = 35`:

```text
35 >= 18 → True
35 <= 30 → False
True and False → False
```

---

## 8. `or`

`or` requires at least one condition to be true.

```python
age = 35

if age < 18 or age > 30:
    print("Outside the 18–30 range")
```

```text
False or True → True
```

Quick reference:

```text
and → both must be True
or  → at least one must be True
```

---

## 9. `not`

`not` reverses a Boolean value.

```python
has_license = False

if not has_license:
    print("You need a license.")
else:
    print("You have a license.")
```

Output:

```text
You need a license.
```

Because:

```text
not False → True
```

---

## 10. Membership: `in`

Use `in` to check whether a value exists inside a collection.

```python
requested_toppings = ["mushrooms", "onions", "pineapple"]

if "mushrooms" in requested_toppings:
    print("Adding mushrooms.")
```

---

## 11. Membership: `not in`

Use `not in` to check whether a value does **not** exist in a collection.

```python
banned_users = ["admin", "root", "guest"]
username = "abhijith"

if username not in banned_users:
    print("You can log in.")
else:
    print("Access denied.")
```

Output:

```text
You can log in.
```

For `username = "root"`, the `else` branch executes.

---

## 12. Boolean Values and Truthiness

Python can evaluate values in a Boolean context.

```python
print(bool([]))
print(bool(["python"]))
print(bool(""))
print(bool("python"))
print(bool(0))
print(bool(10))
```

Output:

```text
False
True
False
True
False
True
```

Commonly encountered false values include:

- `False`
- `None`
- `0`
- `""` — empty string
- `[]` — empty list

Non-empty collections and strings are treated as true in Boolean contexts.

---

## 13. Checking an Empty List

```python
requested_toppings = []

if requested_toppings:
    print("Adding toppings.")
else:
    print("No toppings requested.")
```

Output:

```text
No toppings requested.
```

---

## 14. `for` Loops with `if`

```python
requested_toppings = ["mushrooms", "onions", "pineapple"]

for topping in requested_toppings:
    if topping == "mushrooms":
        print("Adding mushrooms.")
    else:
        print(f"Adding {topping}.")
```

Output:

```text
Adding mushrooms.
Adding onions.
Adding pineapple.
```

The condition is evaluated once per iteration.

---

## 15. Indentation and Control Flow

```python
for number in range(3):
    print(number)

print("Done")
```

Output:

```text
0
1
2
Done
```

`print(number)` is inside the loop, so it runs three times.

`print("Done")` is outside the loop, so it runs once.

---

## 16. `if / elif` Inside a Loop

```python
users = ["admin", "abhijith", "john", "sarah"]

for user in users:
    if user == "admin":
        print("Hello admin, would you like to see a status report?")
    elif user == "abhijith":
        print("Hello Abhijith, welcome back!")
    else:
        print(f"Hello {user}, thank you for logging in again.")
```

Each iteration gets its own conditional decision.

---

## 17. Ordered Conditions and Boundary Logic

A clean age-range implementation is:

```python
age = 25

if age < 2:
    print("This person is a baby")
elif age < 4:
    print("This person is a toddler")
elif age < 13:
    print("This person is a kid")
elif age < 20:
    print("This person is a teenager")
elif age < 65:
    print("This person is an adult")
else:
    print("This person is an elder")
```

Output:

```text
This person is an adult
```

When Python reaches:

```python
elif age < 20:
```

the earlier false conditions already establish that `age >= 13`. Therefore the condition effectively represents:

```text
13 <= age < 20
```

For `age = 20`:

```text
20 < 2   → False
20 < 4   → False
20 < 13  → False
20 < 20  → False
20 < 65  → True
```

So `20` is classified as an adult in this exercise.

---

# Chapter 5 Exercises

## Exercise 5-1 — Conditional Tests

```python
alien_color = "green"

if alien_color == "green":
    print("The player just earned 5 points.")
```

Output:

```text
The player just earned 5 points.
```

## Exercise 5-2 — Alien Colors #2

```python
alien_color = "yellow"

if alien_color == "green":
    print("The player just earned 5 points.")
```

Output:

```text
(no output)
```

Changing the value to `"green"` causes the message to print.

## Exercise 5-3 — Alien Colors #3

```python
alien_color = "yellow"

if alien_color == "green":
    print("The player just earned 5 points.")
else:
    print("The player just earned 10 points.")
```

Output:

```text
The player just earned 10 points.
```

## Exercise 5-4 — Three Outcomes

```python
alien_color = "red"

if alien_color == "green":
    print("The player just earned 5 points.")
elif alien_color == "yellow":
    print("The player just earned 10 points.")
else:
    print("The player just earned 15 points.")
```

For `"red"`:

```text
The player just earned 15 points.
```

## Exercise 5-5 — Explicit Red Branch

```python
alien_color = "red"

if alien_color == "green":
    print("The player just earned 5 points.")
elif alien_color == "yellow":
    print("The player just earned 10 points.")
elif alien_color == "red":
    print("The player just earned 15 points.")
```

Only `"red"` receives the 15-point message.

## Exercise 5-6 — Stages of Life

```python
age = 25

if age < 2:
    print("This person is a baby")
elif age < 4:
    print("This person is a toddler")
elif age < 13:
    print("This person is a kid")
elif age < 20:
    print("This person is a teenager")
elif age < 65:
    print("This person is an adult")
else:
    print("This person is an elder")
```

For `age = 25`:

```text
This person is an adult
```

### Debugging lesson

An implementation such as:

```python
elif age > 4 and age <= 13:
```

makes boundary handling harder to reason about. Sequential upper-bound checks are simpler because earlier failed conditions establish the lower boundary automatically.

## Exercise 5-7 — Favorite Fruit

```python
favorite_fruits = ["mango", "banana", "apple"]

if "mango" in favorite_fruits:
    print("You really like mango!")

if "banana" in favorite_fruits:
    print("You really like banana!")

if "apple" in favorite_fruits:
    print("You really like apple!")

if "watermelon" in favorite_fruits:
    print("You really like watermelon!")

if "cherry" in favorite_fruits:
    print("You really like cherry!")
```

Output:

```text
You really like mango!
You really like banana!
You really like apple!
```

## Exercise 5-8 — Hello Admin

```python
usernames = ["admin", "abhijith", "john", "sarah", "mike"]

for username in usernames:
    if username == "admin":
        print("Hello admin, would you like to see a status report?")
    else:
        print(f"Hello {username}, thank you for logging in again.")
```

Output:

```text
Hello admin, would you like to see a status report?
Hello abhijith, thank you for logging in again.
Hello john, thank you for logging in again.
Hello sarah, thank you for logging in again.
Hello mike, thank you for logging in again.
```

## Exercise 5-9 — No Users

```python
usernames = []

if usernames:
    for username in usernames:
        if username == "admin":
            print("Hello admin, would you like to see a status report?")
        else:
            print(f"Hello {username}, thank you for logging in again.")
else:
    print("We need to find some users!")
```

Output:

```text
We need to find some users!
```

## Exercise 5-10 — Checking Usernames

```python
current_users = ["admin", "abhijith", "john", "sarah", "mike"]
new_users = ["alice", "john", "bob", "ADMIN", "sarah"]

for user in new_users:
    if user.lower() in current_users:
        print(f"The username {user} is already taken. Please enter a new username.")
    else:
        print(f"The username {user} is available.")
```

Example output:

```text
The username alice is available.
The username john is already taken. Please enter a new username.
The username bob is available.
The username ADMIN is already taken. Please enter a new username.
The username sarah is already taken. Please enter a new username.
```

### Normalization lesson

The original username is not changed. It is converted to lowercase for comparison:

```python
user.lower()
```

Therefore:

```text
"Admin".lower() → "admin"
"ADMIN".lower() → "admin"
"AdMiN".lower() → "admin"
```

## Exercise 5-11 — Ordinal Numbers

```python
numbers = range(1, 10)

for n in numbers:
    if n == 1:
        print(f"{n}st")
    elif n == 2:
        print(f"{n}nd")
    elif n == 3:
        print(f"{n}rd")
    else:
        print(f"{n}th")
```

Output:

```text
1st
2nd
3rd
4th
5th
6th
7th
8th
9th
```

`range(1, 10)` is iterable, so it can be used directly in a `for` loop.

---

# Interview Review

## 1. `if / elif / else` vs independent `if`

An `if / elif / else` chain checks conditions from top to bottom and executes the first true branch.

Separate `if` statements are independent, so multiple conditions can execute.

## 2. `=` vs `==`

```python
a = 2
```

assigns `2` to `a`.

```python
a == 2
```

checks whether `a` equals `2`.

## 3. `and` vs `or`

`and` requires both conditions to be true.

`or` requires at least one condition to be true.

## 4. `in` vs `not in`

```python
if "Python" in skills:
```

checks whether `"Python"` exists.

```python
if "Python" not in skills:
```

checks whether `"Python"` does not exist.

## 5. Empty lists

```python
numbers = []

if numbers:
    print("The list has values.")
else:
    print("The list is empty.")
```

The `else` branch executes because:

```python
bool([]) == False
```

## 6. Loop vs list comprehension

```python
for number in numbers:
    print(number ** 2)
```

Processes/displays each square without creating a new list.

```python
squares = [number ** 2 for number in numbers]
```

Builds and stores a new list.

## 7. Loop and indentation

```python
numbers = [1, 2, 3, 4, 5]

for number in numbers:
    if number == 3:
        print("Found 3")

print("Finished")
```

Output:

```text
Found 3
Finished
```

## 8. `sort()` vs `sorted()`

`sort()` modifies the original list and returns `None`.

`sorted()` returns a new sorted list and preserves the original.

## 9. List references vs copying

```python
numbers = [1, 2, 3]

copy1 = numbers
copy2 = numbers[:]

copy1.append(4)
```

Results:

```text
numbers → [1, 2, 3, 4]
copy1   → [1, 2, 3, 4]
copy2   → [1, 2, 3]
```

## 10. Conditional list comprehension

```python
numbers = [1, 2, 3, 4, 5]

even_numbers = [number for number in numbers if number % 2 == 0]
```

Plain English:

> For each number in `numbers`, if it is divisible by 2, store it in `even_numbers`.

Result:

```python
[2, 4]
```

---

# Key Takeaways

1. **Conditions produce Boolean results.**
2. **Indentation determines block membership.**
3. **`if / elif / else` stops at the first true branch.**
4. **Separate `if` statements are independent.**
5. **`and` requires both conditions to be true.**
6. **`or` requires at least one condition to be true.**
7. **`not` reverses a Boolean value.**
8. **Empty collections are false in Boolean contexts.**
9. **Ordered conditions can eliminate unnecessary lower-bound checks.**
10. **Normalize data before comparison when capitalization should not matter.**

---

# Debugging Lessons

### Boundary conditions matter

A condition can work for one input while failing at the boundaries.

For example:

```python
age > 4 and age <= 13
```

excludes `4`.

Always test boundary values.

### Conditions are evaluated in order

When Python reaches a later `elif`, the earlier conditions have already been proven false.

### Avoid unnecessary conditions

Instead of:

```python
elif age > 20 and age <= 65:
```

an ordered chain can use:

```python
elif age < 65:
```

because earlier branches already establish the lower boundary.

### Test edge cases

Don't only test:

```python
age = 25
```

Test values around every boundary:

```text
1
2
3
4
12
13
19
20
64
65
```

This catches logical bugs.

---

# Chapter 5 Completion Checklist

- [x] Basic `if`
- [x] `if / else`
- [x] `if / elif / else`
- [x] Independent `if` statements
- [x] Comparison operators
- [x] `and`
- [x] `or`
- [x] `not`
- [x] `in`
- [x] `not in`
- [x] Boolean/truthiness
- [x] Empty-list checks
- [x] `for` + `if`
- [x] Nested control flow
- [x] Boundary-condition reasoning
- [x] Exercises 5-1 through 5-11
- [x] Interview review — 10/10

---

## Status

**Chapter 5 — If Statements: COMPLETE ✅**

**Next: Chapter 6 — Dictionaries**
