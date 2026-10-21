- [Todo](#todo)
- [List](#list)
  - [Adding items](#adding-items)
  - [Removing items](#removing-items)
  - [Check if an Element Exists in a List](#check-if-an-element-exists-in-a-list)
  - [Unpacking Values from a List](#unpacking-values-from-a-list)
  - [Other](#other)
- [Dictionary](#dictionary)
  - [Looping Over a Dictionary](#looping-over-a-dictionary)
- [Sets](#sets)
- [Built-ins](#built-ins)
  - [Good to knows](#good-to-knows)
  - [Cool to knows](#cool-to-knows)
  - [Type Casting](#type-casting)

## Todo

- [ ] most useful string method - **TODAY 22**s
- [ ] python typing - **TODAY 22**
- [ ] imports in file - **TODAY 22**
- [ ] imports in __init__ - **TODAY 22**
- [ ] running seperate modules in a package - **TODAY 22**
- [ ] OOP
- [ ] dataclass
- [ ] sys
- path
- stdin/stdout
- platform
- [ ] subprocess
- [ ] os
- sys.path.append(os.path.dirname(__file__))
- special variable like __file__
- file openings

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

**insert(*index, item*)** - insert an item at a specific index in the list

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

**pop(*index*)** - remove a specific item from the list and return it

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

### Other

**sort()** - sort the elements in place

```python
numbers = [19, 2, 35, 1, 67, 41]
numbers.sort()

print(numbers) # [1, 2, 19, 35, 41, 67]
```

**reverse()** - reverse the order of the elements in a list

```python
numbers = [6, 5, 4, 3, 2, 1]
numbers.reverse()

print(numbers) # [1, 2, 3, 4, 5, 6]
```

**index()** - find the first index where an element can be found in a list

> [!important]
> If the element cannot be found using the index() method, then the result will be a `ValueError`

```python
programming_languages = ['Rust', 'Java', 'Python', 'C++']
programming_languages.index('Java') # 1
```

**count()** - determine how many times an item appears

```python
programming_languages = ['Rust', 'Java', 'Python', 'C++', 'Rust']
programming_languages.count('Rust') # 2
```

## Dictionary

**get()** - retrieves the value associated with a key

> [!important]
> it lets you set a default value, preventing errors if the key doesn't exist.

```python
person: dict = {"name": "Tamas", "age": 25, "hobby": "drumming"}

print(person.get("name", "Unknown"))  # Tamas
print(person.get("namee", "Unknown"))  # Unknown
```

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

**items()** - returns a view object with all the key-value pairs

```python
person: dict = {"name": "Tamas", "age": 25, "hobby": "drumming"}

print(person.items())
# dict_items([('name', 'Tamas'), ('age', 25), ('hobby', 'drumming')])
```

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

## Sets

## Built-ins

**[Official Docs](https://docs.python.org/3.14/builtins/functions.html)**

### Good to knows

**sorted()** - return a new sorted list from the items in iterable

sorted(iterable, key=None, reverse=False)


- `key` - a function used to extract a comparison key from each element

```python
programming_languages = ('Rust', 'Java', 'Python', 'C++', 'Rust', 'Python')
sorted(programming_languages, key=len)

# Result
# ['C++', 'Rust', 'Java', 'Rust', 'Python', 'Python']
```

**range()** - range(start, stop, step=1)

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

**isinstance()**

```python
name = "Tamas"

isinstance(name, int)  # False
isinstance(name, (int, str))  # True
```

### Cool to knows

**ord() -> int** - return the ordinal value of a character

"ordinal value" - the numerical value assigned to a character in Unicode

```python
print(ord("A"))  # 65
print(ord("a"))  # 97
print(ord("T"))  # 84

name = "Tamas"

print(ord(name[0]) == 84)  # True
```

**chr()** - return the string representing a character with the specified Unicode code point

```python
print(chr(65))  # A
print(chr(97))  # a
print(chr(84))  # T

name = "Tamas"

print(name[0] == chr(84))  # True
```

**dir(object)** - attempt to return a list of valid attributes for that object.

```python
dir(str)  # ['capitalize', 'casefold', 'center', 'count', ...]

print("startswith" in dir(str))  # True
```


### Type Casting

1. bool()
2. list()
3. tuple()
4. set()
5. str()
6. int()
7. float()
