# Control Flow - Conditionals

In programming, we often need to write code such that:

- if X, do action A
- if Y, do action B
- else (otherwise) do action C

Enter the `if` statment.

## If Statement

An `if` statment is a way to execute varying blocks of code depending on the results of an expression.

Basic syntax:

```javascript
if (true) {
  console.log('Look ma, no hands!');
}
```

Let's break down the basic syntax:

- The `if` keyword begins the conditional statement
- The parentheses `(...)` contains an **expression** which evaluates to `true` or `false`
- If the expression evaluates to `true`, the statement inside the curly brackets `{...}` is executed

Now for an example with multiple possible outcomes:

```javascript
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

```javascript
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

> Note - I personally recommend making every effort to AVOID nesting conditionals (placing if-statements inside if-statements). Other developers (and your future self) will thank you. Flat logical structures are much easier to wrap our reptilian brains around and less prone to bugs due to human error.

## Else If Statement

Sometimes you have situations where you have a number of possible outcomes.

In Javascript, you simply chain an additional `if` statement on the else clause to create
a "chain" of conditional branches.

```javascript
const swallow = {
  // try changing this to a different type
  type: 'african',
};

if (swallow.type === 'african') {
  console.log('African swallows are not migratory!');
} else if (swallow.type === 'european') {
  console.log('European swallows could not carry two coconuts; it\'s a simple matter of weight ratios!');
} else if (swallow.type === 'australian') {
  console.log('Now that\'s a big bird!');
} else {
  console.log('This type of swallow is unknown to us');
}
```

> Nerd note - Javascript's `else if` statement is similar to conditional branching in C++, C#, and Java.
However other languages have a separate keyword entirely for the `else if` branch: Python has the keyword
`elif`, and Ruby has `elsif`.

## Switch statements

In the example above, there is a bit of repetition. We programmers like to avoid repetition as much as possible.

`switch` statements are another way to construct conditional branches in Javascript.

Let's refactor the previous example to instead utilize a switch statement (the outcome is exactly the same):

```javascript
const swallow = {
  // try changing this to a different type
  type: 'african',
};

switch (swallow.type) {
  case 'african':
    console.log('African swallows are not migratory!');
    break;
  case 'european':
    console.log('European swallows could not carry two coconuts; it\'s a simple matter of weight ratios!');
    break;
  case 'austrailian':
    console.log('Now that\'s a big bird!');
    break;
  default:
    console.log('This type of swallow is unknown to us');
}
```

Pros:

- Easier to read
- Less repetition

Cons:

- If we forget a `break` statement, then unexpected outcomes will occur

## Early Returns

This is a more advanced concept, but I'll introduce it here because this one pattern can drastically cut down
on the size of code, simplify logic, and make it easier to comprehend (quite helpful for a meat computer which
contains an amygdala).

My rule of thumb: _return early and often_.

Observe:

```javascript
// Option A - with conditional branching (the ordinary way)
function doSomething() {
  if (conditionA) {
    return 'A';
  } else if (conditionB) {
    return 'B';
  } else {
    return 'C';
  }
}

// Option B - with early returns
function doSomething() {
  if (conditionA) return 'A';
  if (conditionB) return 'B';
  return 'C';
}
```

You'll learn about `function`s and the `return` statement later. What's more important to note is that
the second example not only saves us lines of code, but also _lessens cognitive load_ as our eyes attempt to
absorb the information on the screen.

If we combine early returns and the `switch` statement, we get what I consider
one of the most elegant patterns in Javascript:

```javascript
const swallow = {
  // try changing this to a different type
  type: 'african',
};

function getSwallowDescription(swallow) {
  switch (swallow.type) {
    case 'african':
      return 'African swallows are not migratory!';
    case 'european':
      return 'European swallows could not carry two coconuts; it\'s a simple matter of weight ratios!';
    case 'austrailian':
      return 'Now that\'s a big bird!';
    default:
      return 'This type of swallow is unknown to us';
  }
}

console.log(getSwallowDescription());
```

Now, I will admit that some people gripe about this potentially opening up the possibility of forgetting a `break`
statement if the developer refactors and removes the `return`. However, to mitigate this, my personal rule of thumb is to
ALWAYS use only `return` statements OR `break` statements exclusively, never mixing them together.

I use this pattern ALL THE TIME and highly recommend adding this pattern to your code arsenal.
