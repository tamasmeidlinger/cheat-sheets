- [Todo](#todo)
- [Strings](#strings)
  - [trim()](#trim)
  - [replace() / replaceAll()](#replace--replaceall)
  - [split()](#split)
  - [join()](#join)
  - [startsWith() \& endsWith()](#startswith--endswith)
  - [indexOf()](#indexof)
  - [includes()](#includes)
  - [slice()](#slice)
  - [repeat()](#repeat)
  - [toUpperCase() \& toLowerCase()](#touppercase--tolowercase)
- [Arrays](#arrays)
  - [Adding elements](#adding-elements)
    - [push()](#push)
    - [Extending arrays using `push()`](#extending-arrays-using-push)
    - [unshift()](#unshift)
  - [Remove elements](#remove-elements)
    - [pop()](#pop)
    - [shift()](#shift)
  - [splice() - insert, replace, remove elements](#splice---insert-replace-remove-elements)
  - [Other](#other)
    - [indexOf()](#indexof-1)
    - [includes()](#includes-1)
    - [concat()](#concat)
    - [slice()](#slice-1)
  - [Spread Syntax](#spread-syntax)
  - [Shallow Copy](#shallow-copy)
  - [Array Destructuring](#array-destructuring)
- [Objects](#objects)
  - [Definition](#definition)
  - [Set a Property of an Existing Object](#set-a-property-of-an-existing-object)
  - [Removing Properties From an Object](#removing-properties-from-an-object)
    - [`delete` operator](#delete-operator)
  - [Checking if an Object has a Property](#checking-if-an-object-has-a-property)
    - [Object.hasOwn()](#objecthasown)
    - [hasOwnProperty()](#hasownproperty)
    - [`in` Operator](#in-operator)
  - [Accessing Properties From Nested Objects](#accessing-properties-from-nested-objects)
  - [Working with the Optional Chaining Operator `?.`](#working-with-the-optional-chaining-operator-)
  - [Object Methods](#object-methods)
  - [Object Destructuring](#object-destructuring)
  - [Working with JSON](#working-with-json)
    - [JSON.stringify()](#jsonstringify)
    - [JSON.parse()](#jsonparse)


## Todo

1. str.replace() and replaceAll() regular expression
2. counting character occurences - regular expression
 ```typescript
const city = "Los Angeles";

console.log(city.match(/e/g)?.length ?? 0); // 2
```
3. counting substring occurences

```typescript
const greeting = "hello, hello everyone";

const count = greeting.split("hello").length - 1;

console.log(count); // 2
```
4. Type casting
5. TypeScript Typing
6. imports/exports

- [ ] Terminology and Other [Source](https://www.freecodecamp.org/learn/javascript-v9/review-javascript-fundamentals/review-javascript-fundamentals)
7. Closures
8. Hoisting and var Keyword

- [ ] Higher Order Functions and Callback functions [Source](https://www.freecodecamp.org/learn/javascript-v9/review-javascript-higher-order-functions/review-javascript-higher-order-functions)

- [ ] Web APIs

## Strings

### trim()

**trim()** - returns a new string with leading and trailing whitespace removed

```typescript
const greeting: string = "  hello world  ";

const trimmed = greeting.trim();
console.log(trimmed); // "hello world"
```

### replace() / replaceAll()

**replace() and replaceAll()** - replaces the first/all occurrence(s) when given a string as its search argument, respectively

```typescript
const greeting: string = "hello, hello everyone";

greeting.replace("hello", "hi");
// "hi, hello everyone"

greeting.replaceAll("hello", "hi");
// "hi, hi everyone"
```

### split()

**split()** - divides a string into an array using a specified separator

```typescript
const dashedName: string = "example-dashed-name";
const whitespaceName: string = "example dashed name";

const splitDashed = dashedName.split("-");
const splitWhitespace = whitespaceName.split(" ");

console.log(splitDashed);
// ["example", "dashed", "name"]

console.log(splitWhitespace);
// ["example", "dashed", "name"]
```

```typescript
const name: string = "cookie";

const chars: string[] = name.split("");

console.log(chars);
// [ 'c', 'o', 'o', 'k', 'i', 'e' ]
```

### join()

**join()** - combines an array of strings into one string, using a separator

```typescript
const exampleList: string[] = ["example", "dashed", "name"];

const joinedSpace = exampleList.join(" ");
const joinedNoSep = exampleList.join("");

console.log(joinedSpace); // "example dashed name"
console.log(joinedNoSep); // "exampledashedname"
```

### startsWith() & endsWith()

**startsWith() and endsWith()** - returns a boolean indicating if a string starts/ends with the specified suffix, respectively

```typescript
const name: string = "Tamas";

console.log(name.startsWith("t")); // false
console.log(name.startsWith("T")); // true
console.log(name.startsWith("To")); // false

console.log(name.endsWith("as")); // true
console.log(name.endsWith("i")); // false
```

### indexOf()

**indexOf()** - returns the index of the first occurrence of a substring. If the substring is not found, it returns -1

```typescript
const developer: string = "Naomi";

console.log(developer.indexOf("N")); // 0

const city: string = "Los Angeles";
console.log(city.indexOf("New")); // -1
```

### includes()

**includes()** - returns a boolean if you only need to know whether a substring exists

```typescript
const city: string = "Los Angeles";

console.log(city.includes("Los")); // true
console.log(city.includes("New")); // false
```

### slice()

**slice()** - extracts a portion of a string and returns a new string

```typescript
const name: string = "Tamas";

const result_1 = name.slice(2);
const result_2 = name.slice(0, 3);

console.log(result_1); // mas
console.log(result_2); // Tam
```

### repeat()

**repeat()** - repeat a string a specified number of times

```typescript
const text: string = "Hello";
console.log(text.repeat(3)); // "HelloHelloHello"
```

### toUpperCase() & toLowerCase()

**toUpperCase(), toLowerCase()** - format string casing

```typescript
const greeting: string = "hello World !";

console.log(greeting.toUpperCase()); // "HELLO WORLD !"
console.log(greeting.toLowerCase()); // "hello world !"
```

## Arrays

### Adding elements

#### push()

**push()** - adds one or more items to the end of an array

```typescript
const numbers: number[] = [1, 2, 3];

numbers.push(4);

console.log(numbers); // [ 1, 2, 3, 4 ]

numbers.push(5, 6);

console.log(numbers); // [ 1, 2, 3, 4, 5, 6 ]
```

#### Extending arrays using `push()`

```typescript
const numbers: number[] = [1, 2, 3, 4, 5];
const evenNumbers: number[] = [6, 8, 10];

numbers.push(...evenNumbers);

console.log(numbers); // [1, 2, 3, 4, 5, 6, 8, 10]
```

#### unshift()

**unshift()** - add elements to the beginning of the array and return the new length

```typescript
const desserts: string[] = ["cake", "cookies", "pie"];

console.log(desserts.length); // 3

const newLength = desserts.unshift("ice cream");

console.log(desserts); // ["ice cream", "cake", "cookies", "pie"];
console.log(desserts.length); // 4
```

### Remove elements

#### pop()

**pop()** - remove and return the last element from an array

If the array is **empty**, then the return value will be `undefined`.

```typescript
const desserts = ["cake", "cookies", "pie"];
desserts.pop();

console.log(desserts); // ["cake", "cookies"];
```

#### shift()

**shift()** - remove and return the first element from an array

If the array is **empty**, then the return value will be `undefined`.

```typescript
const desserts = ["cake", "cookies", "pie"];
desserts.shift();

console.log(desserts); // ["cookies", "pie"];
```


### splice() - insert, replace, remove elements

**splice()** - can insert, replace, or remove elements at a specified index

`array.splice(start, deleteCount, item1, item2, ...);`

> [!important]
> The **return value** for the `splice()` method will be an **array of the items removed from the array**.
> If **nothing is removed**, then an **empty array** will be returned.
>
> This method will **mutate the original array**, modifying it **in place** rather than creating a new array.

```typescript
const numbers: number[] = [1, 2, 5, 6];

numbers.splice(2, 0, 3, 4); // [ 1, 2, 3, 4, 5, 6 ]

numbers.splice(3, 3); // [ 1, 2, 3 ]

numbers.splice(1, 1, 4); // [ 1, 4, 3 ]
```

```typescript
const numbers: number[] = [1, 2, 12, 13, 5, 6];
const rightNumbers: number[] = [3, 4];

numbers.splice(2, 2, ...rightNumbers); // [ 1, 2, 3, 4, 5, 6 ]
console.log(numbers);
```

### Other

#### indexOf()

**indexOf()** - finding the first index of a specific element within an array

If the element cannot be found, then it will return `-1`.

```typescript
const fruits = ["apple", "banana", "orange", "banana"];
const index = fruits.indexOf("banana");

console.log(index); // 1
console.log(fruits.indexOf("not found")); // -1
```

#### includes()

**includes()** - check if an array contains a specific value

```typescript
const programmingLanguages = ["JavaScript", "Python", "C++"];

console.log(programmingLanguages.includes("Python")); // true
console.log(programmingLanguages.includes("Perl")); // false
```

#### concat()

**concat()** - returns a new array without modifying the original array

Can merge two or **more** arrays.

```typescript
const numbers: number[] = [1, 2, 3];
const moreNumbers: number[] = [4, 5, 6];

const combined: number[] = numbers.concat(moreNumbers);

console.log(combined); // [1, 2, 3, 4, 5, 6]
console.log(numbers); // [1, 2, 3]
```

```typescript
const fruits = ["apple", "banana"];
const fruits2 = ["orange", "lemon"];
const fruits3 = ["strawberry", "raspberry"];

const newFruits = fruits.concat(fruits2, fruits3);

console.log(newFruits);
// [ 'apple', 'banana', 'orange', 'lemon', 'strawberry', 'raspberry' ]
```

**reverse()** - reverses an array in place

```typescript
const desserts = ["cake", "cookies", "pie"];
console.log(desserts.reverse()); // ["pie", "cookies", "cake"]
```

#### slice()

**slice()** - returns a new array containing a shallow copy of a portion of the original array, specified by start and end indices

> [!important]
> The new array contains **references to the same elements** as the original array (not duplicates).
>
> This means that if the elements are **primitives** (like numbers or strings), the values are **copied**
>
> If the elements are **objects** or **arrays**, the **references** are **copied**, not the objects themselves.

```typescript
const programmingLanguages = ["JavaScript", "Python", "C++"];
const newList = programmingLanguages.slice(1);

console.log(newList); // ["Python", "C++"]
```

### Spread Syntax

The spread syntax is used to create **shallow copies** of an array.

```typescript
const originalArray = [1, 2, 3];
const shallowCopiedArray = [...originalArray];

shallowCopiedArray.push(4);

console.log(originalArray); // [1, 2, 3]
console.log(shallowCopiedArray); // [1, 2, 3, 4]
```

### Shallow Copy

If the elements are **primitives** (like numbers or strings), the values are **copied**.

If the elements are **objects** or **arrays**, the **references** are **copied**, not the objects themselves.

```typescript
type MyArray = [string, { name: string }];

const original: MyArray = ["primitive", { name: "Tamas" }];
const copy: MyArray = [...original];

console.log(copy);
// [ 'primitive', { name: 'Tamas' } ]

copy[0] = "changed";
copy[1].name = "Anna";

console.log(original); // [ 'primitive', { name: 'Anna' } ]
console.log(copy); // [ 'changed', { name: 'Anna' } ]
```

### Array Destructuring

```typescript
const fruits: string[] = ["apple", "banana", "orange"];

const [first, second, third] = fruits;

console.log(first); // "apple"
console.log(second); // "banana"
console.log(third); // "orange"
```

**Rest Syntax**: This allows you to capture the remaining elements of an array that haven't been destructured into a new array.

```typescript
const fruits: string[] = ["apple", "banana", "orange", "mango", "kiwi"];
const [first, second, ...rest] = fruits;

console.log(first); // "apple"
console.log(second); // "banana"
console.log(rest); // ["orange", "mango", "kiwi"]
```

## Objects

### Definition

An object is a **data structure** that is made up of **properties**. A property consists of a **key** and a **value**. To access data from an object you can use either **dot notation** or **bracket notation**.

```typescript
const person = {
  name: "Alice",
  age: 30,
  city: "New York"
};

console.log(person.name);  // Alice
console.log(person["name"]); // Alice
```

### Set a Property of an Existing Object

```typescript
const person = {
  name: "Alice",
  age: 30
};

person.job = "Engineer"
person["hobby"] = "Knitting"
console.log(person);  // {name: 'Alice', age: 30, job: 'Engineer', hobby: 'Knitting'}
```

### Removing Properties From an Object

#### `delete` operator

`delete` - operator is used to remove a property from an object.

```typescript
const person = {
  name: "Alice",
  age: 30,
  job: "Engineer"
};

delete person.job;

console.log(person.job); // undefined
```

### Checking if an Object has a Property

#### Object.hasOwn()

**Object.hasOwn()** - modern, recommended way to check if an object has a property as its own (not inherited)

The syntax is `Object.hasOwn(object, propertyName)`.

It returns `true` if the property exists on the object and false if it does not, regardless of the property's value.

This makes it safer than `hasOwnProperty()` and more reliable than `if (obj.prop)` when values can be `0`, `false`, `null`, or `undefined`.

```typescript
const person = {
  name: "Alice",
  age: 30
};

console.log(Object.hasOwn(person, "name")); // true
console.log(Object.hasOwn(person, "job")); // false
```

A more detailed example showing why Object.hasOwn() is more reliable than checking the value directly:

```typescript
const settings = {
  darkMode: false,
  fontSize: 0,
  language: null
};

// Object.hasOwn() correctly sees these properties exist
console.log(Object.hasOwn(settings, "darkMode")); // true (value is false, but exists)
console.log(Object.hasOwn(settings, "fontSize")); // true (value is 0, but exists)
console.log(Object.hasOwn(settings, "theme"));    // false (property was never added)

// Using if() directly is unsafe for falsy values!
if (settings.darkMode) {
  console.log("Dark mode on"); // Does NOT print — misleading!
}

// Object.hasOwn() is the safe way
if (Object.hasOwn(settings, "darkMode")) {
  console.log("darkMode exists, value is:", settings.darkMode); // darkMode exists, value is: false
}
```

#### hasOwnProperty()

**hasOwnProperty()** - returns a `boolean` indicating whether the object has the specified property as its own property

```typescript
const person = {
  name: "Alice",
  age: 30
};

console.log(person.hasOwnProperty("name")); // true
console.log(person.hasOwnProperty("job")); // false
```

#### `in` Operator

*`in`* - operator will return `true` if the property exists in the object

```typescript
const person = {
  name: "Bob",
  age: 25
};

console.log("name" in person);  // true
```

### Accessing Properties From Nested Objects

```typescript
const person = {
  name: "Alice",
  age: 30,
  contact: {
    email: "alice@example.com",
    phone: {
      home: "123-456-7890",
      work: "098-765-4321"
    }
  }
};

console.log(person.contact.phone.work); // "098-765-4321"
```

### Working with the Optional Chaining Operator `?.`

This operator lets you **safely** access object properties or call methods without worrying whether they exist.

```typescript
const user = {
  name: "John",
  profile: {
    email: "john@example.com",
    address: {
      street: "123 Main St",
      city: "Somewhere"
    }
  }
};

console.log(user.profile?.address?.street); // "123 Main St"
console.log(user.profile?.phone?.number);   // undefined
```

### Object Methods

```typescript
const person = {
  name: "Bob",
  age: 30,
  sayHello: function() {
    return "Hello, my name is " + this.name;
  }
};

console.log(person.sayHello()); // "Hello, my name is Bob"
```

### Object Destructuring

```typescript
const person = { name: "Alice", age: 30, city: "New York" };

const { name, age } = person;

console.log(name); // Alice
console.log(age);  // 30
```

### Working with JSON

#### JSON.stringify()

**JSON.stringify()** - used to convert a JavaScript object into a JSON string

```typescript
const user = {
  name: "John",
  age: 30,
  isAdmin: true
};

const jsonString = JSON.stringify(user);
console.log(jsonString); // '{"name":"John","age":30,"isAdmin":true}'
```

#### JSON.parse()

**JSON.parse()** - converts a JSON string back into a JavaScript object

```typescript
const jsonString = '{"name":"John","age":30,"isAdmin":true}';
const userObject = JSON.parse(jsonString);

// result: { name: 'John', age: 30, isAdmin: true }
console.log(userObject);
```
