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
  - [`bytes`](#bytes)
  - [`bytearray`](#bytearray)
  - [Creating empty or zero-filled bytes](#creating-empty-or-zero-filled-bytes)
  - [`bytes.fromhex()`](#bytesfromhex)
  - [Converting integers to bytes](#converting-integers-to-bytes)
    - [`int.to_bytes(length, byteorder, signed)`](#intto_byteslength-byteorder-signed)
  - [Convert from `bytes` to `int`](#convert-from-bytes-to-int)
  - [Overflow Error](#overflow-error)
  - [Signed integers](#signed-integers)
  - [Encoding and decoding](#encoding-and-decoding)
    - [ASCII](#ascii)
    - [UTF-8](#utf-8)
  - [Reading and writing hexadecimal bytes](#reading-and-writing-hexadecimal-bytes)
    - [Convert bytes to hexadecimal](#convert-bytes-to-hexadecimal)
    - [Convert hexadecimal into bytes](#convert-hexadecimal-into-bytes)
    - [Change individual bytes using hexadecimal](#change-individual-bytes-using-hexadecimal)
    - [Hexadecimal as a debugging tool](#hexadecimal-as-a-debugging-tool)
  - [Integer Methods](#integer-methods)
    - [`bit_length()`](#bit_length)
    - [`bit_count()`](#bit_count)
    - [`to_bytes()`](#to_bytes)
    - [`from_bytes()`](#from_bytes)
    - [`int.as_integer_ratio()`](#intas_integer_ratio)
  - [`struct` module](#struct-module)
    - [Pack](#pack)
    - [Unpack](#unpack)
    - [(Un)packing multiple values](#unpacking-multiple-values)
    - [Why `struct` is useful](#why-struct-is-useful)
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
- [OOP](#oop)
  - [Python Classes and Objects](#python-classes-and-objects)
    - [Attributes](#attributes)
    - [Methods](#methods-1)
    - [Dunder (Magic) Methods](#dunder-magic-methods)
    - [Objects Working Together](#objects-working-together)
  - [Object-Oriented Programming](#object-oriented-programming)
    - [Encapsulation](#encapsulation)
    - [Getters and Setters](#getters-and-setters)
    - [Inheritance](#inheritance)
    - [Polymorphism](#polymorphism)
    - [Name Mangling](#name-mangling)
    - [Abstraction](#abstraction)
- [Working with Dates and Times](#working-with-dates-and-times)

# Todo

- [ ] vars() builtins
- [ ] zip() builtins
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

# String

## str.strip()

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

## str.replace()

**replace()** - returns a new string with all occurrences of the old string replaced by a new one

```python
greeting = "hello, hello everyone"

replaced_my_str = greeting.replace("hello", "hi")
print(replaced_my_str)  # hi, hi everyone
```

## str.split()

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

## str.join()

**join()** - join a collection of strings into one string with a separator

```python
example_list = ["example", "dashed", "name"]

joined_space = " ".join(example_list)  # example dashed name
joined_no_sep = "".join(example_list)  # exampledashedname
```

## str.startswith() & str.endsswith()

**str.startswith(prefix) and str.endswith(suffix)** - returns a boolean indicating if a string starts/ends with the specified suffix, respectively

```python
name = "Tamas"

name.startswith("t")  # False
name.startswith("T")  # True
name.startswith("To")  # False

name.endswith("as")  # True
name.endswith("i")  # False
```

## str.find()

**find()** - returns the index of the first occurrence of a substring

If one is not found, then -1 is returned

```python
developer = 'Naomi'

result = developer.find('N')
print(result)  # 0

city = 'Los Angeles'
print(city.find('New')) # -1
```

## str.count()

**str.count(substring)** - counts how many times a substring appears in a string

```python
city = 'Los Angeles'
print(city.count('e')) # 2
```

## upper(), lower(), capitalize(), title()

**upper(), lower(), capitalize(), title()** - case characters in different ways

```python
greeting = "hello World !"

greeting.upper()  # HELLO WORLD !
greeting.lower()  # hello world !
greeting.capitalize()  # Hello world !
greeting.title()  # Hello World !
```

## isupper(), islower()

**isupper(), islower()** - returns `True` if the string contains at least one cased character and all cased characters are upper/lowercase, respectively

```python
dessert = 'chocolate cake'
print(dessert.isupper()) # False
```

```python
dessert = 'chocolate cake'
print(dessert.islower()) # True
```

## str.maketrans()

**str.maketrans()** - `str.maketrans()` creates a table of one-to-one character mappings

It is often used with `translate()`, which applies the table to a string and returns the translated result.

```python
trans_table = str.maketrans("tomi", "1234")
print(trans_table)  # {116: 49, 111: 50, 109: 51, 105: 52}

result_1 = "tomi".translate(trans_table)  # 1234
result_2 = "imot".translate(trans_table)  # 4321
result_3 = "tomika".translate(trans_table)  # 1234ka
```

# List

## Adding items

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

## Removing items

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

## Check if an Element Exists in a List

```python
programming_languages = ['Python', 'Java', 'C++', 'Rust']

'Rust' in programming_languages # True
'JavaScript' in programming_languages # False
```

## Unpacking Values from a List

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

## Other

### sort()

**sort()** - sort the elements in place

```python
numbers = [19, 2, 35, 1, 67, 41]
numbers.sort()

print(numbers) # [1, 2, 19, 35, 41, 67]
```

### reverse()

**reverse()** - reverse the order of the elements in a list

```python
numbers = [6, 5, 4, 3, 2, 1]
numbers.reverse()

print(numbers) # [1, 2, 3, 4, 5, 6]
```

### index()

**index()** - find the first index where an element can be found in a list

> [!important]
> If the element cannot be found using the index() method, then the result will be a `ValueError`

```python
programming_languages = ['Rust', 'Java', 'Python', 'C++']
programming_languages.index('Java') # 1
```

### count()

**count()** - determine how many times an item appears

```python
programming_languages = ['Rust', 'Java', 'Python', 'C++', 'Rust']
programming_languages.count('Rust') # 2
```

# Dictionary

## get()

**get()** - retrieves the value associated with a key

> [!important]
> it lets you set a default value, preventing errors if the key doesn't exist.

```python
person: dict = {"name": "Tamas", "age": 25, "hobby": "drumming"}

print(person.get("name", "Unknown"))  # Tamas
print(person.get("namee", "Unknown"))  # Unknown
```

## keys(), values()

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

## items()

**items()** - returns a view object with all the key-value pairs

```python
person: dict = {"name": "Tamas", "age": 25, "hobby": "drumming"}

print(person.items())
# dict_items([('name', 'Tamas'), ('age', 25), ('hobby', 'drumming')])
```

## pop()

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

## update()

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

## setdefault()

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

## Looping Over a Dictionary

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

## Unpacking a Dictionary

### Unpack values from a dictionary

```python
person = {"name": "Alice", "age": 25, "city": "Odense"}

name, age, city = person.values()

print(name)  # Alice
print(age)  # 25
print(city)  # Odense
```

### Unpacking a dictionary with `**`

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

### Unpacking a custom object

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

# Sets

## Methods

### add()

**add()** - add an element to a set, passing the new element as an argument

### remove(), discard()

**remove() and discard()** - remove an element from a set, passing the element you want to remove as an argument

> [!important]
> The `remove()` method will raise a `KeyError` if the element is not found while the `discard()` method will not.

### clear()

**clear()** - remove all the elements from the set

## Mathematical Set Operations

### Subset, Superset

**issubset() and issuperset()** - check if a set is a subset or superset of another set, respectively

```python
my_set = {1, 2, 3, 4, 5}
your_set = {2, 3, 4, 5}

print(your_set.issubset(my_set)) # True
print(my_set.issuperset(your_set)) # True
```

### Disjoint

**isdisjoint()** - checks if two sets are disjoint (they don't have elements in common)

```python
my_set = {1, 2, 3}
your_set = {4, 5, 6}

print(my_set.isdisjoint(your_set)) # True
```

### Union

**Union Operator `|`** - returns a new set with all the elements from both sets

```python
my_set = {1, 2, 3}
your_set = {4, 5, 6}

my_set | your_set # {1, 2, 3, 4, 5, 6}
```

### Intersection

**Intersection Operator `&`** - returns a new set with only the elements that the sets have in common

```python
my_set = {1, 2, 3, 4, 5}
your_set = {2, 3, 4, 6}

my_set & your_set # {2, 3, 4}
```

### Difference

**Difference Operator `-`** - returns a new set with the elements of the first set that are not in the other set

```python
my_set = {1, 2, 3, 4, 5}
your_set = {2, 3, 4, 6}

my_set - your_set # {1, 5}
```

### Symmetric Difference

**Symmetric Difference Operator `^`** - returns a new set with the elements that are either in the first or the second set, but not both.

```python
my_set = {1, 2, 3, 4, 5}
your_set = {2, 3, 4, 6}

my_set ^ your_set # {1, 5, 6}
```

### Existance

**`in` operator** - check if an element is in a set or not with the `in` operator

```python
my_set = {1, 2, 3, 4, 5}
print(5 in my_set) # True
```

## Immutable Sets - frozenset

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

# Comprehensions

## List Comprehension

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

## Set Comprehension

```
{ expression for element in iterable if condition }
```

## Dictionary Comprehension

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

# Built-ins

**[Official Docs](https://docs.python.org/3.14/builtins/functions.html)**

## sorted()

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

## range()

**range()** - range(start, stop, step=1)

## enumerate()

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

## all() / any()

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

## filter()

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

## map()

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

## isinstance()

**isinstance()**

```python
name = "Tamas"

isinstance(name, int)  # False
isinstance(name, (int, str))  # True
```

## ord()

**ord() -> int** - return the ordinal value of a character

"ordinal value" - the numerical value assigned to a character in Unicode

```python
print(ord("A"))  # 65
print(ord("a"))  # 97
print(ord("T"))  # 84

name = "Tamas"

print(ord(name[0]) == 84)  # True
```

## chr()

**chr()** - return the string representing a character with the specified Unicode code point

```python
print(chr(65))  # A
print(chr(97))  # a
print(chr(84))  # T

name = "Tamas"

print(name[0] == chr(84))  # True
```

## dir()

**dir(object)** - attempt to return a list of valid attributes for that object.

```python
dir(str)  # ['capitalize', 'casefold', 'center', 'count', ...]

print("startswith" in dir(str))  # True
```

## hash()

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

## id()

**id()** - Return the “identity” of an object

This is an integer which is guaranteed to be unique and constant for this object during its lifetime. Two objects with non-overlapping lifetimes may have the same `id()` value.

**CPython implementation detail**: This is the address of the object in memory.

```python
a = int("-1")
b = int("-2")

print(id(a)) # 4389577432 for example
print(id(b)) # 4389577400 for example
```

# Typing

## Basic Types

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

## Collection Types

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

## Nested Collections

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

## Union and Optional Types

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

## Function Annotations

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

## Useful Types from `typing`

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

## Type Aliases and Generics

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

# Bitwise Operations & Binary Data

## Conversions

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

## Formatting binary numbers

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

## Bitwise operators

| Operator | Name          |                    Purpose |
| -------- | ------------- | -------------------------: |
| `&`      | `AND`         |        Both bits must be 1 |
| `\|`     | `OR`          | At least one bit must be 1 |
| `^`      | `XOR`         |     Bits must be different |
| `~`      | `NOT`         |               Inverts bits |
| `>>`      | `Right shift` |           Moves bits right |
| `<<`      | `Left shift` |           Moves bits left |

### Bitwise `AND`, `OR`, `XOR`

```python
bitwise_and = 0b0011 & 0b1101  # 0001
bitwise_or = 0b1010 | 0b0101  # 1111
bitwise_xor = 0b1011 ^ 0b0101  # 1110
```

### Bitwise `NOT`

> [!IMPORTANT]
> Python's `~` inverts bits, but the result is interpreted as a **signed integer**, not an automatically fixed-width binary value.

The mathematical relationship is:

$\sim x = -x-1$

```python
x = 12

print(~x)  # -13
```

### Inverting bits

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

### Bitwise `SHIFT`

```python
x = 0b1000

print(format(x >> 1, "04b"))  # 0100
print(format(x >> 3, "04b"))  # 0001
print(format(x << 1, "04b"))  # 10000
```

### The four fundamental bit operations

| Goal | Operation | Formula |
|---|---|---|
| Check bit | AND | `value & mask` |
| Set bit | OR | `value \| mask` |
| Clear bit | AND + NOT | `value & ~mask` |
| Toggle bit | XOR | `value ^ mask` |


### Checking whether a bit is set

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

### Setting a bit

```python
# Set bit 2 to "1"
value = 0b1011
mask = 1 << 2  # 0100
result_1 = value | mask
print(format(result_1, "04b"))  # 1111
```

### Clearing a bit

```python
value = 0b11111111

mask = 1 << 2

value = value & ~mask

print(format(value, "08b"))
# 11111011
```

### Toggling a bit

```python
value = 0b10110110

mask = 1 << 2

value = value ^ mask
print(format(value, "08b"))  # 10110010
value ^= mask
print(format(value, "08b"))  # 10110110
```

## Subnetting example

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

## `bytes`

A built-in type that represents an immutable sequence of integers, where each integer must be between 0 and 255.

`bytes()` converts those integers into bytes.

```python
data = bytes([65, 66, 67])
# those values correspond to ASCII characters

print(data)  # b'ABC'

print(data[0])  # 65
print(data[1])  # 66
print(data[2])  # 67
```

## `bytearray`

Mutable sequence of bytes

```python
data = bytearray([65, 66, 67])

print(data)  # bytearray(b'ABC')

data[0] = 70

print(data)  # bytearray(b'FBC')
```

`bytearray(data)` creates a new, independent object. It is not a shallow copy or a reference to the original object.

```python
data = bytes([65, 66, 67])
# b'ABC'

editable = bytearray(data)
editable[0] = 70
print(editable)
# bytearray(b'FBC')

result = bytes(editable)
# b'FBC'
```

```python
for byte in bytearray(b"ABC"):
    print(byte)

# 65
# 66
# 67

for byte in bytes([65, 66, 67]):
    print(byte)

# 65
# 66
# 67
```

## Creating empty or zero-filled bytes

- `bytes()` creates an empty sequence.
- `bytes(4)` creates a sequence containing four zero bytes.

```python
a = bytes()
b = bytes(4)

print(a)  # b''
print(b)  # b'\x00\x00\x00\x00'
```

## `bytes.fromhex()`

- `data1[0]` uses indexing. It returns one integer representing the byte at index 0.
- `data2[0:2]` uses slicing. It returns a new bytes object containing bytes at indices 0 and 1.

```python
data1 = bytes.fromhex("41 42 43")
print(data1)  # b'ABC'

data2 = bytes.fromhex("414243")
print(data2)  # b'ABC'

print(data1[0])  # 65
print(data2[0:2])  # b'AB'
```

## Converting integers to bytes

Imagine you have this integer:

`number = 1000`

You know that its binary representation is:

`1111101000` or `0b1111101000`

What if you want to store that integer in a binary file or send it over a network?

You need to decide how many bytes to use and how to arrange them.

### `int.to_bytes(length, byteorder, signed)`

1. `length` - represent the integer using exactly `x` bytes
2. `byteorder` - store the most significant byte first

Big-endian byte order:

`03` - Most significant
`E8` - Least significant

```python
number = 1000

data = number.to_bytes(2, byteorder="big")

print(data)  # b'\x03\xe8'
print(data.hex())  # 03e8

print(bin(number) == bin(0x03E8))  # True
```

Little-endian byte order:

```python
number = 1000

data = number.to_bytes(2, byteorder="little")
data2 = number.to_bytes(2, byteorder="big")


print(data)  # b'\xe8\x03'
print(data.hex())  # e803

print(data2)  # b'\x03\xe8'
print(data2.hex())  # 03e8
```

## Convert from `bytes` to `int`

```python
data = bytes.fromhex("00 01")

number_big = int.from_bytes(data, byteorder="big")
number_little = int.from_bytes(data, byteorder="little")

print(number_big)  # 1
print(number_little)  # 256
```

## Overflow Error

1 byte is not enough to represent `1000`

```python
number = 1000

big = number.to_bytes(1, byteorder="big")
# OverflowError: int too big to convert

big = number.to_bytes(1, byteorder="little")
# OverflowError: int too big to convert
```

## Signed integers

Python integers **don't** have a fixed width.

Instead, Python behaves as if negative integers have infinitely many leading 1 bits when performing bitwise operations.

```python
neg_signed = (-100).to_bytes(2, "big", signed=True)
pos_signed = (+100).to_bytes(2, "big", signed=True)
pos_num = (100).to_bytes(2, "big", signed=True)

print(neg_signed)  # b'\xff\x9c'
print(pos_signed)  # b'\x00d'
print(pos_num)  # b'\x00d'

neg_num = int.from_bytes(neg_signed, "big", signed=True)
neg_num2 = int.from_bytes(neg_signed, "big", signed=False)

print(neg_num)  # -100
print(neg_num2)  # 65436

neg_num_s_false = (-100).to_bytes(2, "big", signed=False)
# OverflowError: can't convert negative int to unsigned
```

## Encoding and decoding

Computers often need to transmit or store text as bytes.

Character encoding:

- An encoding defines how characters are represented as bytes.

Python provides two particularly important methods:
- `.encode()` — string to bytes.
- `.decode()` — bytes to string.

### ASCII

```python
text = "ABC"

data = text.encode("ascii")

print(data)  # b'ABC'
print(data.hex())  # 414243
```

### UTF-8

```python
text = "Café"

data = text.encode("utf-8")

print(data)  # b'Caf\xc3\xa9'
print(data.hex())  # 436166c3a9

cafe_hex = bytes.fromhex("43 61 66 C3 A9")
cafe_text = cafe_hex.decode("utf-8")
print(cafe_text)  # Café
```

## Reading and writing hexadecimal bytes

### Convert bytes to hexadecimal

```python
data = bytes([72, 101, 108, 108, 111])

print(data.hex())  # 48656c6c6f

print(data.hex(" "))  # 48 65 6c 6c 6f
```

### Convert hexadecimal into bytes

```python
data = bytes.fromhex("48 65 6c 6c 6f")

print(data)  # b'Hello'
```

### Change individual bytes using hexadecimal

```python
data = bytearray.fromhex("48 65 6c 6c 6f")

data[0] = 0x4A

print(data.hex(" "))  # 4a 65 6c 6c 6f

print(data)  # bytearray(b'Jello')
```

### Hexadecimal as a debugging tool

You might eventually encounter something like this when inspecting a file or network packet:

```
0000   45 00 00 3C 1C 46 40 00
0008   40 06 B1 E6 C0 A8 01 01
0010   C0 A8 01 02
```

This is a **hexadecimal dump**.

Each pair represents one byte. The left column indicates the offset (position) in the data.

**Try it out**

1. Copy the below into a `txt` file.

```
Hello how are you?
I am ABC
abc
def
```

2. Run `xxd <name>.txt`

```
00000000: 4865 6c6c 6f20 686f 7720 6172 6520 796f  Hello how are yo
00000010: 753f 0a49 2061 6d20 4142 430a 6162 630a  u?.I am ABC.abc.
00000020: 6465 660a                                def.
```

## Integer Methods

### `bit_length()`

`bit_length()` tells you how many bits are needed to represent an integer in binary, excluding the sign and leading zeros.

```python
x = 10
y = -10

print(bin(x))  # 0b1010
print(x.bit_length())  # 4

print(bin(y))  # -0b1010
print(y.bit_length())  # 4
```

### `bit_count()`

`bit_count()` counts how many 1 bits appear in the binary representation of the integer's absolute value.

```python
x = 13

print(bin(x))  # 0b1101
print(x.bit_count())  # 3
```

### `to_bytes()`

This method converts an integer into a sequence of bytes.

```python
number = 1000

data = number.to_bytes(2, byteorder="big")

print(data)  # b'\x03\xe8'
print(data.hex())  # 03e8
```

### `from_bytes()`

It converts bytes back into an integer.

```python
data = bytes.fromhex("03 E8")
number = int.from_bytes(data, byteorder="big")
print(number)  # 1000

data = bytes.fromhex("FB")
number = int.from_bytes(data, "big", signed=True)
print(number)  # -5
```

### `int.as_integer_ratio()`

This method expresses an integer as a fraction consisting of a numerator and denominator.

The return value is a `tuple` containing two integers.

Every integer can be expressed as `x = x/1`

```python
print((10).as_integer_ratio())  # (10, 1)
print((-5).as_integer_ratio())  # (-5, 1)
print((0).as_integer_ratio())  # (0, 1)
```

```python
x = 0.5
y = 0.75
z = 9.5

print(x.as_integer_ratio())
# (1, 2)

print(y.as_integer_ratio())
# (3, 4)

print(z.as_integer_ratio())
# (19, 2)
```

## `struct` module

The struct module lets you convert Python values into binary data structures and back again.

| Symbol | Meaning |
|:---:|---|
| `>` | Big-endian |
| `<` | Little-endian |
| `H` | Unsigned 16-bit integer |
| `h` | Signed 16-bit integer |
| `I` | Unsigned 32-bit integer |
| `i` | Signed 32-bit integer |
| `B` | Unsigned 8-bit integer |
| `b` | Signed 8-bit integer |
| `f` | 32-bit float |
| `d` | 64-bit float |

### Pack

```python
import struct

data = struct.pack(">H", 1000)

print(data)  # b'\x03\xe8'
print(data.hex())  # 03e8
```

### Unpack

```python
import struct

data = bytes.fromhex("03 E8")

result = struct.unpack(">H", data)

print(result)  # (1000,)
```

### (Un)packing multiple values

```python
import struct

# 255 as an unsigned 8-bit integer.
# 1000 as an unsigned 16-bit integer.
data = struct.pack(">B H", 255, 1000)

print(struct.unpack(">BH", data))
# (255, 1000)
```

### Why `struct` is useful

Imagine creating a binary file format with this structure:

| Field | Type | Size |
|---|---|---:|
| File version | Unsigned 8-bit | 1 byte |
| File size | Unsigned 32-bit | 4 bytes |
| Temperature | 32-bit float | 4 bytes |

```python
import struct

# encode the entire header
header = struct.pack(">BIf", 1, 1024, 23.5)

# read it back
version, size, temperature = struct.unpack(">BIf", header)

print(version)  # 1
print(size)  # 1024
print(temperature)  # 23.5
```

# Python Imports & Packages

## Directory overview

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

## Imports in a file

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

## Imports in `__init__.py`

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

## Running separate modules in a package

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

## Absolute vs. Relative Imports

### Directory structure

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

### Absolute Imports

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

### Relative Imports

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

### Running a Module

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

# OOP

- [ ] type()
- [ ] isinstance()
- [ ]

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

# Working with Dates and Times

- **Getting the Current Date and Time**: Calling `datetime.datetime.now()` returns the current date and time as a `datetime` object.

- **Storing a Timestamp on an Instance**: Call `datetime.datetime.now()` inside `__init__()` and assign the result to an attribute to record when the object was created.

```python
import datetime

class Email:
    def __init__(self, body):
        self.body = body
        self.timestamp = datetime.datetime.now()
```

- **Formatting with strftime()**: The `strftime()` method turns a `datetime` object into a `string`, using format codes: `%Y` for the four-digit year, `%m` for the month, `%d` for the day, `%H` for the hour (24-hour clock), `%M` for the minutes, and `%S` for the seconds. Any other characters, such as -, /, :, or spaces, are kept as literal separators.

```python
email = Email('Hello!')

print(email.timestamp.strftime('%Y-%m-%d %H:%M:%S'))  # 2026-11-02 14:30:05
print(email.timestamp.strftime('%d/%m/%Y'))           # 02/11/2026
```
