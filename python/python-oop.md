# OOP

## Python Classes and Objects

**Class Definition**: A class is a blueprint for creating objects. It defines the behavior an object will have through its attributes and methods. Here is a basic example of a class definition in Python:

```python
class Dog:
    def __init__(self, name, age):
        self.name = name
        self.age = age

    def bark(self):
        print(f'{self.name.upper()} says woof woof!')
```

- **Class Names**: By convention, class names use PascalCase: each word starts with a capital letter and there are no underscores, as in Dog or ShoppingCart.
- **The `__init__()` Method**: Python calls __init__() automatically every time you create a new object. It's used to set up the object's initial attributes.
- **The `self` Parameter**: self refers to the specific object the method is working on. Python passes it automatically when you call a method on an object, so you don't write it in the call. self is the conventional name, but it's always the first parameter of an instance method.
- **Creating Objects**: Objects are instances of a class. They are created by calling the class with the necessary arguments.

```python
dog1 = Dog('Jack', 3)
dog2 = Dog('Thatcher', 5)

dog1.bark()  # JACK says woof woof!
dog2.bark()  # THATCHER says woof woof!
```

- **Calling Methods on Objects**: You can call methods on objects to perform actions or retrieve information.

```python
object_name1.method_name()
object_name2.method_name()
```

- **Difference Between Class and Object**: A class is a reusable template, while an object is a specific instance of that class with actual data.

### Attributes

- **Instance Attributes**: Usually defined in __init__() using self, and unique to each object.
- **Class Attributes**: Defined directly inside the class and shared by all instances.

```python
class Dog:
    species = 'French Bulldog'  # Class attribute

    def __init__(self, name):
        self.name = name  # Instance attribute

print(Dog.species) # French Bulldog

jack = Dog('Jack')
print(jack.name)     # Jack
print(jack.species)  # French Bulldog
```

- **Handling Attributes Dynamically**: Sometimes the attribute name is only known at runtime, for example when it comes from user input or a loop. In that case you can't write object.name, so you use functions that take the name as a string:

    - `getattr(obj, name)` returns the attribute's value. It raises an `AttributeError` if the attribute doesn't exist, unless you pass a default value as a third argument.

    - `setattr(obj, name, value)` creates or updates an attribute.

    - `hasattr(obj, name)` returns True if the attribute exists, otherwise False.

    - `delattr(obj, name)` deletes an attribute.

```python
class Dog:
    def __init__(self, name):
        self.name = name

dog = Dog('Jack')

print(getattr(dog, 'name'))            # Jack
print(getattr(dog, 'age', 'unknown'))  # unknown
getattr(dog, 'age')                    # AttributeError

setattr(dog, 'age', 3)
print(hasattr(dog, 'age'))  # True

delattr(dog, 'age')
print(hasattr(dog, 'age'))  # False
```

- **Inspecting Attributes with `dir()`**: The `dir()` function returns a list with the names of an object's attributes and methods. Combine it with `callable()` to separate methods from data attributes.

```python
class Dog:
    def __init__(self, name):
        self.name = name

    def bark(self):
        print('woof')

dog = Dog('Jack')
names = [n for n in dir(dog) if not n.startswith('__')]

print([n for n in names if callable(getattr(dog, n))])      # ['bark']
print([n for n in names if not callable(getattr(dog, n))])  # ['name']
```

### Methods

- **Methods**: Functions defined inside a class that operate on the object's attributes.

```python
class Car:
    def __init__(self, color, model):
        self.color = color
        self.model = model

    def describe(self):
        return f'This car is a {self.color} {self.model}'

my_car_1 = Car('red', 'Tesla Model S')
print(my_car_1.describe())  # This car is a red Tesla Model S
```

### Dunder (Magic) Methods

- **Definition**: Special methods that start and end with a double underscore (e.g., `__init__`, `__len__`, `__str__`, `__eq__`). Python uses them internally for built-in operations.

- **Behavior Without Custom Special Methods**: Python does not infer how built-in operations should use a custom object's attributes. It uses inherited default behavior where available and raises a `TypeError` for unsupported operations.

