# Variables && Assignment

And finally we get to variables, without which we'd be very limited in what we could do.

Variables allow us to assign a value in memory and re-use that value as many times as we want.

> Definition of a `variable` according to [Wikipedia](https://en.wikipedia.org/wiki/Variable_(computer_science)):
_a variable is a container for different types of data (like integer, float, String and etc...)_

> One distinction that is important to note is that the variable is not the same as the value itself;
instead think of the variable as a container that houses this value.

```javascript
var name = "Bob";
console.log(name); // outputs "Bob"
```

Breakdown of what just happened:

- Instantiated (created, declared) the variable labelled `name` using the keyword `var`
- Assigned the `string` value "Bob" to `name` using the `=` assignment operator
- Read from and printed the stored contents of `name` in our log statement

```javascript
var name = "Don"
var age = 33;
var favoriteColor = "tomato";

console.log(`Hello, my name is ${name}`); // >> outputs "Hello, my name is Don"
console.log(`I am ${age} years old`); // >> outputs "I am 33 years old"
console.log(`My favorite color is ${favoriteColor}`); // >> outputs "My favorite color is tomato"

// assign a different value to `name`
name = "Sufjan"

console.log(`Hello, my name is ${name}`); // >> outputs "Hello, my name is Sufjan"
```

Notice how easy it was to mutate (change) the value of the variable `name` in the example above.

## Types of Variables

### `var`

This was used mainly in earlier versions of Javascript. **It is generally now recommended to use `let` or `const` instead.**

Any variable instantiated (created) using `var` can be `reassigned` any number of times.

```javascript
// instantiate and set age to 33.
var age = 33;

// change age to 25
age = 25;
```

> Nerd note: changing any variable's value is considered a **data mutation**. More on this later.

### `let`

The assignment keyword `let` works exactly the same as `var`, except is generally considered safer to use as its scope is limited to the current code block.

```javascript
let numCars = 2;

// just bought a new car!
numCars = 3;

// NOTE - there is a better way to increment a number - see below.
```

### `const`

The `const` keyword is used to instantiate a value that never changes. (This is at least true for primitive data types).

```javascript
// things that will not likely change:
const name = "Don Juan";
const countryOfOrigin = "United States";
const favVideoGame = "Halo";
```

Things to note:

- If you try and re-assign a `const` variable, JS will throw an error
- A `const` variable MUST be assigned a value immediately in its declaration

  ```javascript
  const x; // throws SyntaxError
  ```

## Assignment

The `=` operator is used to assign a value to a variable (or a property of an object, but that's a later topic).

NOTE THAT `=` IS VERY DIFFERENT FROM `==`.

- `=` - the assignment operator
- `==` - the equality operator
- `===` - the strict equality operator

Anyways, all you need to know is that `=` always means ASSIGNMENT, not EQUALITY.

```javascript
const skyColor = "blue";
let numCars = 3;

// just bought a new car!
numCars += 1;

console.log(numCars) // >> outputs `4`
```

## Assignment Shortcuts

```javascript
let x = 0;

// increment a value by 1:
x = x + 1;
// or
x += 1;
// or
x++;

// decrement a value by 1:
x = x - 1;
// or
x -= 1;
// or
x--;

// multiply a value by 2:
x = x * 2;
// or
x *= 2;

// divide a value by 2:
x = x / 2;
// or
x /= 2;
```

## Naming Conventions

In Javascript, here are some industry-standard naming conventions:

- Variables use `camelCase` - e.g. `thisIsMyVariable`
- Constants use `CONSTANT_CASE` - e.g. `API_KEY`
- Classes use `PascalCase` - e.g. `MovieFilm`

## Variable Scope

**TL;DR:**

All you need to know for the time being:

- use `let` - if a variable's value will need to change
- use `const` - if a variable's value will NEVER change*
- do NOT use `var`

> Nerd note: objects and arrays should always use `const` even if they will be mutated. This is because JS objects are always assigned **by reference**. Instantiating an object with `const` is just saying that we won't ever be reassigning that object's pointer reference.

---

For those who want to dive deeper...

Assignment using the `var` keyword creates a variable in the global scope. 

Since in 99% of cases you
probably don't need to be messin' with the global scope, `let` and `const` are generally recommended instead.
Explicitly calling `window.someVar = 'x'` is equivalent to `var someVar = 'x'`.

```javascript
// example of implicit global scope
var someVar = 'x';
console.log(window.someVar); // outputs "x"

// example of non-global scope using `let`
let anotherVar = 'x';
console.log(window.anotherVar); // outputs `undefined`
```

This difference is very subtle but has massive implications.
