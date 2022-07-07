# ES6 :pencil: 
## Table of contents

1. [let and const](#let-and-const)
2. [Arrow functions](#arrow-functions)
3. [Destructuring](#destructuring)


---

## let and const

When you declare a variable with `let` inside a block, statement, or expression, its scope is limited to that block, statement, or expression.
Objects assigned to a variable using a `const` declaration are still mutable. Using the `const` declaration only prevents reassignment of the variable identifier. To ensure your data doesn't change, JavaScript provides a function `Object.freeze` to prevent data mutation.

```JavaScript
let obj = {
    name: "FreeCodeCamp",
    review: "Awesome"
};

Object.freeze(obj);
obj.review = "bad";
obj.newProp = "Test";
console.log(obj);
```

---

## Arrow functions

In JavaScript, we often don't need to name our functions, especially when passing a function as an argument to another function. Instead we create inline functions. ES6 provides us with the syntactic sugar to not have to write anonymous functions this way. Instead, you can use arrow function syntax:

```JavaScript
const myFunc = (item) => {
    return item * 2;
}

// if there is only a return value, the function can be rewritten as
const myFunc = () => "value";

// if it has a single parameter, the parentheses enclosing the parameter may be omitted
const doubler = item => item * 2;
```

ES6 introduces default parameters for functions.

```JavaScript
const greeting = (name = "Anonymous") => "Hello " + name;
```

With the `rest parameter` for function parameters, you can create functions that take a variable number of arguments. These arguments are stored in an array that can be accessed later from inside the function. The rest parameter eliminates the need to check the `args` array and allows us to apply `map()`, `filter()` and `reduce()` on the parameters array.

```javascript
const sum = (...args) => {
    return args.reduce((a, b) => a + b, 0);
}
```

The spread operator allows us to expand arrays and other expressions in places where multiple parameters or elements are expected. The spread operator only works in-place, is not possible to assign the spreaded array to a variable

```javascript
// The ES5 code uses apply() to compute the maximum value in an array
var arr = [6, 89, 3, 45];
// Math.max.apply(null, arr) is used because Math.max(arr) return NaN. Math.max() expects comma-separated arguments, but not an array
var maxiumus = Math.max.apply(null, arr);

// The spread operator makes this syntax much better
const maximus = Math.max(...arr);
```

---

## Destructuring

Destructuring assignment is special syntax introduced in ES6, for neatly assigning values taken directly from an object. It allows to assign a new variable name when extracting values.

```javascript
const user = { name: "John Doe", age: 34 };

const { name: userName, age } = user;

// Destructuring values from nested objects
const user2 = {
    johnDoe: {
        age: 34,
        email: "johnDoe@freeCodeCamp.com"
    }
}

const { johnDoe: { age: userAge, email: userEmail }} = user;
```

One key difference between the spread operator and array destructuring is that the spread operator unpacks all contents of an array into a comma-separated list. Consequently, you cannot pick or choose which elements you want to assign to variables. In this example `a` is `1`, `b` is `2`, and `c` is `5`. The commas are used to reach the desired index

```javascript
const [a, b,,, c] = [1, 2, 3, 4, 5, 6];
console.log(a, b, c);
```

In some situations involving array destructuring, we might want to collect the rest of the elements into a separate array. The result is similar to `Array.prototype.slice()`. `a` and `b` would equal to `1` and `2`, `arr` would equal to `[3, 4, 5, 7]`.

```javascript
const [a, b, ...arr] = [1, 2, 3, 4, 5, 7];
```