```python
class Book:
    def __init__(self, title, pages):
        self.title = title
        self.pages = pages

book1 = Book('Built Wealth Like a Boss', 420)
book2 = Book('Another Book', 420)

print(book1)           # <__main__.Book object at 0x...>
print(book1 == book2)  # False
len(book1)             # TypeError: object of type 'Book' has no len()
```

```python
class Book:
    def __init__(self, title, pages):
        self.title = title
        self.pages = pages

    def __len__(self):
        return self.pages

    def __str__(self):
        return f"'{self.title}' has {self.pages} pages"

    def __eq__(self, other):
        return self.pages == other.pages

book1 = Book('Built Wealth Like a Boss', 420)
print(len(book1))        # 420
print(str(book1))        # 'Built Wealth Like a Boss' has 420 pages
```

- **What the Custom Methods Change**:
  - `__len__()` makes `len()` return the page count instead of raising an error.
  - `__str__()` replaces the default representation with a readable summary.
  - `__eq__()` makes `==` compare the page counts instead of checking whether both names refer to the same object.

```python
book2 = Book('Another Book', 420)

print(book1 == book2)  # True
```

- **Calling dunder methods indirectly**: You don't need to call dunder methods directly. Instead, Python automatically calls them when certain actions happen. These operations include:

    - **arithmetic operations like addition, subtraction, multiplication, division, and others**. `__add__()` is called for addition, `__sub__()` for subtraction, `__mul__()` for multiplication, and `__truediv__()` for division.

    - **string operations like concatenation, repetition, formatting, and conversion to text**. `__add__()` is called for concatenation, `__mul__()` for repetition, `__format__()` for formatting, `__str__()` and `__repr__()` for text conversion, and so on.

    - **comparison operations like equality, less-than, greater-than, and others**. `__eq__()` is called for equality checks, `__lt__()` for less-than, `__gt__()` for greater-than, and so on.

    - **iteration operations like making an object iterable and advancing through items**. `__iter__()` is called to return an iterator and `__next__()` to fetch the next item.

**Example: Shopping Cart**

- **Cart Class with Dunder Methods**: Allows adding, removing, iterating, and checking contents with built-in behavior.

```python
class Cart:
    def __init__(self):
        self.items = []

    def add(self, item):
        self.items.append(item)

    def remove(self, item):
        if item in self.items:
            self.items.remove(item)
        else:
            print(f'{item} is not in cart')

    def list_items(self):
        return self.items

    def __len__(self):
        return len(self.items)

    def __getitem__(self, index):
        return self.items[index]

    def __contains__(self, item):
        return item in self.items

    def __iter__(self):
        return iter(self.items)

cart = Cart()
cart.add('Laptop')
print(len(cart))        # 1
print('Laptop' in cart) # True
```

### Objects Working Together

- **Passing Objects as Arguments**: Objects can be passed to other classes' constructors, just like numbers or strings.

- **Storing Objects in Attributes**: An object can be stored in another object's attribute. You can then call methods through that attribute by chaining the dot notation, as in `receiver.inbox.receive_email(email)`.

```python
class Email:
    def __init__(self, sender, receiver, body):
        self.sender = sender      # A User object
        self.receiver = receiver  # A User object
        self.body = body

class Inbox:
    def __init__(self):
        self.emails = []

    def receive_email(self, email):
        self.emails.append(email)

class User:
    def __init__(self, name):
        self.name = name
        self.inbox = Inbox()  # Each User gets its own Inbox object

sender = User('Ada')
receiver = User('Grace')

email = Email(sender, receiver, 'Hello!')
receiver.inbox.receive_email(email)

print(receiver.inbox.emails[0].body)         # Hello!
print(receiver.inbox.emails[0].sender.name)  # Ada
```

## Object-Oriented Programming

- **Object-oriented programming**: A programming style in which developers treat everything in their code like a real-world object. It is popularly called OOP. The four key principles that help you organize and manage code effectively are **encapsulation**, **inheritance**, **polymorphism**, and **abstraction**.

- **Classes**: The blueprint for creating objects. Every single object created from a class has attributes that define data and methods that determine the behaviors of the object.

