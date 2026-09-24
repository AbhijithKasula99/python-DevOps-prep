# Chapter 6 — Dictionaries

## Overview

Chapter 6 introduces **dictionaries** as a way to connect related pieces of information. A dictionary stores information as **key-value pairs**.

This chapter covered:

- Creating dictionaries
- Accessing values using keys
- Adding and modifying entries
- Removing entries
- Looping through dictionaries
- Checking dictionary membership
- Nesting dictionaries and lists
- Working with lists of dictionaries
- Working with dictionaries of lists
- Working with dictionaries inside dictionaries

---

## 1. Creating a Dictionary

A dictionary is created with curly braces `{}` and contains key-value pairs.

```python
person = {
    "name": "Abhijith",
    "age": 27,
    "city": "Bengaluru"
}
```

Each key identifies a value:

```text
"name" → "Abhijith"
"age"  → 27
"city" → "Bengaluru"
```

---

## 2. Accessing Values

Use the key inside square brackets:

```python
print(person["name"])
print(person["age"])
```

If the key does not exist:

```python
person["salary"]
```

Python raises:

```text
KeyError
```

---

## 3. Modifying and Adding Values

Modify an existing value:

```python
person["age"] = 28
```

Add a new key-value pair:

```python
person["goal"] = "Build great things"
```

---

## 4. Removing an Entry

Use `del`:

```python
del person["goal"]
```

This removes the key and its associated value.

---

## 5. Starting with an Empty Dictionary

```python
person = {}

person["name"] = "Abhijith"
person["age"] = 27
```

---

## 6. Looping Through Dictionaries

Use `.items()` when both the key and value are needed:

```python
for key, value in person.items():
    print(f"{key}: {value}")
```

Compare that with:

```python
for key in person:
    print(key)
```

The first gives **key and value**; the second iterates over **keys**.

---

## 7. Keys and Values

Keys:

```python
for key in person.keys():
    print(key)
```

Values:

```python
for value in person.values():
    print(value)
```

A set can remove duplicate values:

```python
set(person.values())
```

---

## 8. Dictionary Membership

The `in` operator checks dictionary **keys** by default:

```python
poll = {
    "abhijith": "Python",
    "john": "Java"
}

"abhijith" in poll
```

To check values:

```python
"Python" in poll.values()
```

Remember:

```python
"Python" in poll
```

checks keys, so it is `False` for the example above.

---

# Nesting

Chapter 6 also covers nesting lists and dictionaries. fileciteturn13file2turn13file3

## 9. Dictionary Containing a List

```python
person = {
    "name": "Abhijith",
    "skills": ["Python", "AWS", "Docker"]
}
```

Access the list:

```python
person["skills"]
```

Access an individual item:

```python
person["skills"][2]
```

Result:

```text
Docker
```

Pattern:

**dictionary → list → index**

---

## 10. List of Dictionaries

```python
users = [
    {"name": "Abhijith", "age": 27},
    {"name": "John", "age": 30}
]
```

Loop through it:

```python
for user in users:
    print(user["name"])
    print(user["age"])
```

Pattern:

**list → dictionary → key → value**

---

## 11. Dictionary of Lists

```python
places = {
    "abhijith": ["Bengaluru", "Zurich", "Moab"],
    "john": ["London", "Paris", "Tokyo"]
}
```

Loop through it:

```python
for name, places_list in places.items():
    print(f"{name}'s favorite places are {places_list}")
```

Pattern:

**dictionary → list**

---

## 12. Dictionary Inside a Dictionary

```python
people = {
    "abhijith": {
        "age": 27,
        "city": "Bengaluru"
    },
    "john": {
        "age": 30,
        "city": "London"
    }
}
```

Access John's city:

```python
people["john"]["city"]
```

Result:

```text
London
```

Pattern:

**dictionary → nested dictionary → key → value**

---

## 13. Deeply Nested Data

```python
users = {
    "abhijith": {
        "skills": ["Python", "AWS", "Docker"]
    }
}
```

Access `"AWS"`:

```python
users["abhijith"]["skills"][1]
```

Pattern:

**dictionary → nested dictionary → list → index**

---

# Exercises Completed

## 6-1 — Person

Created a dictionary containing first name, last name, age, and city and accessed each value.

## 6-2 — Favorite Numbers

Created nested dictionary data for people and their favorite numbers and practiced accessing the nested value.

## 6-3 — Glossary

Created a glossary dictionary and used `.items()` to print each term and definition.

## 6-4 — Glossary 2

Extended the glossary with additional terms and used one loop so all entries were printed automatically.

## 6-5 — Rivers

Created a dictionary relating countries and rivers and used `.items()` to print the relationship.

## 6-6 — Polling

Created a poll dictionary and checked whether selected people existed as dictionary keys.

Important pattern:

```python
for person in people_to_check:
    if person in poll:
        ...
```

## 6-7 — People

Created a list containing dictionaries representing people and printed each person's information.

## 6-8 — Pets

Created a list of dictionaries representing pets and printed each pet's information.

## 6-9 — Favorite Places

Created a dictionary where each person had a list of favorite places.

## 6-10 — Favorite Numbers

Created a dictionary where each person had a list of favorite numbers.

## 6-11 — Cities

Created a dictionary containing nested dictionaries for cities, then accessed the nested values through a loop.

Example structure:

```python
cities = {
    "Bengaluru": {
        "country": "India",
        "population": "10cr",
        "fact": "Garden City"
    }
}
```

## 6-12 — Extension

Extended the city dictionaries with additional information such as currency and language and printed the new nested values.

---

# Debugging Lessons

## String vs Integer

A condition such as:

```python
if alien["points"] == "5":
```

does not match an integer value:

```python
5
```

because:

```python
"5"   # string
5     # integer
```

Use the type that actually exists in the dictionary.

## Dictionary Membership

```python
"abhijith" in poll
```

checks keys.

```python
"Python" in poll.values()
```

checks values.

## Nested Access

For:

```python
people = {
    "john": {
        "age": 30,
        "city": "London"
    }
}
```

this:

```python
people["john"]["city"]
```

means:

1. Find `"john"` in the outer dictionary.
2. Get John's nested dictionary.
3. Find `"city"`.
4. Return `"London"`.

---

# Interview Takeaways

### `.items()` vs dictionary iteration

```python
for key in dictionary:
```

iterates over keys.

```python
for key, value in dictionary.items():
```

iterates over key-value pairs.

### Accessing a list inside a dictionary

```python
person["skills"][2]
```

gets the third item from the list stored under `"skills"`.

### Missing dictionary key

```python
person["salary"]
```

raises `KeyError` if `"salary"` does not exist.

### Delete vs assignment

```python
del person["age"]
```

removes the key.

```python
person["age"] = 30
```

creates the key if necessary or updates it if it already exists.

### Nested dictionary access

```python
people["john"]["city"]
```

accesses John's city.

### List of dictionaries vs nested dictionary

List of dictionaries:

```python
users = [
    {"name": "Abhijith", "age": 27},
    {"name": "John", "age": 30}
]
```

Nested dictionary:

```python
users = {
    "Abhijith": {"age": 27},
    "John": {"age": 30}
}
```

The first structure is:

**list → dictionary**

The second is:

**dictionary → dictionary**

---

# Chapter 6 Mental Model

When you see nested Python data, identify the container at each level.

For:

```python
users["abhijith"]["skills"][1]
```

read it from left to right:

```text
users
  ↓
dictionary
  ↓
"abhijith"
  ↓
nested dictionary
  ↓
"skills"
  ↓
list
  ↓
[1]
  ↓
item
```

The core skill is being able to look at a Python data structure and understand:

**What is the outer container? What does each key point to? What is inside that value? How do I reach the data I need?**

---

# Chapter 6 Completion

Chapter 6 covered the transition from simple key-value storage to structured, nested data.

The chapter's exercises reinforced dictionaries, loops, membership, and nesting through progressively larger structures. fileciteturn13file0turn13file1
