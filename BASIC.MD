# Basic JavaScript :wave: :earth_africa:

## Table of contents

1. [Comments](#comments)
2. [Variables](#variables)
3. [Numbers](#number)
4. [Strings](#strings)
5. [Arrays](#arrays)
6. [Functions](#functions)

## Comments

Comments are lines of code ignored by JavaScript. THey are a great way to leave notes to yourself and to other people.

```JavaScript
// In-line comment.
```

```javascript   
/* Multi-line
comment*/
```

---

## Variables

In computer science, data is anything that is meaningful to the computer. JavaScript provides eight different data types: `undefined`, `null`, `boolean`, `string`, `symbol`, `bigint`, `number`, and `object`
Variables allow computers to store and manipulate data in a dynamic fashion. They are similar to the x and y variables used in mathematics, which means they're a simple name to represent the data we want to refer to.
To declare a variable in JavaScript, the keyword `var` is used (since ES6, `let` and `const` are used, more on that later)
Variable names can be made up of numbers, letters nad `$` or `_`, but may not contain spaces or start with a number.

```javascript
var name;
```

To store a value in a variable, the assignment operator `=` is used.

```javascript
var myVar;
myVar = 5;
```

When JavaScript variables are declared, they have an initial value of `undefined`. If you do a mathematical operation on a `undefined` variable your result will be `NaN` which means "Not a Number". If you concatenate a string with an `undefined` variable, you will get a string of `undefined`.
In JavaScript all variables and function names are case sensitive

> Best Practice
>
> Write variable names in camelCase. Multi-word variable names have the first word in lowercase and the first letter of each subsequent word is capitalized

One problem with `var` variable declaration is that you can easily overwrite variable declaration

```javascript
var camper = "James";
var camper = "David";
console.log(camper);
```

With the introduction of `let` in ES6, the problem doesn't occur anymore.

```javascript
let camper = "James";
let camper = "David";
console.log(camper);
```

```shell
SyntaxError: unknown: Identifier 'camper' has already been declared. (2:4)
```

To solve another problem, the `const` keyword was introduced. Once a variable is assigned with `const`, it cannot be reassigned.

```javascript
const FAV_PET = "Cats";
FAV_PET = "Dogs";
```

```shell
TypeError: "FAV_PET" is read-only
```

> Common practice
>
> It is common for developers to use uppercase variable identifiers for immutable values and lowercase or camelCase for mutable values

---

## Number

`Number` is a data type which represents numeric data.
The operators `+`, `-`, `*` , and `/` are used to perform basic math operations.
To increment/decrement a variable, the `++`/`--` operator is used.

```javascript
i++;
// is the equivalent of
i = i + 1;
```

A decimal number is sometimes referred to as floating point or floats.
The `%` operator gives the remainder of the division of two numbers.

```javascript
5 % 2 = 1;
Math.floor(5 / 2) = 2 // Quotient
2 * 2 = 4;
5 - 4 = 1; // Remainder
```

In programming, it is common to use assignments to modify the contents of a variable. Compound operators allow to do mathematical operations and assignments in one step.

```javascript
let myVar = 1;
myVar += 5; // 6
```

---

## Strings

To escape a quote from considering it as an end of string quote by placing a backslash `\` in front of the quote.

```javascript
const sampleStr = "Alan said, \"Peter is learning JavaScript\".";
```

Escape sequences 

| Code | Output |
| ---- | ------ |
| `\'` | single quote |
| `\"` | double quote |
| `\\` | backslash |
| `\n` | newline |
| `\r` | carriage return |
| `\t` | tab |
| `\b` | word boundary |
| `\f` | form feed |

The `+` operator is also used with `String` values concatenating them. In this case, `+` is called the concatenation operator.
To find the lenght of a `String` value we can add `.length` after the string variable or string literal
`String` values are immutable, which means that they cannot be altered once created;

```javascript
let myStr = "Bob";
myStr[0] = "J";
```

```shell
TypeError: Cannot assign to read only property '0' of string 'Bob'
```

---

## Arrays

With JavaScript `array` variables, we can store several pieces of data in one place.

```javascript
const sandwich = ["peanut butter", "jelly", "bread"];
```

Arrays can be nested inside other arrays.

```javascript
const teams = [["Bulls", 23], ["White Sox", 45]];
```

Arrays use zero-base indexing, meaning that the first element in the array has an index of 0. To access an element inside an array, square bracket notation `[]` is used, with the use of a specific index. To access elements inside of multi-dimentsional arrays, the first set of brackets refers to the entries in the outer-most array, and each additional pair of brackets refers to the next level of entries inside.

```javascript
const arr = [
    [1, 2, 3],
    [4, 5, 6],
    [7, 8, 9],
    [[10, 11, 12], 13, 14]
];

arr[3]; // [[10, 11, 12], 13, 14]
arr[3][0]; // [10, 11, 12]
arr[3][0][1]; // 11
```

The `.push()` method takes one or more parameters and "pushes" them onto the end of the array. The `.unshift()` mehtod "pushes" the element at the beginning of the array.
The `.pop()` method is used to pop a value off of the end of an array. This popped off value can be stored by assigning it to a variable. To remove the first value, the `.shift()` is used instead.

---

## Functions

In JavaScript, we can divide up our code into reusable parts called functions. They can be invoked by using their name followed by parentheses.

```javascript
function functionName() {
    console.log("Hello World");
}
functionName();
```