### Encapsulation

- **Encapsulation**: The bundling of the attributes and methods of an object into a single unit. It lets you hide the internal state of the object behind a simple set of public methods and attributes that act like doors. Behind those doors are private attributes and methods that control how the data changes and who can see it.

- **Example of Encapsulation**: If you want to track a wallet balance, you will allow deposit and withdrawal, but you won't want anyone to tamper with the wallet balance itself:

```python
class Wallet:
   def __init__(self, balance):
       self.__balance = balance # Private attribute

   def deposit(self, amount):
       if amount > 0:
           self.__balance += amount # Add to the balance safely

   def withdraw(self, amount):
       if 0 < amount <= self.__balance:
           self.__balance -= amount # Remove from the balance safely

account = Wallet(500)
print(account.__balance) # AttributeError: 'Wallet' object has no attribute '__balance'
```

- **Difference Between Prefixing Attributes with Single and Double Underscore**: Prefixing attributes and methods with a single underscore signals that they are meant for internal use. This is only a convention, and Python doesn't restrict access to them from outside the class. Prefixing attributes and methods with a double underscore triggers name mangling, which renames `__balance` to `_Wallet__balance`. This helps avoid accidental name collisions in subclasses, but it doesn't make outside access impossible:

```python
print(account._Wallet__balance) # 500
```

### Getters and Setters

- **Getters and Setters**: Methods that let you control how the attributes of a class are accessed and modified. You retrieve values with getters and you set values with setters.

- **Properties**: They connect getters and setters, and allow access to data. They run extra logic behind the scenes when you get, set, or delete values.

- **Why Properties Instead of Methods**: Properties are used instead of methods for better readability and cleaner code. They let you access values with dot notation, like regular attributes, without parentheses.

- **Decorators**: A decorator is a function that modifies or wraps other functions, or classes, without changing their original code. You apply a decorator by placing **@decorator_name** directly above a function or class definition. For example, placing the **@property** decorator above a method turns it into a property, so it can be accessed like an attribute while internally calling the decorated method.

- **Creating a Getter**: To create a getter, you use the **@property** decorator. Here's a getter that gets the radius of a circle:

```python
class Circle:
    def __init__(self, radius):
        self._radius = radius

    @property
    def radius(self): # A getter to get the radius
        return self._radius

    @property
    def area(self):  # A getter to calculate area
        return 3.14 * (self._radius ** 2)

my_circle = Circle(3)

print(my_circle.radius) # 3
print(my_circle.area) # 28.26
```

- **Creating a Setter**: To create the setter that will set the radius, you have to define another method with the same name and use `@<property_name>.setter` above it:

```python
class Circle:
    def __init__(self, radius):
        self.radius = radius

    @property
    def radius(self):  # A getter to get the radius
        return self._radius

    @radius.setter
    def radius(self, value):  # A setter to set the radius
        if value <= 0:
            raise ValueError('Radius must be positive')
        self._radius = value

my_circle = Circle(3)
print('Initial radius:', my_circle.radius) # Initial radius: 3

my_circle.radius = 8
print('After modifying the radius:', my_circle.radius) # After modifying the radius: 8
```

- **How Python Handles Getters and Setters**: Once you define getters and setters, Python automatically calls them under the hood whenever you use normal attribute syntax this way:

```python
my_circle.radius # This will call the getter
my_circle.radius = 4 # This will call the setter
```

Inside the setter, you should not assign to the property name itself because that will cause a `RecursionError`.

- **Deleter**: After setting and getting a value with setter and getter, you can control how it is deleted with a `deleter`. A deleter runs custom logic when you use the `del` statement on a property. To create a deleter, you use the `@<property_name>.deleter` decorator.

```python
# Deleter
    @radius.deleter
    def radius(self):
        print("Deleting radius...")
        del self._radius
```

### Inheritance

- **Inheritance**: The process by which a child class uses the attributes and methods of a parent class. Inheritance promotes code reuse, provides clear hierarchies, and customizes behavior without rewriting everything. To implement inheritance, a child class takes in the name of a parent class:

