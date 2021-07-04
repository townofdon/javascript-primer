# Statements && Expressions

"Computers are dumb."

This is a mantra that my first boss, Chiedo drilled into my head. Computers are not smart. They just do exactly what they are told to do. There is no "magic". Things don't "just work". If something works correctly, or if a program contains a bug, it's not the computer's fault. The computer is just doing what a computer does: _computing stuff_.

"Javascript is a scripting or programming language," [according to MDN Web docs](https://developer.mozilla.org/en-US/docs/Learn/JavaScript/First_steps/What_is_JavaScript). This just means that Javascript reads instructions (statements) one-by-one from start to finish.

Understanding that computers are dumb and just do what they're told is the beginning of learning development, in my opinion.

## Lines of Code

Each line of code in a software has a number.

This is so that one developer can say to another developer, "look at line 237".

This is also very useful when receiving an error: "Syntax Error: unexpected '<' at line 128".

To demonstrate this, try the following:

- Open RunJS
- Go to Preferences -> General
- Check the box to enable `Show Line Numbers`, and close the window
- Paste the following snippet into RunJS:

```
console.log('I am on line one!');
console.log('I am on line two!');
console.log('I am on line three!');
```

## Javascript Statements

In Javascript, the instructions that the computer reads are called "statements".

[W3 Schools explains JS statements](https://www.w3schools.com/js/js_statements.asp) like so:

- A computer program is a list of "instructions" to be "executed" by a computer.
- In a programming language, these programming instructions are called statements.
- A JavaScript program is a list of programming statements.

Most JavaScript programs contain many JavaScript statements.

The statements are executed, one by one, in the same order as they are written.

## Semicolons (`;`)

Semicolons separate JavaScript statements.

```
let a = 1 + 2;             // statement one
const b = "Howdy Pardner"; // statement two
fireRocketShip();          // statement three
```

You can also have multiple statements on the same line of code (however this is generally NOT recommended as
it impairs code readability):

```
const a = 1; const b = 2; const c = 3;
```

You'll hear me harp on code readability a LOT in this tutorial. It's of prime importance to keep things as
simple as possible for our primate brains.

> For now, don't worry about knowing exactly what is happening in the code examples above. The main takeaway:
Javascript contains statements separated by semicolons (`;`).

## Expressions

In Javascript, an **expression** is a unit of code that can be reduced to a single value.

A good example of this is compound expressions on the right-hand side of an assignment operator (`=`):

```
// This syntax may look strange, but is perfectly valid.
// The example breaks up the statements so that one is one each line.
var result = (1 + 1)  // expression one
           + (2 + 2)  // expression two
           + (3 + 3); // expression three - semicolon also denotes end-of-statement
```

The JS engine will **evaluate** the above expressions like so:

```
// PSEUDO-CODE - steps of evaluating above expressions:
(1 + 1) + (2 + 2) + (3 + 3) // step 1
2       + (2 + 2) + (3 + 3) // step 2
2       + 4       + (3 + 3) // step 3
2       + 4       + 6       // step 4
12                          // step 5

// RESULT AFTER EVALUATED EXPRESSION:
var result = 12;
```

Note that the **parentheses** `(...)` in the code above only used to demonstrate the grouping of various
expressions. However, parentheses are the go-to way to insert additional complex expressions into a statement:

```
// The expression inside the PARENTHESES gets evaluated first (x + y) before multiplication (*) operator
const calculated = ( calculateComplexFormula() + getOffsetNum() ) * getScalarNum();
```

That example was deliberately obtuse... all you need to know is that **parentheses** can be used
to group expressions, and sub-expressions, and sub-sub-expressions... you get the point.

### Left-to-Right Evaluation

Javascript always evaluates **expressions** from left-to-right.

Consider the following example (DON'T worry about understanding `function`, `const`, assignment `=`, etc.,
just consider the ORDER of how the expressions get evaluated):

```
// -- copy and paste this example into RunJS --

function a() { console.log('a'); return 1; }
function b() { console.log('b'); return 2; }
function c() { console.log('c'); return 3; }
function d() { console.log('d'); return 4; }
function test() {
  let exprOne, exprTwo;
  // KEY TAKEAWAY: WHAT ORDER WILL THE LOGS FOLLOW?
  const result =
    ( exprOne = a() * b() ) + // first expression -> (1 * 2) = 2
    ( exprTwo = c() * d() );  // second expression -> (3 * 4) = 12
  console.log(`${exprOne} + ${exprTwo} = ${result}`);
}
test();
// outputs:
// >> 'a'
// >> 'b'
// >> 'c'
// >> 'd'
// >> '2 + 12 = 14'
```

Try changing the code from the above example and see what happens:

- Under the `const result =` line, switch the order of `a`, `b`, `c`, and `d`
- Try replacing the multiplication operator (`*`) with the addition operator (`+`)
- **For bonus points:** - Try removing the function calls (AKA function invocations) by removing the parentheses `()` from `a()`, `b()`, etc.
  - Tip - don't mess with the lines of code containing the `function` keyword

&nbsp;

**Takeways**

If you absorbed nothing else from the information presented above - here's all you really need to know:

- Javascript statements are a set of instructions performed one-by-one
- Javascript expressions get evaluated left-to-right
- You can have multiple expressions in a single statement