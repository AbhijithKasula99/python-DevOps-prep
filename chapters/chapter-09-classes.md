# Chapter 9 --- Classes

**Study notes based on *Python Crash Course, 3rd Edition* by Eric
Matthes, plus the examples practiced during this chapter.**

## 1. Classes and instances

A **class** is a blueprint that defines attributes and methods. An
**instance** (object) is a specific object created from that class.

``` python
class Dog:
    def __init__(self, name, age):
        self.name = name
        self.age = age

    def sit(self):
        print(f"{self.name} is now sitting.")

my_dog = Dog("Willie", 6)
my_dog.sit()
print(my_dog.age)
```

-   `class Dog:` defines the class.
-   `__init__()` initializes a new instance.
-   `self` refers to the instance being worked on.
-   `self.name` and `self.age` are instance attributes.
-   `sit()` is a method.
-   `my_dog` is an instance of `Dog`.

## 2. Creating and using classes

``` python
class Restaurant:
    def __init__(self, restaurant_name, cuisine_type):
        self.restaurant_name = restaurant_name
        self.cuisine_type = cuisine_type

    def describe_restaurant(self):
        print(f"{self.restaurant_name} serves {self.cuisine_type} food.")

    def open_restaurant(self):
        print(f"{self.restaurant_name} is open.")
```

Create instances with different data:

``` python
restaurant1 = Restaurant("Meghana Foods", "Hyderabadi")
restaurant2 = Restaurant("Waga Mama", "Japanese")

restaurant1.describe_restaurant()
restaurant2.describe_restaurant()
```

Each instance stores its own attribute values.

## 3. Changing attribute values

An attribute can be changed directly:

``` python
my_car.year = 2027
```

Or through a method:

``` python
def update_year(self, year):
    self.year = year
```

A method is useful when you want to control how an attribute is changed.

## 4. Tracking values with attributes and methods

### Number served

``` python
class Restaurant:
    def __init__(self, restaurant_name, cuisine_type):
        self.restaurant_name = restaurant_name
        self.cuisine_type = cuisine_type
        self.number_served = 0

    def set_number_served(self, number):
        self.number_served = number

    def increment_number_served(self, number):
        self.number_served += number
```

### Login attempts

``` python
class User:
    def __init__(self, first_name, last_name, login_attempts=0):
        self.first_name = first_name
        self.last_name = last_name
        self.login_attempts = login_attempts

    def increment_login_attempts(self):
        self.login_attempts += 1

    def reset_login_attempts(self):
        self.login_attempts = 0
```

-   An attribute can store the current state.
-   A method can update that state.
-   A default argument such as `login_attempts=0` is used when no value
    is supplied.

## 5. Inheritance

**Inheritance** lets a child class reuse attributes and methods from a
parent class.

``` python
class Car:
    def __init__(self, make, model, year):
        self.make = make
        self.model = model
        self.year = year

    def describe_car(self):
        print(f"{self.year} {self.make} {self.model}")


class ElectricCar(Car):
    def __init__(self, make, model, year):
        super().__init__(make, model, year)
        self.battery_size = 75
```

-   `class ElectricCar(Car):` means `ElectricCar` inherits from `Car`.
-   `super().__init__(...)` calls the parent class constructor.
-   Pass all required arguments expected by the parent constructor.
-   The child class can add its own attributes and methods.
-   A child class can override a parent method by defining a method with
    the same name.

## 6. Composition --- an object as an attribute

**Composition** means one object contains another object. In the
examples, an electric car has a battery.

``` python
class Battery:
    def __init__(self, battery_size=40):
        self.battery_size = battery_size

    def get_range(self):
        if self.battery_size == 40:
            car_range = 150
        elif self.battery_size == 65:
            car_range = 225
        else:
            print("Range couldn't be determined")
            return

        print(f"This car can go about {car_range} miles on a full charge.")


class ElectricCar:
    def __init__(self, make, model, year):
        self.make = make
        self.model = model
        self.year = year
        self.battery = Battery()
```

Usage:

``` python
my_car = ElectricCar("Tesla", "Model 3", 2026)
my_car.battery.get_range()
```

`my_car.battery` accesses the `Battery` instance contained in the
`ElectricCar` instance. Since `get_range()` belongs to `Battery`, it is
called through `my_car.battery`.

### Battery upgrade

``` python
def upgrade_battery(self):
    if self.battery_size != 65:
        self.battery_size = 65
```

After `my_car.battery.upgrade_battery()`, calling
`my_car.battery.get_range()` reports the range for the 65-kWh battery.

## 7. Separate responsibilities with composition

An administrator is a user, and an administrator has privileges:

``` python
class Privileges:
    def __init__(self):
        self.privileges = ["create", "delete", "modify", "update"]

    def show_privileges(self):
        for privilege in self.privileges:
            print(privilege)


class Admin(User):
    def __init__(self, first_name, last_name, role, location, login_attempts=0):
        super().__init__(first_name, last_name, role, location, login_attempts)
        self.privileges = Privileges()
```

Usage:

``` python
u1 = Admin("Abhijith", "Kasula", "AIOps Engineer", "Bengaluru")
u1.privileges.show_privileges()
```

-   `Admin(User)` demonstrates inheritance: an admin **is a** user.
-   `self.privileges = Privileges()` demonstrates composition: an admin
    **has a** privileges object.
-   `u1.privileges.show_privileges()` accesses the object and calls its
    method.

