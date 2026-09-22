# Chapter 3 — Introducing Lists

> Based on **Python Crash Course, 3rd Edition — Chapter 3: Introducing Lists**
>
> This chapter documents the concepts, exercises, hands-on practice, mistakes, and interview review completed while studying Chapter 3.

---

## 1. Chapter Overview

A **list** stores multiple values in a single variable.

```python
cars = ["bmw", "audi", "toyota", "subaru"]
```

Lists are useful when several related values need to be kept together and accessed or modified individually.

Chapter 3 covers:

- Creating lists
- Accessing list elements
- Indexing
- Modifying elements
- Adding elements
- Removing elements
- Sorting
- Reversing
- Finding the length of a list
- Avoiding index errors

---

## 2. Creating a List

```python
cars = ["bmw", "audi", "toyota", "subaru"]

print(cars)
```

Output:

```text
['bmw', 'audi', 'toyota', 'subaru']
```

A list is written using square brackets `[]`, with individual values separated by commas.

---

## 3. Accessing List Elements

Python uses **zero-based indexing**.

```python
cars = ["bmw", "audi", "toyota", "subaru"]

print(cars[0])
print(cars[1])
print(cars[-1])
```

Output:

```text
bmw
audi
subaru
```

Index positions:

```text
bmw     -> 0
audi    -> 1
toyota  -> 2
subaru  -> 3
```

Negative indexing starts from the end:

```text
-1 -> last item
-2 -> second-to-last item
```

Using `-1` is useful when you want the last item without knowing the list's length.

---

## 4. Lists Are Mutable

Unlike strings, lists can be changed after they are created.

```python
cars = ["bmw", "audi", "toyota", "subaru"]

cars[1] = "honda"

print(cars)
```

Output:

```text
['bmw', 'honda', 'toyota', 'subaru']
```

The assignment:

```python
cars[1] = "honda"
```

**replaces** the value at index `1`.

It does not insert a new element.

---

## 5. Adding Elements with `append()`

`append()` adds an item to the **end** of a list.

```python
cars.append("tesla")
```

Pattern:

```python
list_name.append(value)
```

---

## 6. Adding Elements with `insert()`

`insert()` adds an item at a specific index.

```python
cars.insert(1, "mercedes")
```

Pattern:

```python
list_name.insert(index, value)
```

Existing elements shift to the right.

- `append()` → adds to the end
- `insert()` → adds at a specified position

---

## 7. Removing by Value with `remove()`

`remove()` removes an item by its **value**.

```python
cars.remove("audi")
```

If the value does not exist, Python raises a `ValueError`.

---

## 8. Removing by Index with `del`

`del` removes an element using its **index**.

```python
del cars[1]
```

`del` does not return the removed value.

---

## 9. Removing with `pop()`

`pop()` removes an item and **returns the removed value**.

```python
removed_car = cars.pop()
```

This removes the last item.

You can also specify an index:

```python
removed_car = cars.pop(1)
```

Given:

```python
cars = ["bmw", "toyota", "subaru"]
```

the result is:

```text
removed_car -> 'toyota'
cars        -> ['bmw', 'subaru']
```

---

## 10. `remove()` vs `del` vs `pop()`

| Operation | Identifies item by | Returns removed value? |
|---|---|---|
| `remove(value)` | Value | No |
| `del list[index]` | Index | No |
| `pop(index)` | Index | Yes |

---

## 11. Finding the Length with `len()`

```python
cars = ["bmw", "toyota", "subaru", "tesla"]

print(len(cars))
```

Output:

```text
4
```

`len()` returns the number of elements in the list.

---

## 12. Sorting with `sort()`

`sort()` changes the existing list into alphabetical order.

```python
cars.sort()
```

For reverse-alphabetical order:

```python
cars.sort(reverse=True)
```

### Important

`sort()`:

- Is a list method.
- Modifies the existing list **in place**.
- Returns `None`.

Therefore:

```python
result = cars.sort()
```

