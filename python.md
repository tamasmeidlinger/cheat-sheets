- [Todo](#todo)
- [String](#string)
  - [str.strip()](#strstrip)
  - [str.replace()](#strreplace)
  - [str.split()](#strsplit)
  - [str.join()](#strjoin)
  - [str.startswith() \& str.endsswith()](#strstartswith--strendsswith)
  - [str.find()](#strfind)
  - [str.count()](#strcount)
  - [upper(), lower(), capitalize(), title()](#upper-lower-capitalize-title)
  - [isupper(), islower()](#isupper-islower)
  - [str.maketrans()](#strmaketrans)
- [List](#list)
  - [Adding items](#adding-items)
  - [Removing items](#removing-items)
  - [Check if an Element Exists in a List](#check-if-an-element-exists-in-a-list)
  - [Unpacking Values from a List](#unpacking-values-from-a-list)
  - [Other](#other)
    - [sort()](#sort)
    - [reverse()](#reverse)
    - [index()](#index)
    - [count()](#count)
- [Dictionary](#dictionary)
  - [get()](#get)
  - [keys(), values()](#keys-values)
  - [items()](#items)
  - [pop()](#pop)
  - [update()](#update)
  - [setdefault()](#setdefault)
  - [Looping Over a Dictionary](#looping-over-a-dictionary)
  - [Unpacking a Dictionary](#unpacking-a-dictionary)
    - [Unpack values from a dictionary](#unpack-values-from-a-dictionary)
    - [Unpacking a dictionary with `**`](#unpacking-a-dictionary-with-)
    - [Unpacking a custom object](#unpacking-a-custom-object)
- [Sets](#sets)
  - [Methods](#methods)
    - [add()](#add)
    - [remove(), discard()](#remove-discard)
    - [clear()](#clear)
  - [Mathematical Set Operations](#mathematical-set-operations)
    - [Subset, Superset](#subset-superset)
    - [Disjoint](#disjoint)
    - [Union](#union)
    - [Intersection](#intersection)
    - [Difference](#difference)
    - [Symmetric Difference](#symmetric-difference)
    - [Existance](#existance)
  - [Immutable Sets - frozenset](#immutable-sets---frozenset)
- [Comprehensions](#comprehensions)
  - [List Comprehension](#list-comprehension)
  - [Set Comprehension](#set-comprehension)
  - [Dictionary Comprehension](#dictionary-comprehension)
- [Built-ins](#built-ins)
  - [sorted()](#sorted)
  - [range()](#range)
  - [enumerate()](#enumerate)
  - [all() / any()](#all--any)
  - [filter()](#filter)
  - [map()](#map)
  - [isinstance()](#isinstance)
  - [ord()](#ord)
  - [chr()](#chr)
  - [dir()](#dir)
  - [hash()](#hash)
  - [id()](#id)
- [Typing](#typing)
  - [Basic Types](#basic-types)
  - [Collection Types](#collection-types)
  - [Nested Collections](#nested-collections)
  - [Union and Optional Types](#union-and-optional-types)
  - [Function Annotations](#function-annotations)
  - [Useful Types from `typing`](#useful-types-from-typing)
  - [Type Aliases and Generics](#type-aliases-and-generics)
- [Bitwise Operations \& Binary Data](#bitwise-operations--binary-data)
  - [Conversions](#conversions)
  - [Formatting binary numbers](#formatting-binary-numbers)
  - [Bitwise operators](#bitwise-operators)
    - [Bitwise `AND`, `OR`, `XOR`](#bitwise-and-or-xor)
    - [Bitwise `NOT`](#bitwise-not)
    - [Inverting bits](#inverting-bits)
    - [Bitwise `SHIFT`](#bitwise-shift)
    - [The four fundamental bit operations](#the-four-fundamental-bit-operations)
    - [Checking whether a bit is set](#checking-whether-a-bit-is-set)
    - [Setting a bit](#setting-a-bit)
    - [Clearing a bit](#clearing-a-bit)
    - [Toggling a bit](#toggling-a-bit)
  - [Subnetting example](#subnetting-example)
- [Python Imports \& Packages](#python-imports--packages)
  - [Directory overview](#directory-overview)
  - [Imports in a file](#imports-in-a-file)
  - [Imports in `__init__.py`](#imports-in-__init__py)
  - [Running separate modules in a package](#running-separate-modules-in-a-package)
  - [Absolute vs. Relative Imports](#absolute-vs-relative-imports)
    - [Directory structure](#directory-structure)
    - [Absolute Imports](#absolute-imports)
    - [Relative Imports](#relative-imports)
    - [Running a Module](#running-a-module)

## Todo

- [ ] vars() builtins
- [ ] split() limit
- [ ] OOP
- [ ] Python import path - how to add things
- [ ] Python Standard Library
- [ ] dataclass
- [ ] sys
- path
- getsizeof
- [ ] pathlib
- stdin/stdout
- platform
- [ ] subprocess
- [ ] os
- sys.path.append(os.path.dirname(**file**))
- [ ] special variable like **file**
- [ ] file openings
- [ ] function args and kwargs spreading and stuff
- [ ] Add the below example, why does this work

```python
my_list = [1, 2, 5]

my_list[2:2] = [3, 4]

print(my_list)
```

## String

### str.strip()

**strip()** - returns a copy of the string with specified leading and trailing characters removed

> [!important]
> if no argument is passed to the method, it removes leading and trailing whitespace.

```python
greeting = '  hello world  '

trimmed_my_str = greeting.strip()
print(trimmed_my_str)  # 'hello world'
```

```python
greeting = "aaahello worldaaa"

trimmed_greeting = greeting.strip("a")
print(trimmed_greeting)  # hello world
```

### str.replace()

**replace()** - returns a new string with all occurrences of the old string replaced by a new one

```python
greeting = "hello, hello everyone"

replaced_my_str = greeting.replace("hello", "hi")
print(replaced_my_str)  # hi, hi everyone
```

### str.split()

**split()** - split a string into a list using a specified separator

A separator is a string specifying where the split should happen. If no separator is specified, `split()` splits on whitespace.

```python
dashed_name = "example-dashed-name"
whitespace_name = "example dashed name"

split_words_dashed = dashed_name.split("-")
split_words_whitespace = whitespace_name.split()

print(split_words_dashed)  # ['example', 'dashed', 'name']
print(split_words_whitespace)  # ['example', 'dashed', 'name']
```

### str.join()

**join()** - join a collection of strings into one string with a separator

```python
example_list = ["example", "dashed", "name"]

joined_space = " ".join(example_list)  # example dashed name
joined_no_sep = "".join(example_list)  # exampledashedname
```

### str.startswith() & str.endsswith()

**str.startswith(prefix) and str.endswith(suffix)** - returns a boolean indicating if a string starts/ends with the specified suffix, respectively

```python
name = "Tamas"

name.startswith("t")  # False
name.startswith("T")  # True
name.startswith("To")  # False

name.endswith("as")  # True
name.endswith("i")  # False
```

### str.find()

**find()** - returns the index of the first occurrence of a substring

If one is not found, then -1 is returned

```python
developer = 'Naomi'

result = developer.find('N')
print(result)  # 0

city = 'Los Angeles'
print(city.find('New')) # -1
```

### str.count()

**str.count(substring)** - counts how many times a substring appears in a string

```python
city = 'Los Angeles'
print(city.count('e')) # 2
```

### upper(), lower(), capitalize(), title()

**upper(), lower(), capitalize(), title()** - case characters in different ways

```python
greeting = "hello World !"

greeting.upper()  # HELLO WORLD !
greeting.lower()  # hello world !
greeting.capitalize()  # Hello world !
greeting.title()  # Hello World !
```

### isupper(), islower()

**isupper(), islower()** - returns `True` if the string contains at least one cased character and all cased characters are upper/lowercase, respectively

```python
dessert = 'chocolate cake'
print(dessert.isupper()) # False
```

```python
dessert = 'chocolate cake'
print(dessert.islower()) # True
```

### str.maketrans()

**str.maketrans()** - `str.maketrans()` creates a table of one-to-one character mappings

It is often used with `translate()`, which applies the table to a string and returns the translated result.

```python
trans_table = str.maketrans("tomi", "1234")
print(trans_table)  # {116: 49, 111: 50, 109: 51, 105: 52}

result_1 = "tomi".translate(trans_table)  # 1234
result_2 = "imot".translate(trans_table)  # 4321
result_3 = "tomika".translate(trans_table)  # 1234ka
```

## List

### Adding items

**append()** - add an item to the end of the list

```python
numbers = [1, 2, 3, 4, 5]
numbers.append(6)
print(numbers) # [1, 2, 3, 4, 5, 6]
```

**extend()** - add multiple items to the end of a list

```python
numbers = [1, 2, 3, 4, 5]
even_numbers = [6, 8, 10]

numbers.extend(even_numbers)
print(numbers) # [1, 2, 3, 4, 5, 6, 8, 10]
```

**insert(_index, item_)** - insert an item at a specific index in the list

```python
numbers = [1, 2, 3, 4, 5]
numbers.insert(2, 2.5)

print(numbers) # [1, 2, 2.5, 3, 4, 5]
```

### Removing items

**remove()** - remove an item from the list

> [!warning]
> Only removes the first occurrence of an item in the list.

```python
numbers = [1, 2, 3, 4, 5, 5, 5]
numbers.remove(5)

print(numbers) # [1, 2, 3, 4, 5, 5]
```

**pop(_index_)** - remove a specific item from the list and return it

> [!note]
> If you don't specify an element for the pop method, then the last element is removed.

```python
numbers = [1, 2, 3, 4, 5]
numbers.pop(1) # The number 2 is returned
```

**del keyword** - elements can be removed from a list using the `del` keyword

```python
developer = ['Jane Doe', 23, 'Python Developer']
del developer[1]
print(developer) # ['Jane Doe', 'Python Developer']
```

**clear()** - remove all items from the list

```python
numbers = [1, 2, 3, 4, 5]
numbers.clear()

print(numbers) # []
```

### Check if an Element Exists in a List

```python
programming_languages = ['Python', 'Java', 'C++', 'Rust']

'Rust' in programming_languages # True
'JavaScript' in programming_languages # False
```

### Unpacking Values from a List

```python
developer = ['Alice', 34, 'Rust Developer']
name, age, job = developer
```

```python
# Collecting Remaining Items From a List

developer = ['Alice', 34, 'Rust Developer']
name, *rest = developer
```

```python
def add(a, b, c):
    return a + b + c


numbers = [1, 2, 3]

add(*numbers)  # 6
```

```python
a = [1, 2]
b = [3, 4]

combined = [*a, *b]
# [1, 2, 3, 4]
```

### Other

#### sort()

**sort()** - sort the elements in place

```python
numbers = [19, 2, 35, 1, 67, 41]
numbers.sort()

print(numbers) # [1, 2, 19, 35, 41, 67]
```

#### reverse()

**reverse()** - reverse the order of the elements in a list

```python
numbers = [6, 5, 4, 3, 2, 1]
numbers.reverse()

print(numbers) # [1, 2, 3, 4, 5, 6]
```

#### index()

**index()** - find the first index where an element can be found in a list

> [!important]
> If the element cannot be found using the index() method, then the result will be a `ValueError`

```python
programming_languages = ['Rust', 'Java', 'Python', 'C++']
programming_languages.index('Java') # 1
```

#### count()

**count()** - determine how many times an item appears

```python
programming_languages = ['Rust', 'Java', 'Python', 'C++', 'Rust']
programming_languages.count('Rust') # 2
```

## Dictionary

### get()

**get()** - retrieves the value associated with a key

> [!important]
> it lets you set a default value, preventing errors if the key doesn't exist.

```python
person: dict = {"name": "Tamas", "age": 25, "hobby": "drumming"}

print(person.get("name", "Unknown"))  # Tamas
print(person.get("namee", "Unknown"))  # Unknown
```

### keys(), values()

**keys() and values()** - return a view object with all the keys and values in the dictionary, respectively

> [!important]
> a **view object** is an object that gives you a dynamic view of the data in a dictionary, rather than a separate copy of that data

```python
person: dict = {"name": "Tamas", "age": 25, "hobby": "drumming"}

view = person.keys()

print(view)  # dict_keys(['name', 'age', 'hobby'])

person["city"] = "Vejle"

print(view)  # dict_keys(['name', 'age', 'hobby', 'city'])

print(person.values())
# dict_values(['Tamas', 25, 'drumming', 'Vejle'])
```

### items()

**items()** - returns a view object with all the key-value pairs

```python
person: dict = {"name": "Tamas", "age": 25, "hobby": "drumming"}

print(person.items())
# dict_items([('name', 'Tamas'), ('age', 25), ('hobby', 'drumming')])
```

### pop()

**pop()** - removes the key-value pair with the key specified as the first argument and returns its value

> [!important]
> If the key doesn't exist, it returns the default value specified as the second argument.

```python
person: dict = {"name": "Tamas", "age": 25, "hobby": "drumming"}

hobby_removed = person.pop("hobby", "This person didn't have a hobby")
# drumming

agee = person.pop("agee", "agee key not found")
# agee key not found

person.pop("something")  # KeyError
```

### update()

**update()** - updates the key-value pairs with the key-value pairs of another dictionary

> [!important]
> If they have keys in common, their values are overwritten.
>
> New keys will be added to the dictionary as new key-value pairs.

```python
person: dict = {"name": "Tamas", "age": 25, "hobby": "drumming"}

person.update({"age": 18, "city": "Vejle"})

print(person.items())
# dict_items([('name', 'Tamas'), ('age', 18), ('hobby', 'drumming'), ('city', 'Vejle')])
```

### setdefault()

**setdefault(key, default)** - get the value for a key, if the key doesn't exist, insert it with the given default value

```python
person = {"name": "Tamas", "age": 25}

person_hobby = person.setdefault("hobby", "drumming")
person_name = person.setdefault("name", "Anna")

print(person_hobby)  # drumming
print(person_name)  # Tamas
print(person)  # {'name': 'Tamas', 'age': 25, 'hobby': 'drumming'}
```

```python
person = {"name": "Tamas", "age": 25}

person_hobby = person.setdefault("hobby")

print(person_hobby)  # None
print(person)  # {'name': 'Tamas', 'age': 25, 'hobby': None}
```

### Looping Over a Dictionary

```python
person: dict = {"name": "Tamas", "age": 25, "hobby": "drumming"}

for key in person:
    print(key)

# name
# age
# hobby
```

```python
person: dict = {"name": "Tamas", "age": 25, "hobby": "drumming"}

for key in person.keys():
    print(key)
# name
# age
# hobby

for value in person.values():
    print(value)
# Tamas
# 25
# drumming
```

```python
person: dict = {"name": "Tamas", "age": 25, "hobby": "drumming"}

for info in person.items():
    print(info)
# ('name', 'Tamas')
# ('age', 25)
# ('hobby', 'drumming')

for key, value in person.items():
    print(f"{key}: {value}")
# name: Tamas
# age: 25
# hobby: drumming
```

### Unpacking a Dictionary

#### Unpack values from a dictionary

```python
person = {"name": "Alice", "age": 25, "city": "Odense"}

name, age, city = person.values()

print(name)  # Alice
print(age)  # 25
print(city)  # Odense
```

#### Unpacking a dictionary with `**`

```python
def greet(name, age):
    print(f"{name} is {age} years old")


person = {"name": "Alice", "age": 25}

greet(**person)
# Alice is 25 years old

# This is equivalent to:
# greet(name="Alice", age=25)
```

```python
a = {"x": 1, "y": 2}
b = {"z": 3}

merged = {**a, **b}
# {'x': 1, 'y': 2, 'z': 3}
```

#### Unpacking a custom object

```python
class Person:
    def __init__(self, name, age):
        self.name = name
        self.age = age


p = Person("Alice", 25)

print(vars(p))
# {'name': 'Alice', 'age': 25}


def greet(name, age):
    print(name, age)


greet(**vars(p))
# Alice 25
```

## Sets

### Methods

#### add()

**add()** - add an element to a set, passing the new element as an argument

#### remove(), discard()

**remove() and discard()** - remove an element from a set, passing the element you want to remove as an argument

> [!important]
> The `remove()` method will raise a `KeyError` if the element is not found while the `discard()` method will not.

#### clear()

**clear()** - remove all the elements from the set

### Mathematical Set Operations

#### Subset, Superset

**issubset() and issuperset()** - check if a set is a subset or superset of another set, respectively

```python
my_set = {1, 2, 3, 4, 5}
your_set = {2, 3, 4, 5}

print(your_set.issubset(my_set)) # True
print(my_set.issuperset(your_set)) # True
```

#### Disjoint

**isdisjoint()** - checks if two sets are disjoint (they don't have elements in common)

```python
my_set = {1, 2, 3}
your_set = {4, 5, 6}

print(my_set.isdisjoint(your_set)) # True
```

#### Union

**Union Operator `|`** - returns a new set with all the elements from both sets

```python
my_set = {1, 2, 3}
your_set = {4, 5, 6}

my_set | your_set # {1, 2, 3, 4, 5, 6}
```

#### Intersection

**Intersection Operator `&`** - returns a new set with only the elements that the sets have in common

```python
my_set = {1, 2, 3, 4, 5}
your_set = {2, 3, 4, 6}

my_set & your_set # {2, 3, 4}
```

#### Difference

**Difference Operator `-`** - returns a new set with the elements of the first set that are not in the other set

```python
my_set = {1, 2, 3, 4, 5}
your_set = {2, 3, 4, 6}

my_set - your_set # {1, 5}
```

#### Symmetric Difference

**Symmetric Difference Operator `^`** - returns a new set with the elements that are either in the first or the second set, but not both.

```python
my_set = {1, 2, 3, 4, 5}
your_set = {2, 3, 4, 6}

my_set ^ your_set # {1, 5, 6}
```

#### Existance

**`in` operator** - check if an element is in a set or not with the `in` operator

```python
my_set = {1, 2, 3, 4, 5}
print(5 in my_set) # True
```

### Immutable Sets - frozenset

`frozenset` is an immutable version of a set.

It contains unique, hashable elements that cannot be changed.

| Property                |    set    |   frozenset   |
| :---------------------- | :-------: | :-----------: |
| Mutable                 |    Yes    |      No       |
| add(), remove(), etc... | Supported | Not supported |
| Set operations          | Supported |   Supported   |
| Use as dict key         |    No     |      Yes      |

```python
permissions = frozenset(["read", "write", "read"])

print(permissions)  # frozenset({'write', 'read'})

groups = {frozenset(["Tamas", "Anna"]): "Team A", frozenset(["Muci", "Ocsi"]): "Team B"}

group_1_name = groups[frozenset(["Tamas", "Anna"])]
group_2_name = groups[frozenset(["Muci", "Ocsi"])]

print(group_1_name)  # Team A
print(group_2_name)  # Team B
```

## Comprehensions

### List Comprehension

```
[ expression for element in iterable if condition ]
```

```python
fruits_lower = ["orange", "strawberry", "banana", "ananas"]

fruits_upper = [fruit.upper() for fruit in fruits_lower if fruit.count("a") >= 3]

print(fruits_upper) # ['BANANA', 'ANANAS']
```

```python
numbers = [1, 2, 3, 4]

labels = ["Even" if x % 2 == 0 else "Odd" for x in numbers]

print(labels)  # ['Odd', 'Even', 'Odd', 'Even']
```

### Set Comprehension

```
{ expression for element in iterable if condition }
```

### Dictionary Comprehension

```
{ key_expression : value_expression for element in iterable if condition }
```

```python
food = {
    "carrot": "vegetable",
    "orange": "fruit",
    "strawberry": "fruit",
    "cabbage": "vegetable",
}

food_vegetable = {key: value for key, value in food.items() if value == "vegetable"}

print(food_vegetable)  # {'carrot': 'vegetable', 'cabbage': 'vegetable'}
```

## Built-ins

**[Official Docs](https://docs.python.org/3.14/builtins/functions.html)**

### sorted()

**sorted()** - return a new sorted list from the items in iterable

sorted(iterable, key=None, reverse=False)

- `key` - a function used to extract a comparison key from each element

```python
programming_languages = ('Rust', 'Java', 'Python', 'C++', 'Rust', 'Python')
sorted(programming_languages, key=len)

# Result
# ['C++', 'Rust', 'Java', 'Rust', 'Python', 'Python']
```

```python
students = [("Tamas", 80), ("Muci", 40), ("Anna", 60)]

ranked = sorted(students, key=lambda student: student[1])

print(ranked)  # [('Muci', 40), ('Anna', 60), ('Tamas', 80)]
```

### range()

**range()** - range(start, stop, step=1)

### enumerate()

**enumerate()**

```python
members = ["Tamas", "Obi-Wan", "Anakin", "Muci"]

for index, member in enumerate(members, start=1):
    print(index, member)

# 1 Tamas
# 2 Obi-Wan
# 3 Anakin
# 4 Muci
```

### all() / any()

**all() / any()** - return `True` if all/any elements of the iterable are true

```python
group = [
    {"name": "John", "age": 18},
    {"name": "Thomas", "age": 20},
    {"name": "Obi-Wan", "age": 17},
    {"name": "Jackson", "age": 19},
]

all(person["age"] >= 18 for person in group)  # False
any(person["age"] < 18 for person in group)  # True
```

### filter()

**filter()** - filter(function, iterable)

Construct an iterator from those elements of iterable for which function is true.

```python
members = ["Tamas", "Obi-Wan", "Anakin", "Muci", "Otto", "Thomas"]

names_o = filter(lambda p: p.startswith("O"), members)

for name in names_o:
    print(name)

# A generator expression might be better here tho
for p in filter(lambda p: p.startswith("T"), members):
    print(p)

# Obi-Wan
# Otto
# Tamas
# Thomas
```

### map()

**map()** - return an iterator that applies function to every item of iterable, yielding the results

```python
numbers = [1, 2, 3, 4]

doubled = list(map(lambda x: x * 2, numbers))

print(doubled)  # [2, 4, 6, 8]
```

```python
numbers = [1, 2, 3, 4]
numbers_2 = [4, 3, 2, 1]

sum = list(map(lambda x, y: x + y, numbers, numbers_2))

print(sum)  # [5, 5, 5, 5]
```

### isinstance()

**isinstance()**

```python
name = "Tamas"

isinstance(name, int)  # False
isinstance(name, (int, str))  # True
```

### ord()

**ord() -> int** - return the ordinal value of a character

"ordinal value" - the numerical value assigned to a character in Unicode

```python
print(ord("A"))  # 65
print(ord("a"))  # 97
print(ord("T"))  # 84

name = "Tamas"

print(ord(name[0]) == 84)  # True
```

### chr()

**chr()** - return the string representing a character with the specified Unicode code point

```python
print(chr(65))  # A
print(chr(97))  # a
print(chr(84))  # T

name = "Tamas"

print(name[0] == chr(84))  # True
```

### dir()

**dir(object)** - attempt to return a list of valid attributes for that object.

```python
dir(str)  # ['capitalize', 'casefold', 'center', 'count', ...]

print("startswith" in dir(str))  # True
```

### hash()

**hash()** - Return the hash value of the object (if it has one).

Hash values are **integers**.

```python
fruit_1 = "orange"
fruit_2 = "strawberry"

print(hash(fruit_1))  # -5579361166400437433
print(hash(fruit_2))  # -615438833989547485
```

```python
# Hash collision
a = int("-1")
b = int("-2")

print(hash(a), hash(b))
# -2 -2
```

### id()

**id()** - Return the “identity” of an object

This is an integer which is guaranteed to be unique and constant for this object during its lifetime. Two objects with non-overlapping lifetimes may have the same `id()` value.

**CPython implementation detail**: This is the address of the object in memory.

```python
a = int("-1")
b = int("-2")

print(id(a)) # 4389577432 for example
print(id(b)) # 4389577400 for example
```

## Typing

### Basic Types

| Type    | Description           | Example         |
| ------- | --------------------- | --------------- |
| `str`   | String / text         | `"hello"`       |
| `int`   | Integer               | `42`            |
| `float` | Floating-point number | `3.14`          |
| `bool`  | Boolean               | `True`, `False` |
| `None`  | Absence of a value    | `None`          |

```python
name: str = "Alice"
age: int = 25
price: float = 19.99
active: bool = True
result: None = None
```

### Collection Types

| Type            | Description                                   | Example           |
| --------------- | --------------------------------------------- | ----------------- |
| `list[T]`       | List of T                                     | `list[int]`       |
| `dict[K, V]`    | Dictionary with key type K and value type V   | `dict[str, int]`  |
| `set[T]`        | Set of unique values                          | `set[str]`        |
| `tuple[T, ...]` | Tuple containing any number of T values       | `tuple[int, ...]` |
| `tuple[T1, T2]` | Fixed tuple with specific types and positions | `tuple[str, int]` |

```python
names: list[str] = ["Alice", "Bob"]
ages: dict[str, int] = {"Alice": 25, "Bob": 30}
ids: set[int] = {1, 2, 3}
scores: tuple[int, ...] = (10, 20, 30)
user: tuple[str, int] = ("Alice", 25)
```

### Nested Collections

| Type                        | Description                                             |
| --------------------------- | ------------------------------------------------------- |
| `list[list[int]]`           | List of lists of integers                               |
| `list[dict[str, str]]`      | List of dictionaries                                    |
| `dict[str, list[int]]`      | Dictionary mapping strings to lists of integers         |
| `dict[str, dict[str, int]]` | Nested dictionary                                       |
| `list[tuple[float, float]]` | List of coordinate pairs                                |
| `dict[int, str \| None]`    | Dictionary with integer keys and optional string values |

```python
matrix: list[list[int]] = [[1, 2], [3, 4]]

users: list[dict[str, str]] = [
    {"name": "Alice", "role": "admin"},
]

scores: dict[str, list[int]] = {
    "Alice": [10, 12, 11],
}

coordinates: list[tuple[float, float]] = [
    (10.5, 20.3),
    (15.2, 30.1),
]
```

### Union and Optional Types

| Type                | Description               |
| ------------------- | ------------------------- |
| `int \| str`        | Integer or string         |
| `int \| float`      | Integer or float          |
| `str \| None`       | String or `None`          |
| `list[str] \| None` | List of strings or `None` |

```python
user_id: int | str = 123
nickname: str | None = None
number: int | float = 3.14
names: list[str] | None = None
```

### Function Annotations

| Syntax          | Description                                             |
| --------------- | ------------------------------------------------------- |
| `name: str`     | Parameter type                                          |
| `-> int`        | Return type                                             |
| `-> None`       | No meaningful return value                              |
| `*args: int`    | Variable number of positional integer arguments         |
| `**kwargs: str` | Variable number of keyword arguments with string values |

```python
def add(a: int, b: int) -> int:
    return a + b

def greet(name: str) -> None:
    print(f"Hello, {name}")

def total(*numbers: int) -> int:
    return sum(numbers)

def configure(**options: str) -> None:
    print(options)

def get_name(user_id: int) -> str | None:
    if user_id == 1:
        return "Alice"
    return None
```

### Useful Types from `typing`

| Type          | Description                                          | Example                      |
| ------------- | ---------------------------------------------------- | ---------------------------- |
| `Literal`     | Restricts values to specific literals                | `Literal["on", "off"]`       |
| `TypeAlias`   | Explicitly declares a type alias                     | `UserId: TypeAlias = int`    |
| `TypedDict`   | Defines a dictionary's expected keys and value types | `class User(TypedDict)`      |
| `NotRequired` | Marks a `TypedDict` key as optional                  | `nickname: NotRequired[str]` |
| `Callable`    | Describes a callable's signature                     | `Callable[[int], str]`       |
| `cast`        | Tells the type checker to treat a value as a type    | `cast(str, value)`           |

```python
from typing import Literal, TypeAlias, TypedDict, NotRequired, Callable

# Literal Type
status: Literal["on", "off"] = "off"

# TypeAlias
Theme: TypeAlias = Literal["light", "dark"]

theme: Theme = "dark"


# TypedDict
class User(TypedDict):
    name: str
    nickname: NotRequired[str]
    preferred_theme: Theme


user_1: User = {"name": "Tamas", "preferred_theme": "dark"}


# Callable
def transform_command(command_name: str, command: Callable[[str], str]) -> None:
    print(f"Executing command: {command_name}")

    command_result = command(command_name)
    print(command_result)


def titlecase_every_char(word: str) -> str:
    return word.title()


transform_command("title-case-word", titlecase_every_char)  # Title-Case-Word
```

### Type Aliases and Generics

```python
# Python 3.12+
type UserId = int | str
type Coordinates = tuple[float, float]

def first[T](items: list[T]) -> T:  # Python 3.12+
    return items[0]

class Box[T]:  # Python 3.12+
    def __init__(self, value: T) -> None:
        self.value = value
```

For Python 3.11 and earlier, use `TypeVar` and `Generic` for generic functions and classes.

## Bitwise Operations & Binary Data

### Conversions

```python
number_dec = 8
number_bin = 0b1000
number_hex = 0x0008

print(bin(number_dec))  # 0b1000
print(hex(number_dec))  # 0x8
print(int(number_bin))  # 8
print(int(number_hex))  # 8
```

```python
# Second arg is the base
print(int("1000", 2))  # 8
print(int("000f", 16))  # 15
```

### Formatting binary numbers

The `08b` means:

- `b`: binary representation.
- `8`: minimum width of 8 characters.
- Leading zeros are added if necessary.

```python
number = 10

print(format(number, "b"))  # 1010
print(format(number, "08b"))  # 00001010
print(format(number, "016b"))  # 0000000000001010

print(format(157, "x"))  # 9d
print(format(157, "02X"))  # 9D
```

### Bitwise operators

| Operator | Name          |                    Purpose |
| -------- | ------------- | -------------------------: |
| `&`      | `AND`         |        Both bits must be 1 |
| `\|`     | `OR`          | At least one bit must be 1 |
| `^`      | `XOR`         |     Bits must be different |
| `~`      | `NOT`         |               Inverts bits |
| `>>`      | `Right shift` |           Moves bits right |
| `<<`      | `Left shift` |           Moves bits left |

#### Bitwise `AND`, `OR`, `XOR`

```python
bitwise_and = 0b0011 & 0b1101  # 0001
bitwise_or = 0b1010 | 0b0101  # 1111
bitwise_xor = 0b1011 ^ 0b0101  # 1110
```

#### Bitwise `NOT`

> [!IMPORTANT]
> Python's `~` inverts bits, but the result is interpreted as a **signed integer**, not an automatically fixed-width binary value.

The mathematical relationship is:

$\sim x = -x-1$

```python
x = 12

print(~x)  # -13
```

#### Inverting bits

```python
x = 0b1101
y = 0b10101010

invert_x = (~x) & 0xF
invert_y = (~y) & 0xFF

invert_x_xor = x ^ 0xF

print(format(invert_x, "04b"))
# 0010
print(format(invert_y, "08b"))
# 01010101
print(format(invert_x_xor, "04b"))
# 0010
```

#### Bitwise `SHIFT`

```python
x = 0b1000

print(format(x >> 1, "04b"))  # 0100
print(format(x >> 3, "04b"))  # 0001
print(format(x << 1, "04b"))  # 10000
```

#### The four fundamental bit operations

| Goal | Operation | Formula |
|---|---|---|
| Check bit | AND | `value & mask` |
| Set bit | OR | `value \| mask` |
| Clear bit | AND + NOT | `value & ~mask` |
| Toggle bit | XOR | `value ^ mask` |


#### Checking whether a bit is set

Suppose you want to check whether bit position 2 is `1`.

Remember that bit positions start at zero, from the right.

```python
Position:  7 6 5 4 3 2 1 0
Value:     1 0 1 1 0 1 1 0
```

Create a mask that has only bit 2 enabled then `AND` the value and the mask.

```python
value = 0b10110110
mask = 1 << 2  # 0100

result = value & mask

print(result)  # 4
print(result != 0)  # True
```

#### Setting a bit

```python
# Set bit 2 to "1"
value = 0b1011
mask = 1 << 2  # 0100
result_1 = value | mask
print(format(result_1, "04b"))  # 1111
```

#### Clearing a bit

```python
value = 0b11111111

mask = 1 << 2

value = value & ~mask

print(format(value, "08b"))
# 11111011
```

#### Toggling a bit

```python
value = 0b10110110

mask = 1 << 2

value = value ^ mask
print(format(value, "08b"))  # 10110010
value ^= mask
print(format(value, "08b"))  # 10110110
```

### Subnetting example

```
IP address: 192.168.1.10
Subnet:     255.255.255.0 (/24)
```

Convert to binary

```
IP:
11000000.10101000.00000001.00001010

Mask:
11111111.11111111.11111111.00000000
```

Bitwise `AND`

```
IP:       11000000.10101000.00000001.00001010
Mask:     11111111.11111111.11111111.00000000
          -----------------------------------
Result:   11000000.10101000.00000001.00000000

192.168.1.0
```

```python
from ipaddress import ip_address


def ipv4_to_bin(ip_string: str) -> int:
    octets = ip_string.split(".")
    binary = "".join(format(int(octet), "08b") for octet in octets)
    return int(binary, 2)


ip_addr = "192.168.1.10"
subnet = "255.255.255.0"

ip_bin: int = ipv4_to_bin(ip_addr)
subnet_bin: int = ipv4_to_bin(subnet)

network = ip_bin & subnet_bin
print(ip_address(network))  # 192.168.1.0
```

## Python Imports & Packages

### Directory overview

```text
my_project/
├── main.py
└── my_package/
    ├── __init__.py
    ├── math_utils.py
    ├── strings.py
    └── report.py
```

| File            | Purpose                                    |
| --------------- | ------------------------------------------ |
| `main.py`       | Main entry point; runs the application     |
| `__init__.py`   | Defines convenient package-level imports   |
| `math_utils.py` | Contains math functions                    |
| `strings.py`    | Contains string utilities                  |
| `report.py`     | Uses other modules and can run as a module |

**Key idea:** A module is a `.py` file. A package is a directory containing related modules.

### Imports in a file

**`math_utils.py`**

```python
def add(a, b):
    return a + b
```

**`main.py`**

```python
import my_package.math_utils

print(my_package.math_utils.add(2, 3))
```

Or import just the function:

```python
from my_package.math_utils import add

print(add(2, 3))
```

### Imports in `__init__.py`

**`my_package/__init__.py`**

```python
from .math_utils import add
from .strings import greet
```

The `.` means the current package.

Now `main.py` can import directly from the package:

```python
from my_package import add, greet

print(add(2, 3))
print(greet("Alex"))
```

### Running separate modules in a package

**`my_package/report.py`**

```python
from .math_utils import add

def run():
    print(add(10, 20))

if __name__ == "__main__":
    run()
```

From the `my_project/` directory, run:

```bash
python -m my_package.report
```

**Why use `-m`?** It runs the file as a module within its package, allowing relative imports like `from .math_utils import add`.

Running `python my_package/report.py` directly won't work with that relative import.

### Absolute vs. Relative Imports

#### Directory structure

```text
my_project/
├── main.py
└── my_package/
    ├── __init__.py
    ├── math_utils.py
    └── reports/
        ├── __init__.py
        └── report.py
```

#### Absolute Imports

An absolute import uses the full path from the import root (usually `my_project/`).

```python
from my_package.math_utils import add
```

This import works from `main.py` or `report.py`, provided `my_project/` is on Python's import path.

```python
# main.py
from my_package.math_utils import add

print(add(2, 3))
```

#### Relative Imports

A relative import uses dots to locate a module relative to the current package.

Inside `my_package/reports/report.py`:

```python
from ..math_utils import add
```

**How to read it:**

- `.` → current package (`my_package.reports`)
- `..` → parent package (`my_package`)
- `math_utils` → module inside `my_package`

So `..math_utils` refers to `my_package.math_utils`.

#### Running a Module

Relative imports require Python to know the module's package context.

From the `my_project/` directory, run:

```bash
python -m my_package.reports.report
```

This tells Python to run `report` as a module within `my_package.reports`.

Running the file directly:

```bash
python my_package/reports/report.py
```

can fail with a relative-import error because Python treats it as a standalone script.
