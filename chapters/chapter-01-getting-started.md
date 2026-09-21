# Chapter 1 — Getting Started

> **Source:** *Python Crash Course, 3rd Edition* — Eric Matthes

## 1. Chapter Overview

Chapter 1 introduces the Python programming environment and the basic workflow for writing and running Python programs.

Topics covered:

- Setting up the programming environment
- Checking the Python version
- Running Python snippets
- Using the Python interpreter
- Running Python programs from `.py` files
- Running a Hello World program
- Basic troubleshooting
- Understanding Python error messages

---

## 2. Environment Setup

| Component | Configuration |
|---|---|
| OS | WSL / Linux |
| Python | 3.14.4 |
| Shell | Bash |
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

Python was also located with:

```bash
which python3
```

Output:

```text
/usr/bin/python3
```

---

## 3. Running Python Code

Python code can be executed in different ways.

### 3.1 Python Interpreter

Start the interpreter:

```bash
python3
```

The interpreter displays the Python prompt:

```text
>>>
```

Example:

```python
>>> print("Hello Python interpreter!")
Hello Python interpreter!
```

The Python interpreter executes the statement immediately.

Exit the interpreter with:

```python
exit()
```

---

## 4. Running a Python Snippet from the Shell

A small piece of Python code can be executed directly from the Linux shell using `-c`.

Example:

```bash
python3 -c 'print("Executed directly")'
```

Output:

```text
Executed directly
```

This is useful for quickly testing a small piece of Python code without creating a Python file.

---

## 5. Creating a Python Program

Python programs are stored in files ending with:

```text
.py
```

Our first Python program is:

```text
hello_world.py
```

The program contains:

```python
print("Hello Python World!")
print("I am learning python.")
print("I will build production software.")
```

Run the program with:

```bash
python3 hello_world.py
```

Output:

```text
Hello Python World!
I am learning python.
I will build production software.
```

---

## 6. Interpreter vs `.py` File

There are two different workflows we practiced.

### Interactive interpreter

```text
python3
   ↓
>>>
   ↓
Python code
   ↓
Immediate output
```

### Python program

```text
hello_world.py
   ↓
python3 hello_world.py
   ↓
Python executes the file
   ↓
Output
```

The interpreter is useful for experimenting with small pieces of code.

A `.py` file is used to save a complete Python program.

---

# 7. Troubleshooting and Tracebacks

A major part of programming is learning how to understand errors.

We intentionally introduced an error into `hello_world.py`.

The correct code was:

```python
print("Hello Python World!")
```

We changed it to:

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

---

## 8. Reading the Traceback

The traceback gave us several useful pieces of information.

### File

```text
hello_world.py
```

### Line

```text
line 1
```

### Problematic code

```python
pritn("Hello Python World!")
```

### Error type

```text
NameError
```

### Explanation

```text
name 'pritn' is not defined
```

Python even suggested:

```text
Did you mean: 'print'?
```

The problem was a spelling mistake:

```text
pritn
```

instead of:

```text
print
```

We corrected the mistake and successfully ran the program again.

---

# 9. Valid Python but Incorrect Output

We then tested a different kind of mistake.

The correct program contained:

```python
print("Hello Python World!")
```

We changed it to:

```python
print("Hello Python Wrold!")
```

The program executed successfully:

```text
Hello Python Wrold!
I am learning python.
I will build production software.
```

There was no Python error.

Why?

Because:

```python
"Hello Python Wrold!"
```

is valid string data.

Python does not know that `Wrold` was intended to be `World`.

We corrected the string afterwards.

---

# 10. Important Lesson

A program running without an error does **not** necessarily mean that the program is correct.

There are at least two different situations we observed:

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

This distinction is important when debugging real software.

---

# 11. Commands Practiced

### Check Python version

```bash
python3 --version
```

### Find Python

```bash
which python3
```

### Start Python interpreter

```bash
python3
```

### Execute a Python snippet

```bash
python3 -c 'print("Executed directly")'
```

### Run a Python program

```bash
python3 hello_world.py
```

### Edit a file

```bash
nano hello_world.py
```

---

# 12. Git Repository Setup

During this chapter we also established the learning repository.

Repository:

```text
python-genai-prep
```

Git branch:

```text
main
```

The repository was connected to GitHub using SSH.

The first commit was:

```text
Start Python fundamentals
```

The repository was successfully pushed to GitHub.

---

# 13. First Program

Our first Python program:

```python
print("Hello Python World!")
print("I am learning python.")
print("I will build production software.")
```

This program is intentionally simple. Its purpose is to verify that the complete workflow works:

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
Fix error
  ↓
Run again
```

---

# 14. Exercises Completed

- [x] Verify Python installation
- [x] Check Python version
- [x] Locate Python using `which`
- [x] Start the Python interpreter
- [x] Execute Python code interactively
- [x] Exit the Python interpreter
- [x] Execute a Python snippet using `python3 -c`
- [x] Create `hello_world.py`
- [x] Execute a `.py` file
- [x] Introduce an intentional `NameError`
- [x] Read a traceback
- [x] Identify the error
- [x] Fix the error
- [x] Create a valid but incorrect string
- [x] Observe that Python does not detect the incorrect meaning
- [x] Correct the program

---

# 15. Key Takeaways

1. `python3` starts the Python interpreter.
2. `>>>` indicates the Python interpreter prompt.
3. `python3 -c` can execute a small Python snippet directly.
4. Python programs are commonly stored in `.py` files.
5. `python3 filename.py` executes a Python program.
6. Tracebacks help identify where Python encountered an error.
7. `NameError` can occur when Python encounters an unknown name.
8. A program can execute successfully and still produce incorrect output.
9. Debugging requires understanding the problem rather than blindly fixing it.

---

## Chapter Status

**Completed**

Next:

**Chapter 2 — Variables and Simple Data Types**
