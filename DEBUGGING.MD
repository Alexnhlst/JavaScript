# Debugging :bug:

## Table of contents

1. [JavaScript console](#javascript-console)
2. [typeof](#typeof)
3. [Debugging](#debugging)

---

## JavaScript console

The `console.log()` method, which "prints" the output of what's within its parentheses to the console, will likely be the most helpful debugging tool.
`console` has many methods like `log`, `warn`, and `clear`.

---

## typeof

`typeof` can be used to check the data structure, or type, of a variable. This is useful in debugging when working with multiple data types.
Type errors can lurk in calculations or function calls. JavaScript recognizes seven primitive (immutable) data type: `Boolean`, `Null`, `Undefined`, `Number`, `String`, `Symbol` (introduced in ES6), and `BigInt` (introduced in ES2020), and one type for mutable items: `Object` (In JavaScript, arrays are technically a type of object)

---

## Debugging

One syntax-level issue that fast typers can commiserate with is the humble spelling error. Transposed, missing, or mis-capitalized characters in a variable or function name will have the browser looking for an object that doesn't exist - and complain in the form of a reference error.
Another syntax error to be aware of is that all opening parentheses, brackets, curly braces, and quotes have a closing pair.
JavaScript allows the use of both single `'` and double `"` quotes to declare a string.
Branching programs, i.e. ones that do different things if certain conditions are met, rely on `if`, `else if`, and `else` statements in JavaScript. The condition sometimes takes the form of testing whether a result is equal to a value.
This logic is spoken (in English, at least) as "if x equals y, then ..." which can literally translate into code using the ``=``, or assignment operator. This leads to unexpected control flow in your program.
The assignment operator `=` in JavaScript assigns a value to a variable name. And the `==` and `===` operators check for equality (the triple `===` tests for strict equality, meaning both value and type are the same).
When a function or method doesn't take any arguments, you may forget to include the (empty) opening and closing parentheses when calling it. Another bug to watch out is when a function's arguments are supplied in the incorrect order. If the are arguments are the same type, the code wont raise a runtime error, but the logic of the code won't make sense.
Off by one errors (sometimes called OBOE) crop up when you're trying to target a specific index of a string or array, or when looping over the indices of them. JavaScript indexing starts at zero which means the last index is always one less than the length of the item. If you try to access an index equal to the length, the program may throw an index out of range reference error or print `undefined`.
Sometimes it's necessary to save information, increment counters, or re-set variables within a loop. A potential issue is when variables either should be reinitialized, and aren't, or vice versa. This is particularly dangerous if you accidentally reset the variable being used for the terminal condition, causing an infinite loop.
Loops are great tools when you need your program to run a code block a certain number of times or until a condition is met, but they need a terminal condition that ends the looping. Infinite loops are likely to freeze or crash the browser, and cause general program execution mayhem, which no one wants.