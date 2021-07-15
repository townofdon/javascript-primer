# Functions

Functions are actions. Events. Things that happen.

**Kick** the can.  
**Fire** the gun.  
**Send** the email.

Functions are **invoked** or **called** when we want to execute (or run) the function.

Functions come in many flavors.

## Named Functions

Ways to write functions (all of these are valid):

```
// declarative function
function speakFriendAndEnter() {
  console.log("Mellon");
}

// anonymous function expression assigned to a variable
const challengeBalrog = function() {
  console.log("YOU SHALL NOT PASS!");
}

// ES6 anonymous arrow function assigned to a variable
const scoldPippen = () => {
  console.log("Fool of a Took!");
};
```

And we invoke them like so - with opening and closing parentheses `()`:

```
speakFriendAndEnter(); // outputs "Mellon"
challengeBalrog(); // outputs "YOU SHALL NOT PASS!"
scoldPippen(); // outputs "Fool of a Took!"
```

## Anonymous Functions

_([He who must not be named](https://en.wikipedia.org/wiki/Lord_Voldemort))._

Anonymous functions are just functions that are unnamed.

```
const doStuff = function() { console.log('stuff'); }
//              ^ Anonymous function

const doSomething = () => { console.log('something') };
//                  ^ Anonymous function

const bankAccount = {
  processPayment: () => { console.log('Payment has been processed!'); }
  //              ^ Anonymous function
};
```

So anonymous functions are really very simple. I'm just pointing them out so that you don't
get confused when you hear the term.

## Function returns

Functions can **return** values.

This does two things:

- Finishes function execution (function stops running)
- Returns the value back to the caller

```
function add(num1, num2) {
  return num1 + num2;
  console.log("Un-reachable code!!");
}

add(1, 1); // 2
add(2, 4); // 6
add(3, 5); // 8

const theSumOfAllThings = add(1, 1) + add(2, 2) + add(3, 3) + add(4, 4);
console.log(theSumOfAllThings); // outputs `20`
```

The return **type** can be:

- any primitive value
- an **object**
- an **array**
- even another **function** :scream:

A function that returns a function can be difficult to wrap your brain around! This is called a
**curried** function and leads to some interesting patterns:

```
function add(a) {
  return function (b) {
    return a + b;
  }
}

const plusTwo = add(2);

plusTwo(0); // 2
plusTwo(1); // 3
plusTwo(2); // 4
plusTwo(3); // 5

// We can rewrite the `add` function in a much more concise and readable form:
const addTo = (a) => (b) => a + b;

const plusSix = addTo(6);

plusSix(0); // 6
plusSix(1); // 7
plusSix(2); // 8
plusSix(3); // 9
```

## Function parameters

Functions can specify **parameters** that they can accept when they are called.

We pass in **arguments** for those parameters when we invoke (call) a function.

```
function sayHelloTo(name) {
  console.log(`Howdy, ${name}`!);
}

sayHelloTo("Dave"); outputs "Howdy, Dave!"
sayHelloTo("Suzy"); outputs "Howdy, Suzy!"
sayHelloTo("Rico"); outputs "Howdy, Rico!"
```

We can provide default values for our function parameters:

```
function sayHelloTo(name = "Stranger") {
  console.log(`Howdy, ${name}`!);
}

sayHelloTo("Tom"); // outputs "Howdy, Tom!"
sayHelloTo();      // outputs "Howdy, Stranger!"
```

You can have as many or as little parameters as you like.

```
// generally this is considered a BAD pattern:
function sum(a, b, c, d, e, f, g) {
  return a + b + c + d + e + f + g;
}
```

## Callback Functions

Functions can not only **return** a function; they also accept functions as valid arguments.

One of the most commonly used patterns in JavaScript is the **Callback Function** pattern.

You are going to see callback functions ALL THE TIME. So get used to them.

Okay, a quick and dirty example:

```
const processPayment(onProcessingComplete) {
  // fetch user's account info...
  // determine if the user has access...
  // perform some calculations...
  // transfer bitcoin...
  onProcessingComplete();
}

processPayment(() => { console.log('Hooray! Payment has been processed!'); });
```

The above example is an extreme simplification. For instance, we would need to add error handling in a real-world situation. But hopefully you get the picture for how this powerful pattern works!

Quick note: it's a common naming convention to prefix callback function parameter names with `"on"`. For example:

- `onCompleted`
- `onSuccess`
- `onError`
- `onClick`
- `onScroll`

Etc.

> Callback functions were originally the primary way to implement **asynchronous** programming in JavaScript.  
> If you think about it - callback functions are perfect for:
>
> - defining WHAT action should be performed
> - without knowing WHEN it should occur
>
> Examples might include:
>
> - showing a pop-up when the user clicks a mouse button
> - enabling a form when the page finishes loading
> - showing an error if an action times out

> Understanding **callbacks** is essential to understanding **promises**. And understanding
> promises is essential to understanding the **async/await** pattern.

Confused yet? Just wait til we get to asynchronous programming. :sweat_smile:

**But it's all good, because you've got this.**
