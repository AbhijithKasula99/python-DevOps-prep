# Chapter 1 — Getting Started

> **Source:** *Python Crash Course, 3rd Edition* — Eric Matthes

## 1. Chapter Overview

Chapter 1 establishes the Python programming environment and introduces the basic workflow for writing, running, and troubleshooting Python programs.

Topics covered from the chapter:

- Setting up the programming environment
- Checking the Python version
- Running snippets of Python code
- Using the Python interpreter
- Using VS Code
- Running a Hello World program
- Basic troubleshooting
- Understanding Python error messages
- Chapter exercises

---

## 2. Our Development Environment

| Component | Configuration |
|---|---|
| OS | WSL / Linux |
| Python | 3.14.4 |
| Shell | Bash |
| Editor | VS Code |
| Repository | `python-genai-prep` |
| Git branch | `main` |

Python was verified with:

```bash
python3 --version
```

Output:

```text
Python 3.14.4
```

Python was located with:

```bash
which python3
```

Output:

```text
/usr/bin/python3
```

The book requires Python 3.9 or later, so the installed version satisfies that requirement.

---

## 3. Running Python Snippets

The Python interpreter can be used to experiment with small pieces of Python code without creating a complete program.

Start the interpreter:

```bash
python3
```

The Python prompt appears:

```text
>>>
```

Example:

```python
>>> print("Hello Python interpreter!")
Hello Python interpreter!
```

Exit the interpreter with:

```python
exit()
```

### Key distinction

When the terminal displays:

```text
>>>
```

you are inside the **Python interpreter**.

When the terminal displays a normal shell prompt such as:

```text
abhijith@AbhisLenovo:~/python-genai-prep$
```

you are in the **Linux shell**.

---

## 4. Running Python Directly from the Shell

A small Python expression can also be passed directly to Python using `-c`.

Example:

```bash
python3 -c 'print("Executed directly")'
```

Output:

```text
Executed directly
```

This is useful for quickly testing small pieces of Python code.

---

## 5. Creating and Running a Python Program

Python programs are stored in files ending in `.py`.

Our first program is:

```text
hello_world.py
```

It contains:

```python
print("Hello Python World!")
print("I am learning python.")
print("I will build production software.")
```

Run it with:

```bash
python3 hello_world.py
```

Output:

```text
Hello Python World!
I am learning python.
I will build production software.
```

### Interpreter vs `.py` program

```text
python3
   ↓
Python interpreter
   ↓
Enter Python code interactively
   ↓
Immediate execution
```

versus:

```text
hello_world.py
   ↓
python3 hello_world.py
   ↓
Python executes the saved program
   ↓
Output
```

The interpreter is useful for experimentation. A `.py` file allows us to save a program and execute it repeatedly.

---

## 6. VS Code Workflow

The chapter introduces VS Code as a text editor suitable for Python development.

We verified that VS Code can open our WSL project with:

```bash
code .
```

The `python-genai-prep` project opened successfully.

We also opened `hello_world.py` in VS Code and verified that Python syntax highlighting was working.

Our basic development workflow is therefore:

```text
WSL terminal
     ↓
VS Code
     ↓
Write / edit Python
     ↓
Save .py file
     ↓
Run with python3
     ↓
Inspect output or traceback
```

---

# 7. Troubleshooting and Tracebacks

Programming errors are normal. The important skill is learning how to read the information Python provides.

We intentionally introduced several different mistakes into `hello_world.py`.

---

## 8. `NameError`

We changed:

```python
print("Hello Python World!")
```

to:

```python
pritn("Hello Python World!")
```

Running the program produced:

```text
Traceback (most recent call last):
  File "/home/abhijith/python-genai-prep/hello_world.py", line 1, in <module>
    pritn("Hello Python World!")
    ^^^^^
NameError: name 'pritn' is not defined. Did you mean: 'print'?
```

### What happened?

`print` is a built-in Python function.

We wrote `pritn`, so Python attempted to resolve a name called `pritn` and could not find it.

Therefore Python raised:

```text
NameError
```

We corrected the spelling and the program ran successfully.

### Debugging information

The traceback told us:

- **File:** `hello_world.py`
- **Line:** `1`
- **Problematic code:** `pritn(...)`
- **Error type:** `NameError`
- **Description:** `name 'pritn' is not defined`

---

# 9. Valid Python but Incorrect Output

We then changed:

```python
print("Hello Python World!")
```

to:

```python
print("Hello Python Wrold!")
```

The program executed:

```text
Hello Python Wrold!
I am learning python.
I will build production software.
```

No Python error occurred.

### Why?

This is valid Python:

```python
"Hello Python Wrold!"
```

Everything between the quotation marks is string data.

Python does not know that `Wrold` was intended to be `World`.

### Important lesson

A program completing without an error does **not** necessarily mean that the program is correct.

There is a difference between:

```text
Invalid Python
     ↓
Python reports an error
```

and:

```text
Valid Python
     ↓
Program runs
     ↓
Output can still be incorrect
```

---

# 10. `SyntaxError`

We removed the closing parenthesis:

```python
print("Hello Python World!"
```

Running the program produced:

```text
File "/home/abhijith/python-genai-prep/hello_world.py", line 1
  print("Hello Python World!"
       ^
SyntaxError: '(' was never closed
```

