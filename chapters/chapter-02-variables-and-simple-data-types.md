# Chapter 2 — Variables and Simple Data Types

**Source:** *Python Crash Course, 3rd Edition* by Eric Matthes  
**Status:** Completed  
**Focus:** Python variables, strings, numbers, and simple data types

---

## 1. Chapter Overview

Chapter 2 introduces the basic data types and operations used in Python programs:

- Variables and reassignment
- Variable naming
- Name errors and tracebacks
- Variables as labels associated with values
- Strings and string methods
- f-strings
- Whitespace
- Prefix and suffix removal
- Integers and floats
- Boolean values
- Type conversion
- Comparisons and logical operators
- Indexing and slicing
- String immutability

The goal is to become comfortable storing values, manipulating them, checking their types, and producing formatted output.

---

## 2. Variables

A variable is best understood as a **name or label associated with a value**.

```python
message = "Hello Python!"
print(message)
```

Python associates `message` with the string value.

### Reassignment

A variable can be reassigned:

```python
message = "I am learning Python."
print(message)

message = "I am learning Python fundamentals."
print(message)
```

The second assignment changes what `message` refers to.

### Mental model

Think of variables as **labels**, rather than boxes containing values.

```python
age = 27
age = 28
```

After the second assignment, `age` refers to `28`.

---

## 3. Variable Naming Rules

Python variable names:

- Can contain letters, numbers, and underscores.
- Cannot begin with a number.
- Cannot contain spaces.
- Can use underscores to separate words.
- Should avoid Python keywords and built-in function names such as `print`.
- Should be short but descriptive.
- Conventionally use lowercase names.
- Should avoid confusing lowercase `l` and uppercase `O` with `1` and `0`.

Good examples:

```python
student_name = "Abhijith"
course_name = "Python Fundamentals"
```

---

## 4. Name Errors and Tracebacks

A `NameError` commonly occurs when Python encounters a variable name that has not been defined or has been misspelled.

```python
message = "Hello Python!"
print(mesage)
```

Python cannot find `mesage` because the defined variable is `message`.

When an error occurs, Python provides a **traceback** showing where the problem occurred and what kind of error was found.

### Debugging habit

1. Read the traceback.
2. Find the file and line number.
3. Read the error type.
4. Inspect the indicated code.
5. Check spelling and assumptions.

---

## 5. Strings

A string is a **series of characters**.

Strings can use single or double quotes:

```python
name = "Abhijith"
language = 'Python'
```

Different quote styles can help when a string contains an apostrophe or quotation marks:

```python
message = "Python's syntax is easy."
```

This is invalid:

```python
message = 'Python's syntax is easy'
```

Python interprets the apostrophe as the end of the string and raises a `SyntaxError`.

---

## 6. Changing String Case

Python provides methods for changing the case of strings.

```python
name = "ada lovelace"

print(name.title())
print(name.upper())
print(name.lower())
```

Output:

```text
Ada Lovelace
ADA LOVELACE
ada lovelace
```

A method is an action Python can perform on a piece of data.

---

## 7. f-Strings

f-strings provide a convenient way to insert variable values into strings.

```python
name = "Abhijith"
age = 27

message = f"My name is {name} and I am {age} years old."
print(message)
```

Output:

```text
My name is Abhijith and I am 27 years old.
```

The `f` before the opening quote tells Python to format the string.

Expressions can also be placed inside braces:

```python
age = 27

print(f"I will be {age + 1} next year.")
```

Output:

```text
I will be 28 next year.
```

---

## 8. Concatenating Strings

Strings can be combined with `+`:

```python
first_name = "Abhijith"
last_name = "Kasula"

full_name = first_name + " " + last_name
print(full_name)
```

Output:

```text
Abhijith Kasula
```

A string and an integer cannot be directly combined with `+`:

```python
age = 27
message = "I am " + age + " years old"  # TypeError
```

Convert the integer first:

```python
message = "I am " + str(age) + " years old"
```

Or use an f-string:

```python
message = f"I am {age} years old"
```

---

## 9. Whitespace

Whitespace includes spaces, tabs, and newlines.

### Tab

```python
print("\tPython")
```

### Newline

```python
print("Languages:\nPython\nC\nJavaScript")
```

Useful escape sequences:

| Escape sequence | Meaning |
|---|---|
| `\n` | Newline |
| `\t` | Tab |
| `\\` | Literal backslash |
| `\"` | Double quote inside a double-quoted string |

---

## 10. Stripping Whitespace

Python provides methods for removing unwanted whitespace.

```python
message = "  Python Fundamentals  "

print(message.strip())
print(message)
```

`strip()` returns a stripped version; it does not modify the original string.

```python
message = message.strip()
```

The chapter also introduces:

```python
message.lstrip()
message.rstrip()
message.strip()
```

- `lstrip()` removes whitespace from the left.
- `rstrip()` removes whitespace from the right.
- `strip()` removes whitespace from both sides.

