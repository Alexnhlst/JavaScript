# ES6 :pencil: 
## Table of contents

1. [let and const](#let-and-const)
2. [Arrow functions](#arrow-functions)

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