makes:

```text
cars   -> sorted list
result -> None
```

---

## 13. Sorting with `sorted()`

`sorted()` returns a **new sorted list** without changing the original list.

```python
cars = ["bmw", "audi", "toyota", "subaru"]

sorted_cars = sorted(cars)

print(sorted_cars)
print(cars)
```

Output:

```text
['audi', 'bmw', 'subaru', 'toyota']
['bmw', 'audi', 'toyota', 'subaru']
```

Reverse-alphabetical sorting:

```python
sorted_cars = sorted(cars, reverse=True)
```

### Critical distinction

```text
sort()     -> modifies original list -> None
sorted()   -> returns new list       -> original unchanged
```

---

## 14. Reversing with `reverse()`

`reverse()` reverses the **current order** of a list.

```python
cars = ["bmw", "toyota", "subaru", "audi"]

cars.reverse()

print(cars)
```

Output:

```text
['audi', 'subaru', 'toyota', 'bmw']
```

`reverse()` does **not** mean reverse-alphabetical sorting. It simply reverses the current order.

Applying it again restores the previous order.

Like `sort()`, `reverse()` modifies the list **in place** and returns `None`.

---

## 15. `sort()`, `reverse()`, and `sorted()`

| Operation | Modifies original? | Returns a new list? | Return value |
|---|---:|---:|---|
| `sort()` | Yes | No | `None` |
| `reverse()` | Yes | No | `None` |
| `sorted()` | No | Yes | New list |

---

## 16. Index Errors

A common list error is requesting an index that doesn't exist.

```python
cars = ["bmw", "toyota", "subaru"]

print(cars[3])
```

Valid indexes are:

```text
bmw     -> 0
toyota  -> 1
subaru  -> 2
```

There is no index `3`, so Python raises:

```text
IndexError: list index out of range
```

Remember:

- `IndexError` → invalid index
- `ValueError` → the requested value is not acceptable/present for an operation such as `remove()`

---

## 17. Accessing the Last Item

Use `-1`:

```python
cars[-1]
```

Example:

```python
cars = ["bmw", "toyota", "subaru"]

print(cars[-1])
```

Output:

```text
subaru
```

---

# Hands-On Practice

## 18. Favorite Places

```python
favorite_places = ['Bengaluru', 'Moab', 'Nashville', 'Zurich', 'Portland']

print(favorite_places)
print(favorite_places[-1])
print(len(favorite_places))
```

Output:

```text
['Bengaluru', 'Moab', 'Nashville', 'Zurich', 'Portland']
Portland
5
```

This demonstrated list creation, negative indexing, and `len()`.

---

## 19. Insert and Remove

```python
favorite_places.insert(2, 'Tokyo')
favorite_places.remove('Moab')
```

Final list:

```text
['Bengaluru', 'Tokyo', 'Nashville', 'Zurich', 'Portland']
```

---

## 20. Debugging `reverse()`

This was intentionally explored:

```python
fsr2 = favorite_places.reverse()
```

The list was reversed, but `fsr2` became:

```text
None
```

Trying:

```python
fsr2.reverse()
```

therefore produced an `AttributeError` because `fsr2` was `None`.

The correct pattern is:

```python
favorite_places.reverse()
print(favorite_places)

favorite_places.reverse()
print(favorite_places)
```

This demonstrated the difference between **mutating an object in place** and **returning a new value**.

---

# Book Exercises

## 21. Exercise 3-1 — Names

```python
names = ['abhijith', 'kvvnr', 'lalasa']

print(names[0])
print(names[1])
print(names[2])
```

Output:

```text
abhijith
kvvnr
lalasa
```

---

## 22. Exercise 3-2 — Greetings

```python
names = ['abhijith', 'kvvnr', 'lalasa']

print(f"Hello {names[0]}, how are you?")
print(f"Hello {names[1]}, how are you?")
print(f"Hello {names[2]}, how are you?")
```

---

## 23. Exercise 3-3 — Your Own List

