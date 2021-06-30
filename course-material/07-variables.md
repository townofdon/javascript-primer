# Variables && Assignment

And finally we get to variables, without which we'd be very limited in what we could do.

Variables allow us to assign a value in memory and re-use that value as many times as we want.

```
var name = "Rob Zombie"
var age = 33;
var favoriteColor = "tomato";

console.log(`Hello, my name is ${name}`); // >> outputs "Hello, my name is Don"
console.log(`I am ${age} years old`); // >> outputs "I am 33 years old"
console.log(`My favorite color is ${favoriteColor}`); // >> outputs "My favorite color is tomato"
```

## Types of Variables

### `var`

This was used mainly in earlier versions of Javascript. It is generally now recommended to use `let` or `const` instead.

Any variable instantiated (created) using `var` can be `reassigned` any number of times.

```
// instantiate and set age to 33.
var age = 33;

// change age to 25
age = 25;
```

Changing any variable's value is considered a **data mutation**. More on this later.

### `let`

This works exactly the same as `var`, except is generally considered safer to use as its scope is limited to the current code block.

```
let numCars = 2;

// just bought a new car!
numCars = 3; // NOTE - there is a better way to do this - see below.
```

### `const`

The `const` keyword is used to instantiate a value that never changes. (This is at least true for primitive data types).

```
// things that will not likely change:
const name = "Don Juan";
const countryOfOrigin = "United States";
const favVideoGame = "Halo";
```

If you try and re-assign a `const` variable, JS will throw an error.

## Assignment

The `=` operator is used to assign a value to a variable (or a property of an object, but that's a later topic).

NOTE THAT `=` IS VERY DIFFERENT FROM `==`.

- `=` - the assignment operator
- `==` - the equality operator
- `===` - the strict equality operator

Anyways, all you need to know is that `=` always means ASSIGNMENT, not EQUALITY.

```
const skyColor = "blue";
let numCars = 3;

// just bought a new car!
numCars += 1;

console.log(numCars) // >> outputs `4`
```

## Assignment Shortcuts

```
let x = 0;

// ALL of the following increment a value by 1:
x = x + 1;
x += 1;
x++;

// ALL of the following decrement a value by 1:
x = x - 1;
x -= 1;
x--;

// ALL of the following multiply a value by 2:
x = x * 2;
x *= 2;

// ALL of the following divide a value by 2:
x = x / 2;
x /= 2;
```
