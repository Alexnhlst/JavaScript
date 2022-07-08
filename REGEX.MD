# Regular expression :grey_exclamation:

## Table of contents

1. [Test Method](#test-method)
2. [Match](#match) 
3. [RegEx](#regex)
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

## Match

The `.match()` method is used to extract the actual matches found

```JavaScript
"Hello, World!".match(/Hello/);
```

---

## RegEx 
To search multiple strings, you can use the `alternation` or `OR` operator `|`. A regex made of three patterns would look like this: 
>`/yes|no|maybe/`

Case (or sometimes letter case) is the difference between uppercase letters and lowercase letters. You can math both case using what is called a flag. The ignore flag `i` can be used by appending it to the regex: 
>`/ignorecase/i`. This regex can match the strings `ignorecase`, `igNoreCase`, and `IgnoreCase`.

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

The `+` character is used to check if a character appears one or more times in a row.
> `/a+/g` would find a single match in `aabc` and return `["aa"]`. If it were instead checking the string `abab`, it would find two matches and return `["a", "a"]` because the `a` characters are not in a row

The `*` character is used to check if a character appears zero or more times.
> /go*/ would return `["g"]` in the phrase `gut feeling`

A greedy match finds the longest possible part of a string that fits the regex pattern and returns it as a match.
A lazy match finds the smallest possible part of the string that satisfies the regex pattern.
> `/t[a-z]*i/` to the string `"titanic"` would return `["titani"]` since regular expressions are by default greedy. The `?` character changes to lazy matching. `/t[a-z]*?i/` returns `["ti"]`

The dollar sign character `$` is used to search the end of strings.
> `/story$/` would return `true` in the string `"This is a never ending story"`

The character class `[a-z]` is so common that a shortcut for it exists. The `\w` shortcut is equal to `[A-Za-z0-9_]`
There is also the opposite pattern: `\W` which is equal to `[^A-Za-z0-9_]`
> The syntax for it is `/\w/`

To search all numbers, the shortcut `\d` is equal to `[0-9]`
The opposite shortcut is `\D`: `[^0-9]`
Whitespace can be searched with `\s`. This pattern also matches carriage return, tab, form feed, and new line characters `[ \r\t\f\n\v]`
The opposite is `\S`: `[^ \r\t\f\n\v]`
You can specify the lower and upper number of patterns with quantity specifiers. They are used with curly brackets
> To match only the letter `a` appearing between `3` and `5` times in the string `ah`, your regex would be `/a{3,5}h`

The `?` character can be used to check for zero or one of the preceding
>For example `/colou?r/` would be true both for color and colour

Lookaheads are patterns that tell JavaScript to look-ahead in your string to check for patterns further along.
A positive lookahead will look to make sure the element in the search pattern is there, but won't actually match it.
> A positive lookahead is used as `(?=...)` where `...` is the required part that is not matched

A negative lookahead will look to make sure the element in the search pattern is not here
> A positive lookahead is used as `(?!=...)` where `...` is the pattern that you do not want to be there

>A practical use of lookaheads is to check two or more patterns in one string. Here is a (naively) simple password checker that looks for between 3 and 6 characters and at least one number: 

```JavaScript
let password = "abc123";
let checkPass = /(?=\w{3,6})(?=\D*\d)/
```

To check for groups of characters using Regular Expression, parentheses are used.
>To find `Penguin` or `Pumpkin` in a string, you can use `/P(engu|umpk)in/g`

Capture groups, used to find repeated substrings, are constructed by enclosing the regex pattern to be captured in parentheses. The substring matched is saved to a temporary "variable", which can be accessed within the same regex using a backslash and the number of the capture group. Capture groups are automatically numbered by the position of their opening parentheses (left to right), starting at 1.

```JavaScript
let repeatStr = "row row row your boat";
let repeatRegex = /(\w+) \1 \1/;
repeatRegex.test(repeatStr); // Returns true
repeatStr.match(repeatRegex); // Returns ["row row row", "row"]
```

You can search and replace text in a strin using `.replace()` on a string. The inputs for `.replace()` is first the regex pattern you want to search for, the second parameter is the string to replace the match.

```JavaScript
let wrongText = "The sky is silver."
let silverRegex = /silver/;
wrongText.replace(silverRegex, "blue")
```

>You can also access capture groups in the replacement string with dollar signs `$`: `"Code Camp".replace(/(\w+)\s(\w+)/, '$2 $1');` The `replace` call would return the string `Camp Code`