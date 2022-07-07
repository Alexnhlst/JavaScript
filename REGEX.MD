# Regular expression :grey_exclamation:

## Table of contents

1. [Test Method](#test-method) 
2. [RegEx - 1](#regex---1)
3. [Match](#match)
4. [RegEx - 2](#regex---2);
---

Regular expressions are used in programming languages to match parts of strings. You create patterns to help you do that matching. If you want to find the word `the` in the string `The dog chased the cat` you could use the following regular expression: `/the/`.
JavaScript has multiple ways to use regex. One way is using the `.test()` method. It takes the regex, applies it to a string, and returns `true` or `false`.

```JavaScript
let testStr = "freeCodeCamp";
let testRegex = /Code/;
testRegex.test(testStr)
```

>In this example, only the exact math with the word `Code` will return true, `CODE` or `code` will return false

---

## RegEx - 1

To search multiple strings, you can use the `alternation` or `OR` operator `|`. A regex made of three patterns would look like this: 
>`/yes|no|maybe/`

Case (or sometimes letter case) is the difference between uppercase letters and lowercase letters. You can math both case using what is called a flag. The ignore flag `i` can be used by appending it to the regex: 
>`/ignorecase/i`. This regex can match the strings `ignorecase`, `igNoreCase`, and `IgnoreCase`.

---

## Match

The `.match()` method is used to extract the actual matches found

```JavaScript
"Hello, World!".match(/Hello/);
```

---

## RegEx - 2

To search or extract a pattern more than once, you can use the global search flag `g`: 
Multiple flags can be combined in one patter like so: 
>`/Repeat/gi`

The wildcard character will match any one character. It can be used to match a pattern which only some letters are specified, like: 
>`/hu./`

Character classes allow to define a group of characters you wish to match by placing them inside square brackets.
For example, you want to match `bag`, `big`, and `bug` but not `bog`. 
> The regex `/b[aiu]g/` contains the character class that will only match the characters `a`, `i`, or `u`

To define a range of characters to match, you can use the hyphen character `-`: 
>`/[a-e]at/`

The range of characters is not limited to letters but it also works to match a range of numbers.
>`/[a-g0-5]/` matches any letters between `a` and `g`, and any number between `0` and `5`, inclusive.

Negated character sets are used to exclude characters you do not want to match. To create a set, you place a caret character `^`: 
>`/[^aeiou]gi`

