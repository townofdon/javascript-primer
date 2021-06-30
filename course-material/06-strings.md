# Strings

A string is a collection of ASCII characters, including alpha-numeric and other symbols.

Strings are used for:

- human-readable text - words, phrases, characters
- formatted numbers, like currency
- also be used as lookup keys for data structures (more on this later)
- storing serialized data in a database for data-persistence

To put it more simply: strings are for TEXT.

## All about the strings, dude

Here are some examples of using strings in code:

```
// a basic string
console.log("Hola Mundo");

// concatenated (combined) strings:
console.log("WOM" + "BAT); // prints "WOMBAT"
console.log("one" + "two" + "three"); // prints "onetwothree"
console.log("One small step for doge " + "one giant leap for Elon Musk);
```

```
// full-fledged example using variables
var firstName = "Paul"
var lastName = "Progeny"
console.log(firstName + " " + lastName);
```

A lot is happening above.

- we are assigning the string "Paul" to the variable named "firstName"
- we are assigning the string "Progeny" to the variable named "lastName"
- we are logging out the _concatenated_ result of `firstName`, a single **whitespace** character, and `lastName`

`concatenation` is the process of combining strings (or arrays, but that's a topic for later).

We use the `+` operator to concatenate strings. Note that this operator's behavior changes based on the `type`
of variable or type of statement currently being evaluated. (E.g. if `+` is used for two `number`s, it will calculate
their sum).

## **More examples**

```
// string with double quotes
"Bob Ross"

// string with single quotes (equally valid in Javascript)
'Boss Rob'

// concatenated strings using `+` op
var experience = 'tedious';
'This' + ' ' + 'is' + ' ' + 'so' + ' ' + experience // >> outputs "This is so tedious"

// template string using backticks (`) --> allows for string interpolation (injecting dynamic content into string output)
var firstName = "Don";
var lastName = "Juan";
`${firstName} ${lastName}` // >> outputs "Don Juan"

// can mix and match any kind of string
'a' + "b" + `c${'d'}` // >> outputs "abcd"
```

> Side note - did you notice the missing `console.log` in the example above? This is each line in this example is a standalone **expression**. An expression is something that gets evaluated and returns a value. If you want to nerd out and take a deep dive into expressions, the [MDN documentation on expressions is a really great resource](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Expressions_and_Operators).