# Basic Data Structure :building_construction:

## Table of contents

1. [Arrays](#arrays)
2. [Objects](#objects)

---

## Arrays

A one-dimensional array has only one level, it does not have any other arrays nested within it. All arrays have a length property, which can be accessed with the syntax `Array.length`

```javascript
let simpleArray = ['one', 2, 'three', true, false, undefined, null];
```

A multi-dimensional array contains other arrays.

```javascript
let complexArray = [
  [
    {
      one: 1,
      two: 2
    },
    {
      three: 3,
      four: 4
    }
  ],
  [
    {
      a: "a",
      b: "b"
    },
    {
      c: "c",
      d: "d"
    }
  ]
];
```

Each array item has an index. This index doubles as the position of that item in the array. JavaScript arrays are zero-indexed, meaning that the first element of an array is actually at the zeroth position. In order to retrieve an element from an array we can enclose an index in brackets and append it to the end of an array. This is knows as bracket notation.
Arrays are mutable. The `push()` method adds element to the end of an array, and `unshift()` adds element to the beginning.
The `pop()` method removes an element from the end of an array, while `shift()` removes an element from the beginning.
The `splice()` method allows to remove any number of consecutive elements from anywhere in an array. It can take up to 3 parameters. The first two are integers which represent indexes in the array that `splice()` is being called upon. The first parameter is the index on the array from which to begin removing elements, while the second parameter indicates the number of elements to delete. The third parameter comprise one or more element(s) to add to the array.

```javascript
const numbers = [10, 11, 12, 12, 15];
const startIndex = 3;
const amountToDelete = 1;
numbers.splice(startIndex, amountToDelete, 13, 14);
console.log(numbers) // [10, 11, 12, 13, 14, 15]
```

`slice()` copies or extract a given number of elements to a new array, leaving the array it is called upon untouched. It takes only 2 parameter -- the first is the index at which to begin extraction, and the second is the index at which to stop extraction

```javascript
let weatherConditions = ['rain', 'snow', 'sleet', 'hail', 'clear'];
let todaysWeather = weatherConditions.slice(1, 3); // ['snow', 'sleet']
```

To copy the whole content of the array, or combine two arrays, the spread operator `...` can be used.

```javascript
let thisArray = ['sage', 'rosemary', 'parsley', 'thyme'];
let thatArray = ['basil', 'cilantro', ...thisArray, 'coriander']; //['basil', 'cilantro', 'sage', 'rosemary', 'parsley', 'thyme', 'coriander']
```

`indexOf()` allows to check for the presence of an element on an array. It takes an element as a parameter, and when called, it returns the position, or index, of that element, or `-1` if the element does not exist on the array.

> Here's an example of a complex multi-dimensional array:

```javascript
let nestedArray = [
  ['deep'],
  [
    ['deeper'], ['deeper'] 
  ],
  [
    [
      ['deepest'], ['deepest']
    ],
    [
      [
        ['deepest-est?']
      ]
    ]
  ]
];

console.log(nestedArray[2][1][0][0][0]) // 'deepest-est?'
```

---

## Objects

At their most basic, objects are just collections of key-value pairs. They are pieces of data (values) mapped to unique identifiers called properties (keys). Object properties can be nested to an arbitrary depth, and their values can be any type of data supported by JavaScript.

```javascript
let nestedObject = {
  id: 28802695164,
  date: 'December 31, 2016',
  data: {
    totalUsers: 99,
    online: 80,
    onlineStatus: {
      active: 67,
      away: 13,
      busy: 8
    }
  }
};
```

To iterate through all the keys within an object, the `for...in` statement is used. Objects do not maintain an ordering to stored keys like arrays do; thus a key's position on an object, or the relative order in which it appears, is irrelevant when referencing or accessing that key.

```javascript
for (let user in users) {
    console.log(user)
}
```

To generate an array which contains all the keys stored in an object, the `Object.keys()` method can be used. This method takes an object as the argument and returns an array of strings representing each property in the object