```python
goals = ['Porsche', 'Gulfstream', 'Lamborghini']

print(f"I will own a {goals[0]} and drive like crazy!")
print(f"I will own a {goals[1]} and fly to desired destinations freely!")
print(f"I will own a {goals[2]} and sail to my privately own island!")
```

---

## 24. Exercise 3-4 — Guest List

```python
names = ['abhijith', 'kvvnr', 'lalasa']

print(f"{names[0]}, please join me for dinner")
print(f"{names[1]}, please join me for dinner")
print(f"{names[2]}, please join me for dinner")
```

---

## 25. Exercise 3-5 — Changing Guest List

One guest was replaced using index assignment:

```python
names[1] = 'sneha'
```

This demonstrated that assignment **replaces** an existing element.

---

## 26. Exercise 3-6 — More Guests

Three guests were added:

```python
names.append('karthik')

names.insert(1, 'abhinav')
names.insert(3, 'sumukh')
```

Final list:

```text
['abhijith', 'abhinav', 'sneha', 'sumukh', 'lalasa', 'karthik']
```

This also demonstrated that inserting changes the indexes of later elements.

---

## 27. Exercise 3-7 — Shrinking Guest List

Guests were removed using `pop()` until only two remained.

Then the final guests were invited and:

```python
del names[0:]
```

removed the remaining elements.

Final list:

```text
[]
```

---

## 28. Exercise 3-8 — Seeing the World

The following sequence was practiced:

```python
favorite_places = ['Bengaluru', 'Moab', 'Nashville', 'Zurich', 'Portland']

print(favorite_places)

print(sorted(favorite_places))
print(favorite_places)

print(sorted(favorite_places, reverse=True))
print(favorite_places)

favorite_places.reverse()
print(favorite_places)

favorite_places.reverse()
print(favorite_places)

favorite_places.sort()
print(favorite_places)

favorite_places.sort(reverse=True)
print(favorite_places)
```

This demonstrated the difference between `sorted()`, `reverse()`, and `sort()`.

---

## 29. Exercise 3-9 — Dinner Guests

```python
names = ['abhijith', 'sneha', 'lalasa']

print(f"I am inviting {len(names)} people to dinner.")
```

Output:

```text
I am inviting 3 people to dinner.
```

---

## 30. Exercise 3-10 — Every Function

A single list was used to demonstrate the major Chapter 3 operations:

```python
goals = ['cashflow', 'house']
print(goals)

goals[1] = 'mansions'
print(goals)

goals.append('private island')
print(goals)

goals.insert(1, 'supercars')
print(goals)

goals.insert(2, 'conglomerate')
print(goals)

goals.remove('cashflow')
print(goals)

goals.pop()
print(goals)

print(len(goals))

goals.sort()
print(goals)

sorted_goals = sorted(goals)
print(sorted_goals)

goals.reverse()
print(goals)

del goals[0]
print(goals)
```

Final output:

```text
['cashflow', 'house']
['cashflow', 'mansions']
['cashflow', 'mansions', 'private island']
['cashflow', 'supercars', 'mansions', 'private island']
['cashflow', 'supercars', 'conglomerate', 'mansions', 'private island']
['supercars', 'conglomerate', 'mansions', 'private island']
['supercars', 'conglomerate', 'mansions']
3
['conglomerate', 'mansions', 'supercars']
['conglomerate', 'mansions', 'supercars']
['supercars', 'mansions', 'conglomerate']
['mansions', 'conglomerate']
```

---

# Interview Review

## Q1 — `sort()` vs `sorted()`

`sort()` is a list method that modifies the existing list and returns `None`.

`sorted()` is a function that returns a new sorted list.

---

## Q2 — `pop(index)`

```python
cars = ['bmw', 'audi', 'toyota']
cars.pop(1)
```

removes `'audi'`.

Final list:

```python
['bmw', 'toyota']
```

---

## Q3 — Removing Items

```python
cars.remove('audi')
```