## 8. Importing classes and using modules

A **module** is a Python file that can define reusable classes and
functions.

For example, `rest.py` contains the `Restaurant` class:

``` python
class Restaurant:
    def __init__(self, restaurant_name, cuisine_type):
        self.restaurant_name = restaurant_name
        self.cuisine_type = cuisine_type

    def describe_restaurant(self):
        print(f"{self.restaurant_name} serves {self.cuisine_type} food.")
```

A separate file can import and use it:

``` python
from rest import Restaurant

my_restaurant = Restaurant("Meghana Foods", "Hyderabadi")
my_restaurant.describe_restaurant()
```

### Classes split across modules

Example project layout:

``` text
python-DevOps-prep/
├── privileges.py
├── user1.py
└── admin_test.py
```

-   `privileges.py` defines `Privileges`.
-   `user1.py` imports `Privileges` and defines `User` and `Admin`.
-   `admin_test.py` imports `Admin` and runs the test.

``` python
# user1.py
from privileges import Privileges
```

``` python
# admin_test.py
from user1 import Admin

u1 = Admin("Abhijith", "Kasula", "AIOps Engineer", "Bengaluru")
u1.privileges.show_privileges()
```

**Important:** When a module is imported, Python executes its top-level
statements. Keep test-only object creation and method calls out of
reusable module files, or they will run during import.

## 9. Python standard-library modules

### `random`

`random.randint(a, b)` returns a random integer, including both
endpoints.

``` python
import random

num = random.randint(1, 6)
print(num)
```

A configurable die:

``` python
import random

class Die:
    def __init__(self, sides=6):
        self.sides = sides

    def roll_die(self):
        num = random.randint(1, self.sides)
        print(num)

throw = Die(20)
i = 1

while i <= 5:
    throw.roll_die()
    i += 1
```

-   `Die()` creates a six-sided die by default.
-   `Die(20)` creates a 20-sided die.
-   Use `self.sides` rather than hardcoding `6` so the class works with
    different side counts.

### `random.choice()`

`random.choice(sequence)` selects one item from a sequence.

``` python
import random

lottery = [7, 12, 23, "A", "B", 35]
print(random.choice(lottery))
```

Repeated calls can select the same item because `choice()` does not
remove it from the original list.

### List equality

``` python
a = [7, 12, 23]
b = [7, 12, 23]
print(a == b)  # True
```

List equality compares the elements in order. Matching membership alone
does not mean two lists are equal.

### Lottery-attempt loop

``` python
while winning_ticket != my_ticket and attempt < 1000:
    attempt += 1
    i = 0
    my_ticket = []

    while i < 4:
        my_ticket.append(random.choice(lottery))
        i += 1

if winning_ticket == my_ticket:
    print(attempt)
else:
    print("Max limit reached")
```

This stops when a matching ticket is generated or the attempt limit is
reached. The ticket is generated with replacement, so repeated items are
possible.

### `pathlib`

`pathlib.Path` represents filesystem paths.

``` python
from pathlib import Path

print(Path.cwd())                 # Current working directory
print(Path("dice.py").exists())   # True if the path exists
print(Path("missing.py").exists())
```

-   `Path.cwd()` returns the current working directory.
-   `.exists()` returns `True` if the path exists and `False` otherwise.

## 10. Common mistakes to remember

-   Use `self.attribute` to access instance attributes inside instance
    methods.
-   Call a method on an instance, such as `throw.roll_die()`.
-   If a loop starts at `0`, `while i <= 10` runs 11 times. For exactly
    10 iterations, choose a consistent counter and condition.
-   Reset the counter and list at the correct point when repeating an
    operation.
-   Avoid printing an object directly when you want a particular
    attribute; `print(my_car)` typically shows an object representation.
-   Use `self.sides` rather than a fixed `6` in a configurable die.
-   Don't import a class and also define it again in the same module.
-   Keep module-level test code from running unintentionally during
    imports.
-   `range` is a built-in name; use a descriptive variable such as
    `car_range` for a calculated distance.

## 11. Interview recap

1.  **What is a class?** A blueprint defining attributes and methods.
2.  **What is an instance?** An object created from a class.
3.  **What is `self`?** A reference to the current instance.
4.  **What does `__init__()` do?** Initializes instance attributes when
    an object is created.
5.  **What is inheritance?** A child class reuses or extends a parent
    class.
6.  **What does `super().__init__()` do?** Calls the parent constructor.
7.  **What is composition?** An object contains another object as an
    attribute.
8.  **What is a module?** A Python file that can be imported to reuse
    code.
9.  **What happens to top-level statements during import?** They execute
    when the module is imported.
10. **What does `random.randint(1, 6)` return?** A random integer from 1
    through 6, inclusive.
11. **What does `random.choice(items)` do?** Selects one random item
    from a sequence.
12. **What does `Path("file.py").exists()` return?** A Boolean
    indicating whether that path exists.

## Chapter checklist

-   [x] Create classes and instances
-   [x] Initialize and update attributes
-   [x] Write instance methods
-   [x] Use inheritance and `super()`
-   [x] Override a method
-   [x] Use composition and instances as attributes
-   [x] Import classes from modules
-   [x] Organize related classes across files
-   [x] Use `random` for dice and lottery exercises
-   [x] Use `pathlib` to inspect filesystem paths
-   [x] Answer introductory class and module interview questions
