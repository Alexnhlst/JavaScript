# Basic JavaScript

## Table of contents

1. [Comments](#comments)
2. [Variables](#variables)
3. [Numbers](#number)
4. [Strings](#strings)

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