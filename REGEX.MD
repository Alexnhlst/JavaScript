# Regular expression :grey_exclamation:

## Table of contents

1. [Test Method](#test-method) 
2. [RegEx](#regex)
3. [Match](#match)

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

## RegEx

To search multiple strings, you can use the `alternation` or `OR` operator `|`. A regex made of three patterns would look like this: `/yes|no|maybe/`
Case (or sometimes letter case) is the difference between uppercase letters and lowercase letters. You can math both case using what is called a flag. The ignore flag `i` can be used by appending it to the regex: `/ignorecase/i`. This regex can match the strings `ignorecase`, `igNoreCase`, and `IgnoreCase`.

---