Removes by **value**.

```python
del cars[1]
```

Removes by **index**.

```python
removed = cars.pop(1)
```

Removes by **index** and stores the removed value.

---

## Q4 — `append()` vs `insert()`

```python
cars.append('honda')
```

puts `'honda'` at the end.

```python
cars.insert(1, 'honda')
```

puts `'honda'` at index `1`.

---

## Q5 — Assignment vs `insert()`

```python
cars[1] = 'honda'
```

replaces the existing value.

```python
cars.insert(1, 'honda')
```

adds a new value and shifts existing elements.

---

## Q6 — Indexing and Slicing

Given:

```python
numbers = [10, 20, 30, 40, 50]
```

```python
numbers[0]   # 10
numbers[-1]  # 50
numbers[1:4] # [20, 30, 40]
```

---

## Q7 — IndexError

```python
cars = ['bmw', 'audi', 'toyota']
cars[3]
```

raises:

```text
IndexError: list index out of range
```

because the highest valid index is `2`.

---

## Q8 — `reverse()` vs reverse sorting

```python
cars.reverse()
```

reverses the current order in place.

```python
cars = sorted(cars, reverse=True)
```

creates a new reverse-alphabetically sorted list and assigns it back to `cars`.

---

## Q9 — Why does `sort()` return `None`?

```python
result = cars.sort()
```

sorts `cars` in place, while `result` becomes:

```text
None
```

---

## Q10 — Why does `sorted()` work differently?

```python
sorted_cars = sorted(cars)
```

works because `sorted()` returns a new list.

```python
sorted_cars = cars.sort()
```

does not store a sorted list because `sort()` returns `None`.

---

# Key Takeaways

1. Lists store multiple values in one variable.
2. Lists use zero-based indexing.
3. Negative indexes access elements from the end.
4. Lists are mutable.
5. Assignment replaces an existing element.
6. `append()` adds to the end.
7. `insert()` adds at a specific position.
8. `remove()` removes by value.
9. `del` removes by index.
10. `pop()` removes by index and returns the removed value.
11. `len()` returns the number of elements.
12. `sort()` modifies the list in place and returns `None`.
13. `sorted()` returns a new sorted list.
14. `reverse()` modifies the list in place and returns `None`.
15. Invalid indexes raise `IndexError`.
16. Do not assume every method returns the object it modifies.

---

# Chapter 3 Completion Status

**Status: COMPLETE**

### Concepts

- [x] Creating lists
- [x] Accessing elements
- [x] Zero-based indexing
- [x] Negative indexing
- [x] Modifying elements
- [x] `append()`
- [x] `insert()`
- [x] `remove()`
- [x] `del`
- [x] `pop()`
- [x] `len()`
- [x] `sort()`
- [x] `sorted()`
- [x] `reverse()`
- [x] `IndexError`

### Exercises

- [x] 3-1 Names
- [x] 3-2 Greetings
- [x] 3-3 Your Own List
- [x] 3-4 Guest List
- [x] 3-5 Changing Guest List
- [x] 3-6 More Guests
- [x] 3-7 Shrinking Guest List
- [x] 3-8 Seeing the World
- [x] 3-9 Dinner Guests
- [x] 3-10 Every Function

### Interview Review

- [x] 10 questions completed
- [x] `sort()` vs `sorted()`
- [x] `IndexError` vs `ValueError`
- [x] In-place mutation vs returned values

---

## Chapter 3 Summary

```text
LIST
 |
 +-- Access       -> cars[0]
 |
 +-- Modify       -> cars[0] = ...
 |
 +-- Add          -> append(), insert()
 |
 +-- Remove       -> remove(), del, pop()
 |
 +-- Inspect      -> len()
 |
 +-- Reorder      -> sort(), sorted(), reverse()
```

Most important distinction:

```text
sort()     -> changes existing list -> None
reverse()  -> changes existing list -> None
sorted()   -> creates new list      -> returns list
```

**Chapter 3 complete.**