```python
class Parent:
    # Parent attributes and methods

class Child(Parent):
    # Child inherits, extends, and/or overrides where necessary
```

- **Single and Multiple Inheritance**: When a child class inherits properties and methods from a single parent, as you can see above, the process is called **single inheritance**. When a child class inherits properties and methods from more than one parent, that is **multiple inheritance**. Here's the syntax for that:

```python
class Parent:
    # Attributes and methods for Parent

class Child:
    # Attributes and methods for Child

class GrandChild(Parent, Child):
    # GrandChild inherits from both Parent and Child
    # GrandChild can combine or override behavior from each
```

- **`super()` Function**: A function that lets you call a method from a parent class, when a class has a different implementation of that method, or it extends the method, without duplicating code.

### Polymorphism

- **Polymorphism**: The OOP principle that lets different classes use the same method name, but each class implements it differently when called. Here's the syntax for it:

```python
class A:
   def action(self): ...

class B:
   def action(self): ...

class C:
   def action(self): ...

Class().method()  # Works for A, B, or C
```

- **Inheritance-based polymorphism**: A parent sets up a method, and each child class twists it to their use.

### Name Mangling

- **Name Mangling**: A process in which Python internally renames an attribute prefixed with a double underscore by adding an underscore and the class name as a prefix, turning `__attribute` into `_ClassName__attribute`.

- **The Purpose of Name Mangling**: The main purpose of name mangling is to prevent accidental attribute and method overriding when you use inheritance. Here's a code example that makes that more understandable:

```python
class Parent:
    def __init__(self):
        self.__data = 'Parent data'

class Child(Parent):
    def __init__(self):
        super().__init__()
        self.__data = 'Child data'

c = Child()
print(c.__dict__) # {'_Parent__data': 'Parent data', '_Child__data': 'Child data'}
```

```python
class Parent:
    def __init__(self):
        self.__data = 'Parent data'

class Child(Parent):
    def __init__(self):
        super().__init__()
        self.__data = 'Child data'

c = Child()
print(c.__dict__) # {'_Parent__data': 'Parent data', '_Child__data': 'Child data'}
```

### Abstraction

- **Abstraction**: A programming concept in which complex implementation details of an object or system are hidden and only the essential features are shown. In Python and other programming languages, abstraction simplifies complex systems by increasing reusability.

- **Example of Abstraction**: A good example of abstraction in everyday life is a car letting you just use the wheel, pedals, and shifter without knowing how the engine or brakes work.

- **How Python Implements Abstraction**: You can create abstractions with ordinary functions and classes by hiding implementation details behind a simple interface. For more formal interfaces, Python's `abc` module provides the `ABC` helper class and the `@abstractmethod` decorator. An abstract base class defines the common methods and properties that concrete subclasses are expected to provide.

- **How Abstract Methods Are Defined**: An abstract method is defined with `@abstractmethod`. A class can only be instantiated if it provides or inherits concrete implementations of all its abstract methods. A subclass that leaves any abstract method unimplemented remains abstract. An abstract method can still have a default implementation, which subclasses can call with `super()`. Inheriting from `ABC` alone doesn't block instantiation: `ABC()` and subclasses with no abstract methods can be instantiated. The basic syntax of abstraction looks like this:

```python
from abc import ABC, abstractmethod

# Define an abstract base class
class AbstractClass(ABC):
    @abstractmethod
    def abstract_method(self):
        pass

# Concrete subclass that implements the abstract method
class ConcreteClassOne(AbstractClass):
    def abstract_method(self):
        print('Implementation in ConcreteClassOne')

# Another concrete subclass
class ConcreteClassTwo(AbstractClass):
    def abstract_method(self):
        print('Implementation in ConcreteClassTwo')

AbstractClass() # TypeError
ConcreteClassOne().abstract_method() # Implementation in ConcreteClassOne
```

### Object Representations

- **`__repr__` Method**: A special method that returns a string representation of an object. Ideally, that string looks like the code used to create the object.
  + For example, `Employee('Charlie', 'developer')` should be represented as `Employee('Charlie', 'developer')`.
