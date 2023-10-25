# Operators

In code, you need to evaluate and compute stuff. I mean, you are using a... _computer_... right?

To do so, you will need to learn your operators. Please Excuse My Dear Aunt Sally, all that jazz.

## Addition, Subtraction, Multiplication, Division

Copy and paste each of the following code blocks into RunJS _(one at a time)_, and ponder what is happening:

```javascript
// ADDITION
// - Use the `+` operator. Simple enough.
// - when used on `number` types, sums the numbers
// - when used on `string` types, concatenates the result into a string

5 + 5; // >> outputs `10`
"My " + "Cirona"; // >> outputs "My Cirona"
```

```javascript
// SUBTRACTION
// - Use the `-` operator.
// - Only used on `number` types.

10 - 6; // >> outputs `4`
```

```javascript
// MULTIPLICATION
// - use the `*` operator.
// - only used on `number` types.

9 * 9 * 9; // >> outputs `729`
```

```javascript
// DIVISION
// - use the `/` operator.
// - only used on `number` types.

99 / 9; // >> outputs `11`
```

```javascript
// MODULUS
// - use the `%` operator
// - gets the REMAINDER of the value after division
// - only used on `number` types

2 % 2; // >> outputs `0`;
3 % 2; // >> outputs `1`;
4 % 2; // >> outputs `0`;
5 % 2; // >> outputs `1`;
6 % 2; // >> outputs `0`;
```

```javascript
// PARENTHESES
// - use `(` and `)` brackets
// - used for math operations and also JS scopes (a really advanced topic)

(5 + 5) * 2; // >> outputs `20`

// ---------------------------------------------
// You can combine ops into a single evaluation.
// (Order of math operations applies)
// ---------------------------------------------

(5 * 2 + 2 * 5) / 10 - 2; // >> outputs `0`
```

> **Did you notice?** All of the above lines end with a semicolon (`;`). This is the way that traditional Javascript determines the end of a **statement**.

## More complex maths

For other math calculations, like exponents, absolute value, square root, etc., you can
simply use the `Math` library (comes standard in all Javascript):

```javascript
// ABSOLUTE VALUE
Math.abs(-1000); // outputs `1000`

// EXPONENT
Math.pow(10, 5); // outputs `100000`

// SQUARE ROOT
Math.sqrt(16); // outputs `16`

```

See the [Math docs](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Math) for more possible uses!
