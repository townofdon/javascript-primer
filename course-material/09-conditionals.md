# Control Flow - Conditionals

In programming, we often need to write code such that:

- if X, do action A
- if Y, do action B
- else (otherwise) do action C

Enter the `if` statment.

## If Statement

An `if` statment is a way to execute varying blocks of code depending on the results of an expression.

Basic syntax:

```
if (true) {
  console.log('This statement will always get executed since the condition was `true`!');
}
```

Let's break down the basic syntax:

- The `if` keyword begins the conditional statement
- The parentheses `(...)` contains an **expression** which evaluates to `true` or `false`
- If the expression evaluates to `true`, the statement inside the curly brackets `{...}` is executed


Now for an example with multiple possible outcomes:

```
const x = <SOME_NUMBER>; // note - this is a common way to write "pseudo-code"

if (x > 4) {
  console.log('Greater than four, my dude!');
} else {
  console.log('Less than or equal to four, my good sir');
}
```

Let's break down what's happening above:

- If `x > 4` evaluates to `true`, then:
  - The statement inside the FIRST set of curly braces `{...}` runs
  - Prints `"Greater than four, my dude!"`
- If `x > 4` does NOT evaluate to `true`, then:
  - The bracketed statement following the `else` keyword runs instead
  - Prints `"Less than or equal to four, my good sir"`

**If statements** can be as long or as short or as nested as you need them to be. Like this top-notch example:

```
// PSEUDO-CODE
if (isDogFriendly) {
  if (isDogHouseTrained) {
    if (isDogOld) {
      gentlyPetTheDog();
    } else {
      petTheDog();
    }
  } else {
    // dog is not house trained
    walkTheDog();
  }
} else {
  // dog is not friendly so let's train it
  trainTheDog();
}
```

> Note - I personally recommend making every effort to AVOID nesting conditionals. Other developers and your future self will thank you. Flat logical structures are much easier to wrap our reptilian brains around and less prone to bugs due to human error.