---

## 11. Removing Prefixes and Suffixes

Python 3 provides `removeprefix()` for removing a known prefix.

```python
url = "https://example.com"

clean_url = url.removeprefix("https://")

print(clean_url)
```

Output:

```text
example.com
```

The original string is unchanged unless reassigned.

The chapter also introduces `removesuffix()`:

```python
filename = "python_notes.txt"

print(filename.removesuffix(".txt"))
```

Output:

```text
python_notes
```

---

## 12. Numbers

Python supports several kinds of numerical values.

### Integers

Integers are whole numbers:

```python
x = 10
y = 3
```

Common operations:

```python
print(x + y)   # 13
print(x - y)   # 7
print(x * y)   # 30
print(x / y)   # 3.333...
print(x // y)  # 3
print(x % y)   # 1
print(x ** y)  # 1000
```

| Operator | Meaning |
|---|---|
| `+` | Addition |
| `-` | Subtraction |
| `*` | Multiplication |
| `/` | Division |
| `//` | Floor division |
| `%` | Remainder |
| `**` | Exponentiation |

### Operator precedence

Python follows the normal order of operations.

```python
x = 2 + 3 * 4
print(x)
```

Output:

```text
14
```

Parentheses can change the order:

```python
y = (2 + 3) * 4
print(y)
```

Output:

```text
20
```

### Negative numbers

Negative values are valid integers:

```python
x = -5
y = 2

print(x + y)  # -3
print(x * y)  # -10
print(x ** 2) # 25
```

---

## 13. Floats

A number containing a decimal point is a **float**.

```python
price = 19.99
quantity = 2

total = price * quantity
print(total)
```

Output:

```text
39.98
```

Division also commonly produces a float:

```python
print(10 / 3)
```

Output:

```text
3.3333333333333335
```

---

## 14. Type Conversion

Python provides functions for converting between common data types.

### Integer to string

```python
age = 27

print(str(age))
print(type(str(age)))
```

Output:

```text
27
<class 'str'>
```

### String to integer

```python
age = "27"

print(int(age))
print(type(int(age)))
```

Output:

```text
27
<class 'int'>
```

### String to float

```python
price = "19.99"

print(float(price))
print(type(float(price)))
```

Output:

```text
19.99
<class 'float'>
```

Not every string can be converted:

```python
number = "twenty"
int(number)
```

This raises a `ValueError`.

---

## 15. Booleans

Boolean values represent two states:

```python
True
False
```

Their type is `bool`:

```python
is_learning = True
is_tired = False

print(type(is_learning))
```

Output:

```text
<class 'bool'>
```

---

## 16. Comparisons

Comparison operators produce Boolean results.

```python
age = 27

print(age > 18)
print(age < 20)
print(age == 27)
print(age != 30)
print(age >= 27)
print(age <= 27)
```

| Operator | Meaning |
|---|---|
| `>` | Greater than |
| `<` | Less than |
| `>=` | Greater than or equal to |
| `<=` | Less than or equal to |
| `==` | Equal to |
| `!=` | Not equal to |

### `=` vs `==`

`=` assigns a value:

```python
age = 27
```

`==` compares values:

```python
age == 27
```

---

## 17. Logical Operators

Python provides:

- `and`
- `or`
- `not`

Example:

```python
age = 27

print(age > 18 and age < 30)
print(age < 18 or age > 25)
print(not age == 27)
```

Results:

```text
True
True
False
```

- `and` → both conditions must be true.
- `or` → at least one condition must be true.
- `not` → reverses the Boolean result.

---

## 18. String Equality Is Case-Sensitive

String comparisons consider case.

```python
language = "Python"

print(language == "Python")
print(language == "python")
print(language != "Java")
```

Output:

```text
True
False
True
```

`"Python"` and `"python"` are different strings.

---

## 19. len()

`len()` returns the number of characters in a string.

```python
message = "Python"

print(len(message))
```

Output:

```text
6
```

Spaces are counted:

```python
print(len("Python Programming"))
```

Output:

```text
18
```

---

## 20. String Indexing

Python uses **zero-based indexing**.

```python
language = "Python"
```

Positions:

```text
 P  y  t  h  o  n
 0  1  2  3  4  5
```

Examples:

```python
print(language[0])   # P
print(language[3])   # h
print(language[-1])  # n
```

Negative indexes count from the end.

---

## 21. String Slicing

Slicing uses:

```python
string[start:stop]
```

The `stop` index is **excluded**.

```python
language = "Python"

print(language[0:2])  # Py
print(language[2:6])  # thon
print(language[:4])   # Pyth
print(language[2:])   # thon
```

### Step slicing

The full form is:

```python
string[start:stop:step]
```

Example:

```python
numbers = "0123456789"

print(numbers[::2])
print(numbers[1::2])
```

Output:

```text
02468
13579
```

### Reverse a string

```python
print(language[::-1])
```

Output:

```text
nohtyP
```

