# Basic JavaScript :wave: :earth_africa:

## Table of contents

1. [Comments](#comments)
2. [Variables](#variables)
3. [Numbers](#number)
4. [Strings](#strings)
5. [Arrays](#arrays)
6. [Functions](#functions)
7. [Conditionals and comparison](#conditionals-and-comparison)
8. [Objects](#objects)
9. [Loops](#loops)
10. [Some built-in methods](#some-built-in-methods)

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
To ensure reusability, functions accept parameters. They act as placeholders for the values that are to be input to a function when it is called. The actual values that are input (or "passed") into a function when it is called are known as arguments. The `return` statement is used to send a value back out of a function.


```javascript
function functionWithArgs(num1, num2) {
  return num1 + num2;
}

const result = functionWithArgs(1, 2); // 3
```

Scope refers to the visibility of variables. Variables which are defined outside of a function block have Global scope. This means, they can be seen everywhere in your JavaScript code. Variables which are declared without the `let` or `const` keywords are automatically created in the `global` scope. This can create unintended consequences elsewhere in your code or when running a function again. Variables which are declared within a function, as well as the function parameters, have local scope. That means they are only visible within that function. It is possible to have both local and global variables with the same name. In this case, the local variable takes precedence over the global one.
A function can include the `return` statement but it does not have to. In the case that the function doesn't have a `return` statement, when you call it, the function processes the inner code but the returned value is `undefined`. When a `return` statement is reached, the execution of the current function stops and control returns to the calling location.
In computer science a queue is an abstract data structure where items are kept in order. New items can be added at the back of the queue and old items are taken off from the from the fron off the queue.

```javascript
function nextInLine(arr, item) {
    arr.push(item);
    item = arr.shift();
    return item;
}

const testArr = [1, 2, 3, 4, 5];

console.log("Before: " + JSON.stringify(testArr));
console.log(nextInLine(testArr, 6));
console.log("After: " + JSON.stringify(testArr));
```

---

## Conditionals and comparison

Booleans may only be one of two values: `true` or `false`.
The are many comparison operators in JavaScript, all of these return a `boolean` value. The most basic operator is the equality operator `==`, which compares two values and returns true if they're equivalent.
The stric equality operator `===`, unlike the equality operator, which attempts to convert both values being compared to a common type, does not perform a type conversion. If the values being compared have different types, they are considered unequal, and the strict operator will return false.
The `typeof` operator can determine the type of a variable or a value.
The inequality operator `!=` is the opposite of the equality operator. There is also the strict inequality operator `!==`, which is the opposite of the strict equality.
The greater than operator `>`, grater than or equal to `>=`, less than `<`, and less than or equal to `<=` compares the values of two numbers.
To test more conditions at the same time, the logical and operator `&&` returns `true` if and ondly if the operands to the left and right of it are true.
The logical or operator `||` returns `true` if either of the operands is true.
`if` statements are used to make decisions in code. The keyword `if` tells JavaScript to execute the code in the curly braces under certain conditions, defined in the parentheses. These conditions are known as `boolean` conditions. When the condition evaluates to `true`, the program executes the statement inside the curly braces. A `else` statement is an alternate block of code executed when the condition checked in the `if` block is `false`.
To check multiple conditions we can use the `else if` statement.

```javascript
if (num > 15) {
      return "Bigger than 15";
} else if (num < 5) {
  return "Smaller than 5";
} else {
  return "Between 5 and 15";
}
```

To check many options, you can use a switch statement. A `switch` statement tests a value and can have many `case` statements which define various possible values. Statements are executed from the first matched `case` value until a `break` is encountered. `case` values are tested with strict equality. A `default` statement can be added to the `switch` statement, it acts like a final `else` in a `if/else` chain. If the `break` statement is omitted from a `switch` statement's `case`, the following `case` statement(s) are executed until a `break` is encountered.

```javascript
function sequentialSizes(val) {
  let answer = "";
  switch(val) {
    case 1:
    case 2:
    case 3:
      answer = "Low";
      break;
    case 4:
    case 5:
    case 6:
      answer = "Mid";
      break;
    case 7:
    case 8:
    case 9:
      answer = "High";
      break;
  }
}
```

The conditional operator, also called the ternary operator, can be used as a one line `if-else` expression. The syntax i `a ? b : c`. where `a` is the condition, `b` is the code to run when the condition returns `true`, and `c` is the code to run when the condition returns `false`. Multiple ternary operators can be used.

```javascript
function findGreaterOrEqual(a, b) {
  return (a === b) ? "a and b are equal" : (a > b) ? "a is greater" : "b is greater";
}
```

---

## Objects

Objects are similar to `arrays`, except that instead of using indexes to access and modify their data, you access the data in objects through what are called `properties`. Objects are useful for storing data in a structured way, and can represent real world objects. If your object has any non-string properties, JavaScript will automatically typecast them as strings. To access properties of an object we can use the dot notation `.` or the bracket notation `[]`. The bracket notation is used to access property with a space in its name.
To delete properties from an object we can use the `delete` keyword.

```javascript
const cat = {
    "name": "Whiskers",
    "legs": 4,
    "tails": 1,
    "enemies": ["Water", "Dogs"],
    "collar": true,
}

const catTail = cat.tails;
const catName = cat["name"];
delete cat.collar;
```

Objects can be thought of as key/value storage, like a dictionary. If you have tabular data, you can use an object to lookup values rather than `switch` statement or an `if/else` chain. This is most useful when you know that your input data is limited to a certain range.

```javascript
function phoneticLookup(val) {
  let result = "";
  switch(val) {
    case "alpha":
      result = "Adams";
      break;
    case "bravo":
      result = "Boston";
      break;
    case "charlie":
      result = "Chicago";
      break;
    case "delta":
      result = "Denver";
      break;
    case "echo":
      result = "Easy";
      break;
    case "foxtrot":
      result = "Frank";
  }
  return result;
}

// The switch statement can be refactored as an object
function phoneticLookup(val) {
  let result = "";
  const lookup = {
    "alpha": "Adams",
    "bravo": "Boston",
    "charlie": "Chicago",
    "delta": "Denver",
    "echo": "Easy",
    "foxtrot": "Frank",
  }
  result = lookup[val];
  return result;
}
```

The `.hasOwnProperty(propname)` method of objects determines if that object has the given property name.
A JavaScript object is one way to handle flexible data. They allow for arbitrary combinations of `strings`, `booleans`, `arrays`, `functions`, and `objects`. To access sub-properties of objects, it is possible to chain together the dot or bracket notation.

```javascript
const myStorage = {
  "car": {
    "inside": {
      "glove box": "maps",
      "passenger seat": "crumbs"
     },
    "outside": {
      "trunk": "jack"
    }
  }
};

const gloveBoxContents = myStorage.car.inside["glove box"];
```

---

## Loops

Loops are used to run the same code multiple times. A `while` loop runs while a specified condition is true and stops once that condition is no longer true.

```javascript
const ourArray = [];
let i = 0;

while (i < 5) {
  ourArray.push(i);
  i++
}
```

A `for` loop runs a specific number of times. They are declared with three optional expressions separated by semicolons:
`for (a; b; c)`, where `a` is the initialization statement, `b` is the condition statement, and `c` is the final expression.
The initialization statement is executed one time only before the loop starts. The condition statement is evaluated at the beginning of every loop iteration and will continue as lons as it evaluates to `true`. When the condition is `false` at the start of the iteration, the loop will stop executing. The final expression is executed at the end of each loop iteration, prior to the next condition check.

```javascript
const ourArray = [];

for (let i = 0; i < 10; i += 2) {
  ourArray.push(i);
}
```

A `do...while` loop will first `do` one pass of the code inside the loop no matter what, and then continue to run the loop `while` the specified condition evaluates to `true`.
Recursion is the concept that a function can be expressed in terms of itself. To help understand this, start by thinking about the following task: multiply the first `n` elements of an array to create the product of those elements.

```js
// using a for loop
function multiply(arr, n) {
  let product = 1;
  for (let i = 0; i < n; i++) {
    product *= arr[i]
  }
}

// multiply(arr, n) == multiply(arr, n - 1) * arr[n - 1]; multiply can be rewritten in terms of itself
function multiply(arr, n) {
  if (n <= 0) {
    return 1;
  } else {
    return multiply(arr, n - 1) * arr[n - 1];
  }
}
```

The recursive version of `multiply` breaks down like this. In the bad case, where `n <= 0`, it returns 1. For larger values of `n`, it calls itself, but with `n - 1`. 

---

## Some built-in methods

Random numbers are useful for creating random behavior. `Math.random()` function generates a random decimal between 0 (inclusive) and 1 (exclusive).
`Math.random()` is usually used with `Math.floor()` to generate whole numbers. `Math.floor()` rounds the number down to its nearest whole number. 

```javascript
Math.floor(Math.random() * 20);

/* Generating a random whole number within a range
The formula used is:
Math.floor(Math.random() * (max - min + 1)) + min*/

Math.floor(Math.random() * (20 - 15 + 1)) + 15
```

`parseInt()` parses a string and returns an integer. It can take a second argument for the radix, which specifies the base of the number in the string. It can be an integer between 2 and 36.

```javascript
// the radix says that 11 is in the binary system, which corresponds to the integer 3
const a = parseInt("11", 2); 
```