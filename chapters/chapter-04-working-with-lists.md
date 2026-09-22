# Chapter 4 — Working with Lists

## Source

Based on *Python Crash Course, 3rd Edition* — Chapter 4, **Working with Lists**.

## 1. `for` Loops

A `for` loop repeats an operation for every item in a list.

```python
cars = ["bmw", "audi", "toyota", "honda"]

for car in cars:
    print(car)
```

The indented block is the loop body and runs once for every item.

```python
for variable in list:
    # code to repeat
```

Use standard Python indentation of 4 spaces.

## 2. `range()`

`range()` generates a sequence of numbers.

```python
range(1, 6)
```

produces `1, 2, 3, 4, 5`.

The start is included; the stop is excluded.

```python
range(start, stop)
range(start, stop, step)
```

Examples:

```python
range(5)          # 0, 1, 2, 3, 4
range(2, 10, 2)   # 2, 4, 6, 8
range(10, 0, -2)  # 10, 8, 6, 4, 2
```

## 3. Creating Lists with `range()`

```python
numbers = list(range(1, 6))
print(numbers)
```

Output:

```text
[1, 2, 3, 4, 5]
```

Example:

```python
numbers = list(range(1, 21, 2))
```

creates the odd numbers from 1 through 20.

## 4. Simple Statistics

```python
scores = [78, 92, 85, 67, 95]

print(min(scores))
print(max(scores))
print(sum(scores))
```

Output:

```text
67
95
417
```

- `min()` → smallest value
- `max()` → largest value
- `sum()` → total

## 5. List Comprehensions

A list comprehension provides a compact way to create a new list.

Traditional approach:

```python
squares = []

for value in range(1, 6):
    square = value ** 2
    squares.append(square)
```

List comprehension:

```python
squares = [value ** 2 for value in range(1, 6)]
```

Read it as:

> For each `value` in `range(1, 6)`, calculate `value ** 2` and put the result into the new list.

General pattern:

```python
new_list = [expression for item in iterable]
```

Example:

```python
cubes = [number ** 3 for number in range(1, 6)]
```

## 6. Working with Parts of a List

Given:

```python
players = ["charles", "martina", "michael", "florence", "eli"]
```

A slice selects part of a list:

```python
players[1:4]
```

Result:

```text
["martina", "michael", "florence"]
```

The start index is included; the stop index is excluded.

```python
players[:3]   # beginning through index 2
players[2:]   # index 2 through the end
players[:]    # entire list
```

## 7. Copying Lists

Using a full slice creates a separate list:

```python
foods = ["pizza", "falafel", "carrot cake"]

favorite_foods = foods[:]
favorite_foods.append("ice cream")
```

Now `foods` remains unchanged while `favorite_foods` contains `"ice cream"`.

Assignment is different:

```python
favorite_foods = foods
```

Both variables refer to the same list, so changing one changes what the other sees.

### Key distinction

```python
favorite_foods = foods
```

→ same list

```python
favorite_foods = foods[:]
```

→ separate list

# Exercises Completed

## Exercise 4-1 — Pizzas

Created `pizzas.py` and used a `for` loop to print a sentence for each pizza, with another sentence inside the loop.

## Exercise 4-2 — Animals

Created `animals2.py` with three animals sharing a characteristic and used a `for` loop plus a statement outside the loop.

## Exercise 4-3 — Counting to Twenty

Created `counting.py`:

```python
numbers = range(1, 21)

for n in numbers:
    print(n)
```

Printed 1 through 20.

## Exercise 4-4 — One Million

Created a list containing one million numbers:

```python
numbers = list(range(1, 1_000_001))

for number in numbers:
    print(number)
```

The output was intentionally stopped with `Ctrl+C`, producing `KeyboardInterrupt`.

## Exercise 4-5 — Summing a Million

Created `million_stats.py`:

```python
numbers = list(range(1, 1_000_001))

print(min(numbers))
print(max(numbers))
print(sum(numbers))
```

Output:

```text
1
1000000
500000500000
```

## Exercise 4-6 — Odd Numbers

Created `odd_numbers.py`:

```python
numbers = list(range(1, 21, 2))

for num in numbers:
    print(num)
```

## Exercise 4-7 — Threes

Created `threes.py`:

```python
numbers = list(range(3, 31, 3))

for num in numbers:
    print(num)
```

## Exercise 4-8 — Cubes

Created `cubes.py`:

```python
numbers = list(range(1, 11))

for n in numbers:
    print(n ** 3)
```

## Exercise 4-9 — Cube Comprehension

Created `cube_comprehension.py`:

```python
cubes = [n ** 3 for n in range(1, 11)]

print(cubes)
```

Output:

```text
[1, 8, 27, 64, 125, 216, 343, 512, 729, 1000]
```

# Chapter 4 Interview Review

### 1. `range()` vs `list(range())`

`range(1, 10)` creates a range object representing 1 through 9.

`list(range(1, 10))` creates an actual list containing 1 through 9.

### 2. Copying vs assigning a list

`copy = numbers` makes both variables refer to the same list.

`copy = numbers[:]` creates a separate list.

### 3. Modulo operator

`number % 2` returns the remainder after division by 2.

Therefore:

```python
if number % 2 == 0:
```

selects even numbers.

### 4. Printing values vs squares

```python
for number in numbers:
    print(number)
```

prints original values.

```python
for number in numbers:
    print(number ** 2)
```

prints their squares without changing the list.

### 5. Explaining a list comprehension

```python
squares = [value ** 2 for value in range(1, 6)]
```

means:

> For each number from 1 through 5, calculate its square and store the results in `squares` as a list.

### 6. List slices

`numbers[:3]` selects from the beginning up to, but not including, index 3.

`numbers[3:]` selects from index 3 through the end.

### 7. Code outside a loop

A statement with no indentation after a loop runs once after the loop finishes.

### 8. `sort()` vs `sorted()`

```python
numbers.sort()
```

- Changes the original list.
- Returns `None`.

```python
sorted(numbers)
```

- Does not change the original list.
- Returns a new sorted list.

### 9. Why `numbers.sort()` assigned to a variable gives `None`

```python
sorted_numbers = numbers.sort()
```

sorts the list in place, but `sort()` returns `None`.

### 10. `for` loop vs list comprehension

```python
for number in numbers:
    print(number ** 2)
```

processes and prints each square.

```python
squares = [number ** 2 for number in numbers]
```

processes each value and creates a new list containing the squares.

# Key Takeaways

- A `for` loop repeats a block of code for each item.
- Indentation determines what belongs inside the loop.
- `range()` uses an inclusive start and exclusive stop.
- `range(5)` starts at 0.
- `list(range(...))` converts a range object into a list.
- `min()`, `max()`, and `sum()` work directly with numerical lists.
- List comprehensions provide a compact way to create lists.
- List slices use start-inclusive / stop-exclusive behavior.
- `[:]` can create a separate copy of a list.
- Assignment with `=` makes two variables refer to the same list.
- `sort()` changes a list and returns `None`.
- `sorted()` returns a new sorted list.

# Chapter 4 Completion Checklist

- [x] `for` loops
- [x] Loop variables
- [x] Loop indentation
- [x] `range()`
- [x] `range(start, stop)`
- [x] `range(start, stop, step)`
- [x] Negative steps
- [x] `list(range(...))`
- [x] `min()`
- [x] `max()`
- [x] `sum()`
- [x] List comprehensions
- [x] List slices
- [x] Copying lists
- [x] Assignment vs copying
- [x] Exercises 4-1 through 4-9
- [x] Chapter 4 interview review

**Chapter 4 — COMPLETE**
