# Strings

A string is a collection of ASCII characters, including alpha-numeric and other symbols.

Strings are used for:

- human-readable text - words, phrases, characters
- formatted numbers, like currency
- also be used as lookup keys for data structures (more on this later)
- storing serialized data in a database for data-persistence

To put it more simply: strings are for TEXT.

## Basic Strings

There are several ways to construct a string primitive in Javascript.

All of the following produce identical results:

- double quotes - `"Hello World"`
- single quotes - `'Hello World'`
- backticks     - `` `Hello World` ``
  - note - strings wrapped in backticks are referred to as **template literals**

All of the above strings evaluate to the same primitive value of `"Hello World"`.

Try copying and pasting the following code into RunJS:

```javascript
"Hello World";
'Good to see you today';
`My name is Neo`;
```

> Nerd note - did you notice the missing `console.log` in the example above? This is each line in this example is a standalone **expression**. An expression is something that gets evaluated to a single value, as we covered in
the previous lesson [Statements and Expressions](04-statements-expressions.md). The console is displaying the
evaluated result of each expression (which incidentally is also a statement in this example).

## String Concatenation

One of the most common things we will need to do is combine strings together.

```javascript
// a basic string
"Hola Mundo"; // "Hola Mundo"

// concatenated (combined) strings:
"WOM" + "BAT"; // "WOMBAT"
"one" + "two" + "three"; // "onetwothree"
"One small step for doge, " + "one giant leap for Elon Musk";
```

```javascript
// full-fledged example using variables (this is a very common use-case)
var firstName = "Paul"
var lastName = "Progeny"
console.log(firstName + " " + lastName);
```

A lot is happening above. The only takeaway you need to know right now is:

- `firstName` and `lastName` represent string values that somehow get combined
  together into a single string.

**Concatenation** is the process of combining strings _(or arrays, but that's a topic for later)_.

One way to concatenate strings is using the `+` operator. That's what we used in the examples above.

Another way is to perform **string interpolation** - _see next section_.

> Important: the `+` operator changes behavior based on the `type` of variable or type of statement currently
being evaluated. (E.g. if `+` is used for two `number`s, it will calculate their sum).

## String Interpolation

"String interpolation" refers to replacing placeholders with values in a string literal.

> A [**literal**](https://en.wikipedia.org/wiki/Literal_(computer_programming)) is just a fixed value represented in code. Like the number `88` or the boolean `true` or the string `"Cats rule"`.

The string literal MUST use backticks: `` ` ` ``

Placeholder values are specified using a dollar sign and brackets: `${...}`

Example:

```javascript
var name = 'John Boy';
var movie = 'The Matrix';
`My name is ${name} and my favorite movie is ${movie}`;
// result: "My name is John Boy and my favorite movie is The Matrix"
```

## String Methods

All **primitives** have **properties** and **methods** that we have access to. The `string` primitive is no different.

Currently there is only one property for a `string` primitive:

- `length` - lists the number of characters in a string

There are many methods for a `string` primitive, including:

- `charAt(index)` - find the character from the specified index
- `includes(substring)` - determine whether string contains the substring entirely
- `toUpperCase()` - returns a new string transformed to uppercase
- `toLowerCase()` - returns a new string transformed to lowercase
- `trim()` - returns a new string with leading and trailing whitespace (blank spaces) removed

Both **properties** and **methods** utilize the dot operator `.` to access them.

Examples:

```javascript
'Wiley Coyote'.length; // `12`

'Bob Ross'.charAt(1); // "o"
// note that `charAt` is what we call "zero-indexed",
// meaning we start counting at 0, not 1

'Charlie Chaplin'.includes('Charlie'); // `true`
'Charlie Chaplin'.includes('gnarly'); // `false`

'darth vader'.toUpperCase(); // "Darth vader"
// note that only first letter is capitalized

'Han Solo'.toLowerCase(); // "han Solo"

'      lotsa blank space     '.trim(); // "lotsa blank space"
```

> Nerd note: methods (AKA functions) are called with opening and closing parentheses `()` while properties are not. We will cover functions in a later lesson.

There are a LOT more available methods that you can use on strings, but the above are a few of the more commonly-used ones.
An exhaustive list of available methods can be found in the [MDN docs](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String).

## Escaping Strings

What if we need to print the character `'`? How do we do that?

One way would be to wrap the string in double quotes like: `"`"`.

Another method is to escape our characters. We simply add a backwards-slash `\`
before the culprit and all is golden.

```javascript
'Scott\'s house is cool'; // result: "Scott's house is cool"
```

## More String Examples - recap

```javascript
// string with double quotes
"Bob Ross";

// string with single quotes (equally valid in Javascript)
'Boss Rob';

// concatenated strings using `+` op
var experience = 'tedious';
'This' + ' ' + 'is' + ' ' + 'so' + ' ' + experience; // "This is so tedious"

// template string using backticks (`) --> allows for string interpolation (injecting dynamic content into string output)
var firstName = "Don";
var lastName = "Juan";
`${firstName} ${lastName}`; // "Don Juan"

// can mix and match any kind of string
'a' + "b" + `c${'d'}`; // "abcd"
```

## Quick Rules

Some best practices and things I generally recommend:

- Default to single quote strings for normal usage
- Favor template literals (`` `${firstName} ${lastName}` ``) over concatenation (`firstName + ' ' + lastName`)

## Additional Resources

- [Dmitri Pavlutin - String Interpolation in Javascript](https://dmitripavlutin.com/string-interpolation-in-javascript/)
- [MDN docs - String](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String)
