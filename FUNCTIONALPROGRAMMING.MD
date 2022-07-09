# Functional Programming :notebook:

## Table of contents

1. [Functional Programming](#functional-programming)
2. [.map()](#map)
3. [.filter()](#filter)
4. [.slice()](#slice)

---

## Functional Programming

Functional programming is a style of programming where solutions are simple, isolated functions, without any side effects outside of the function scope: `INPUT -> PROCESS -> OUTPUT`.
Functional programming is about:
    1. Isolated functions - there is no dependence on the state of the program, which includes global variables that are subject to change
    2. Pure functions - the same input always gives the same output
    3. Functions with limited side effects - any changes, or mutations, to the state of the program outside the function are carefully controlled

Some terminology:
    - *Callbacks* are the functions that are slipped or passed into another function to decide the invocation of that function.
    - *First class functions* are functions that can be assigned to a variable, passed into another funtion, or returned from another function. In JavaScript, all functions are first class functions
    - *Higher order functions* are functions that take a function as an argument, or return a function as a return function
    - *lambda* are functions passed in to or returned from another function

In English (and many other languages), the imperative tense is used to give commands. Similarly, an imperative style in programming is one that gives the computer a set of statements to perform a task. Often the statements change the state of the program, like updating global variables. In contrast, functional programming is a form of declarative programming. You tell the computer what you want done by calling a method or function. JavaScript offers many predefined methods that handle common tasks so you don't need to write out how the computer should perform them.
One of the core principles of function programming is to not change things. Changing or altering things is called *mutation*, and the outcome is called a *side effect*. A function, ideally, should be a pure function, meaning that it does not cause any side effects.
Another principle of functional programming is to always declare your dependencies explicitly. This means if a function depends on a variable or object being present, then pass that variable or object directly into the function as an argument.

## .map()

As its name suggests, functional programming is centered around a theory of functions. It would make sense to be able to pass them as arguments to other functions, and return a function from another function. Functions are considered first class objects in JavaScript, which means they can be used like any other object.
The `Array.prototype.map()` method iterates over each item in an array and returs a new array containing the results of calling the callback function on each element. It does this without mutating the original array. When the callback is used, it is passed three arguments. The first argument is the current element being processed. The second is the index of that element and the third is the array upon which the `map` method was called

```javascript
const users = [
  { name: 'John', age: 34 },
  { name: 'Amy', age: 20 },
  { name: 'camperCat', age: 10 }
];

const names = users.map(user => user.name); // [ 'John', 'Amy', 'camperCat' ]
```

---

## .filter()

`Array.prototype.filter()` calls a function on each element of an array and returns a new array containing only the elements for which that function returns `true`. In other words, it filters the array, based on the function passed to it. Like `map`, it does this without needing to modify the original array. The callback function accepts three arguments. The first argument is the current element being processed. The second is the index of that element and the third is the array upon which the `filter` method was called.

```javascript
const users = [
  { name: 'John', age: 34 },
  { name: 'Amy', age: 20 },
  { name: 'camperCat', age: 10 }
];

const usersUnder30 = users.filter(user => user.age < 30); // [ { name: 'Amy', age: 20 }, { name: 'camperCat', age: 10 } ].
```

---

## .slice()