### Negative-step slicing

```python
numbers = "0123456789"

print(numbers[8:2:-2])
print(numbers[9:3:-3])
```

Output:

```text
864
96
```

The start index is included, the stop index is excluded, and the negative step moves backward.

---

## 22. String Immutability

Strings are **immutable**.

This is not allowed:

```python
language = "Python"
language[0] = "J"
```

Python raises:

```text
TypeError
```

To produce a changed string, create a new string:

```python
language = "Python"
language = "J" + language[1:]

print(language)
```

Output:

```text
Jython
```

The original string was not modified in place.

---

## 23. Useful type() Checks

```python
print(type(27))
print(type(27.0))
print(type(True))
print(type("27"))
```

Output:

```text
<class 'int'>
<class 'float'>
<class 'bool'>
<class 'str'>
```

---

## 24. Chapter Exercises from the Book

Chapter 2 includes:

- **2-1 Simple Message**
- **2-2 Simple Messages**
- **2-3 Personal Message**
- **2-4 Name Cases**
- **2-5 Famous Quote**
- **2-6 Famous Quote 2**
- **2-7 Stripping Names**
- **2-8 File Extensions**

These exercises reinforce variables, strings, case conversion, f-strings, whitespace, and prefix/suffix removal.

---

## 25. Hands-On Concepts Practiced

### Variables

```python
message = "I am learning Python."
message = "I am learning Python fundamentals."
```

### Naming

```python
student_name = "Abhijith"
course_name = "Python Fundamentals"
```

### Strings

```python
name = "Abhijith"

print(name.title())
print(name.upper())
print(name.lower())
```

### Concatenation

```python
first_name = "Abhijith"
last_name = "Kasula"

full_name = first_name + " " + last_name
```

### f-strings

```python
name = "Abhijith"
age = 27

print(f"My name is {name} and I am {age} years old.")
```

### Numbers

```python
x = 10
y = 3

print(x + y)
print(x / y)
print(x // y)
print(x % y)
```

### Type conversion

```python
str(27)
int("27")
float("19.99")
```

### Booleans and comparisons

```python
age = 27

print(age >= 18)
print(age == 27)
```

### Slicing

```python
numbers = "0123456789"

print(numbers[::2])
print(numbers[::-1])
```

### Immutability

```python
language = "Python"

# language[0] = "J"  # TypeError
language = "J" + language[1:]
```

---

## 26. Interview Review

### Q1. What is a variable?

A variable is a **name or label associated with a value**. Assigning a new value reassigns the variable.

### Q2. Why does this fail?

```python
age = 27
message = "I am " + age + " years old"
```

Python does not automatically convert the integer to a string during concatenation. Use `str(age)` or an f-string.

### Q3. What does string immutability mean?

A string cannot be modified in place. A new string must be created and assigned if a different value is required.

### Q4. What is the difference between `=` and `==`?

```python
age = 27      # assignment
age == 27     # comparison
```

### Q5. What are `/`, `//`, and `%`?

For `10` and `3`:

```text
10 / 3   → 3.333...
10 // 3  → 3
10 % 3   → 1
```

### Q6. What does `2:8:2` mean?

- Start at index `2`.
- Stop before index `8`.
- Move by `2`.

### Q7. Why does this raise `TypeError`?

```python
language = "Python"
language[0] = "J"
```

Because strings are immutable.

### Q8. Does `.upper()` modify the original string?

No. It returns a new string.

```python
message = "Python"

message.upper()
print(message)  # Python
```

Assigning the result changes what the variable refers to:

```python
message = message.upper()
```

### Q9. What do these conversions produce?

```python
str(27)       # "27" -> str
int("27")     # 27   -> int
```

### Q10. What are the types?

```python
type(27)      # int
type(27.0)    # float
type(True)    # bool
type("27")    # str
```

---

## 27. Key Takeaways

Before moving to Chapter 3, be comfortable with:

- Assigning and reassigning variables.
- Choosing readable variable names.
- Reading a `NameError` traceback.
- Understanding variables as labels associated with values.
- Creating and manipulating strings.
- Using `title()`, `upper()`, `lower()`, `strip()`, `lstrip()`, and `rstrip()`.
- Formatting messages with f-strings.
- Using `\n` and `\t`.
- Removing prefixes and suffixes.
- Performing arithmetic with integers and floats.
- Understanding operator precedence.
- Converting between `str`, `int`, and `float`.
- Working with Boolean values.
- Using comparison and logical operators.
- Measuring strings with `len()`.
- Indexing and slicing strings.
- Understanding negative indexes and slice steps.
- Understanding that strings are immutable.
- Inspecting types with `type()`.

---

## 28. Chapter Completion Status

**Chapter 2 — Variables and Simple Data Types: COMPLETE**

The chapter was studied from *Python Crash Course, 3rd Edition*, followed by hands-on prediction exercises and an interview-style review.

**Next chapter:** Chapter 3 — Introducing Lists
