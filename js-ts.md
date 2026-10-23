- [Todo](#todo)
- [String](#string)
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
  - [push()](#push)
  - [Extending arrays using `push()`](#extending-arrays-using-push)
  - [concat()](#concat)
  - [splice()](#splice)


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

## String

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

### push()

**push()** - adds one or more items to the end of an array

```typescript
const numbers: number[] = [1, 2, 3];

numbers.push(4);

console.log(numbers); // [ 1, 2, 3, 4 ]

numbers.push(5, 6);

console.log(numbers); // [ 1, 2, 3, 4, 5, 6 ]
```

### Extending arrays using `push()`

```typescript
const numbers: number[] = [1, 2, 3, 4, 5];
const evenNumbers: number[] = [6, 8, 10];

numbers.push(...evenNumbers);

console.log(numbers); // [1, 2, 3, 4, 5, 6, 8, 10]
```

### concat()

**concat()** - returns a new array without modifying the original array

```typescript
const numbers: number[] = [1, 2, 3];
const moreNumbers: number[] = [4, 5, 6];

const combined: number[] = numbers.concat(moreNumbers);

console.log(combined); // [1, 2, 3, 4, 5, 6]
console.log(numbers); // [1, 2, 3]
```

### splice()

**splice()** - can insert, replace, or remove elements at a specified index

`array.splice(start, deleteCount, item1, item2, ...);`

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