### What happened?

Python syntax has rules for how code must be structured.

The opening:

```text
(
```

requires a matching closing:

```text
)
```

The expression was incomplete, so Python could not parse the code and raised:

```text
SyntaxError
```

We restored the missing `)` and the program ran successfully.

---

# 11. Errors We Practiced

| Situation | Result |
|---|---|
| `pritn(...)` | `NameError` |
| `"Hello Python Wrold!"` | No Python error, but incorrect output |
| Missing `)` | `SyntaxError` |

These examples demonstrate that debugging is not simply about finding "an error."

We need to determine:

```text
What failed?
     ↓
Where did it fail?
     ↓
Why did it fail?
     ↓
What should be changed?
```

---

# 12. Debugging Checklist

When a Python program produces a traceback, first inspect:

### 1. File

Where did Python encounter the problem?

```text
hello_world.py
```

### 2. Line number

Which line should be inspected?

```text
line 1
```

### 3. Error type and description

What kind of problem occurred?

Examples:

```text
NameError
SyntaxError
```

Then inspect the relevant line and surrounding code.

---

# 13. Chapter Exercise Practice

We practiced the concepts behind the chapter's Hello World typo exercise.

### Exercise: intentional error

We deliberately created:

```python
pritn("Hello Python World!")
```

and used the traceback to identify and fix the problem.

### Exercise: typo without a Python error

We deliberately created:

```python
print("Hello Python Wrold!")
```

and observed that Python executed the program because the string was valid.

### Additional syntax experiment

We removed a closing parenthesis:

```python
print("Hello Python World!"
```

and observed:

```text
SyntaxError: '(' was never closed
```

We then restored the correct syntax.

---

# 14. Commands Practiced

### Check Python version

```bash
python3 --version
```

### Locate Python

```bash
which python3
```

### Start the Python interpreter

```bash
python3
```

### Execute a snippet

```bash
python3 -c 'print("Executed directly")'
```

### Run a Python program

```bash
python3 hello_world.py
```

### Open the project in VS Code

```bash
code .
```

### Edit a file from the terminal

```bash
nano hello_world.py
```

---

# 15. Git and Project Setup

The learning repository was established during this chapter.

Repository:

```text
python-genai-prep
```

Branch:

```text
main
```

The repository was connected to GitHub using SSH.

The first commit was:

```text
Start Python fundamentals
```

The Chapter 1 documentation was then committed and pushed to GitHub.

The repository is intended to become a reusable learning guide rather than simply a collection of code.

---

# 16. First Program

Our first Python program:

```python
print("Hello Python World!")
print("I am learning python.")
print("I will build production software.")
```

The purpose of this simple program was to establish the complete development loop:

```text
Write
  ↓
Save
  ↓
Run
  ↓
Observe output
  ↓
Introduce an error
  ↓
Read traceback
  ↓
Understand the problem
  ↓
Fix the code
  ↓
Run again
```

---

# 17. Chapter Takeaways

By completing this chapter, we can explain:

- What the Python interpreter is.
- What the `>>>` prompt represents.
- How to execute a small Python snippet.
- How to execute a `.py` Python program.
- The difference between interactive Python and a saved program.
- How VS Code fits into the development workflow.
- What a traceback provides.
- What a `NameError` means in the example we encountered.
- What a `SyntaxError` means in the example we encountered.
- Why valid Python can still produce incorrect output.
- Why debugging requires understanding the problem rather than blindly changing code.

---

# 18. Interview-Style Review

## Q1. What is the difference between `python3` and `python3 hello_world.py`?

**Answer:**

`python3` starts the Python interpreter and allows Python statements to be entered interactively.

`python3 hello_world.py` starts Python and executes the code stored in the `hello_world.py` file.

---

## Q2. Why did `pritn("Hello Python World!")` produce a `NameError`?

**Answer:**

`print` is a built-in Python function, but `pritn` is not a defined name. Python therefore could not resolve the name and raised `NameError`.

---

## Q3. Why did `print("Hello Python Wrold!")` produce no error?

**Answer:**

`"Hello Python Wrold!"` is valid string data. Python does not interpret the contents of a string as Python names, so the spelling mistake inside the string does not cause a Python error.

---

## Q4. What does `SyntaxError` mean in the missing-parenthesis example?

**Answer:**

Python could not parse the code according to its syntax rules because the opening parenthesis did not have a matching closing parenthesis.

---

## Q5. What should you inspect first when reading a traceback?

**Answer:**

Start with:

1. The file where the problem occurred.
2. The line number.
3. The error type and description.

Then inspect the relevant code.

---

# 19. Chapter Completion Checklist

- [x] Python environment verified
- [x] Python version checked
- [x] Python interpreter used
- [x] Python snippet executed
- [x] `.py` program created
- [x] `.py` program executed
- [x] VS Code workflow verified
- [x] `NameError` introduced and fixed
- [x] Valid Python / incorrect output demonstrated
- [x] `SyntaxError` introduced and fixed
- [x] Traceback reading practiced
- [x] Interview-style review completed
- [x] Chapter documentation prepared

---

## Chapter Status

**Completed**

### Next Chapter

**Chapter 2 — Variables and Simple Data Types**