- **`repr() Function`**: When you call `repr()` on an object, Python calls that object's `__repr__` method under the hood. For strings, `repr()` adds quotes and escapes any characters that need it:

```python
print(repr("Charlie"))  # 'Charlie'
print(repr("O'Reilly"))  # "O'Reilly"
print("C:\\new", repr("C:\\new"))  # C:\new 'C:\\new'
```

- **`!r` Conversion**: Inside an f-string, adding `!r` after an expression applies `repr()` to it. Using `!r` in `__repr__` keeps the representation valid when a value contains quotes or backslashes, unlike wrapping values in quotes by hand:

```python
class Employee:
    def __init__(self, name, level):
        self.name = name
        self.level = level

    def __repr__(self):
        return f"Employee({self.name!r}, {self.level!r})"


print(repr(Employee("O'Reilly", "junior")))  # Employee("O'Reilly", 'junior')
```

### Type Checks

**`isinstance()` vs. `type()`**: `isinstance(obj, ClassName)` returns `True` if `obj` is an instance of `ClassName` or any of its subclasses, because it considers the full inheritance chain. To check for one exact class, compare `type(obj)` instead:

```python
class Movie:
    pass


class TVSeries(Movie):
    pass


series = TVSeries()
print(isinstance(series, Movie))  # True
print(type(series) == Movie)  # False
print(type(series) == TVSeries)  # True
```

## Custom Exceptions with Extra Context

**Storing Context on an Exception**: A custom exception can accept extra data along with its message. Calling `super().__init__(message)` lets the built-in `Exception` class store and display the message, and you can then store the extra data as an attribute. When you catch the exception, you can read that attribute to help with debugging:

```python
class MediaError(Exception):
    """Custom exception for media-related errors."""

    def __init__(self, message, obj):
        super().__init__(message)
        self.obj = obj


try:
    raise MediaError("Only Movie or TVSeries instances can be added", 42)
except MediaError as e:
    print(
        f"Media Error: {e}"
    )  # Media Error: Only Movie or TVSeries instances can be added
    print(f"Unable to add {e.obj}: {type(e.obj)}")  # Unable to add 42: <class 'int'>
```

# Class methods

Class methods operate on the class itself rather than on a specific instance, allowing access to and modification of shared class attributes

`@classmethod` - a decorator that defines a class method

`cls` - refers to the class on which the method is called, just as `self` refers to an individual object

```python
class Customer:
    total_customers = 0

    def __init__(self, name: str) -> None:
        self.name = name
        Customer.total_customers += 1

    @classmethod
    def get_total_customers(cls) -> int:
        return cls.total_customers


cust1 = Customer("Tamas")
cust2 = Customer("Anna")

print(Customer.get_total_customers())  # 2
print(cust1.get_total_customers())  # 2
```

# Static methods

Static methods define operations associated with a class without requiring access to a specific object or the class itself

`@staticmethod` - a decorator used to define a static method inside a class

**No self or cls** - Static methods receive neither the instance nor the class as an implicit first argument

```python
class Person:
    def __init__(self, name: str, age: int):
        self.name = name
        self.age = age

    @staticmethod
    def is_adult(age: int) -> bool:
        return age >= 18


per1 = Person("Tamas", 19)

print(Person.is_adult(per1.age))  # True
print(Person.is_adult(17))  # False
```

# Object Composition and Interactions

**Object Composition** - An object can contain other objects as attributes

**Nested Attributes** - Access attributes of referenced objects using object.attribute.attribute

**Passing Objects to Methods** - Methods can receive other objects as arguments

**Object Interactions** - Methods can invoke methods belonging to other objects

```python
import uuid


class Person:
    def __init__(self, name, age):
        self.name = name
        self.age = age

    def __str__(self) -> str:
        return f"I'm {self.name}, {self.age} years old"


class Customer:
    def __init__(self, person: Person):
        self.id = uuid.uuid4()
        self.personal_info = person


per1 = Person("Tamas", 25)
cust1 = Customer(per1)

print(cust1.id)  # Random uuid
print(cust1.personal_info.name)  # Tamas
print(cust1.personal_info)  # I'm Tamas, 25 years old
```
