# Primitive Data Types

Javascript primitive data types include the following:

- `number` - `1`, `-20`, `3.141592653589793`, etc.
- `boolean` - `true` or `false`
- `string` - `"Hello"`, `"A"`, `"b"`, `"C"`, etc.
- `null` and `undefined`

There are more primitives Than those listed above, however I've found that thees primitives
cover the vast majority of software development needs.

## Numbers

Numbers are discrete mathematical units used to quantify or measure things. In the code world
they operate much the same:

```
var numCars = 3;
var numBoats = 5;
var numAirplanes = 7;
console.log(numCars + numBoats + numAirplanes); // >> outputs "15"
```

Numbers in Javascript are floating point numerical representations. WUT?!

In simpler terms, this just lets us use decimal points in our numbers and it just works. (In other programming
languages you have to specify the right data type if you want to use decimals).

```
// very crude approximation of PI - Note that `Math.PI` holds this constant with a decent level of precision
var PI = 3.14159;
```

See [next section for some Mathematical Operators](./05-mathematical-operators.md) you can use in Javascript.

> Nerd note: Numbers are all instances of the global `Number` object and thus have **properties** and **methods** (in this way, they are like **objects**) - see [MDN Number documentation](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Number) for a deeper dive.

> Nerd note: Javascript's floating point number system does result in inaccuracies and loss of precision from time to time - just keep that in mind. See this [Stack Overflow example](https://stackoverflow.com/questions/588004/is-floating-point-math-broken) for a humerous example.

## Booleans

A boolean is just a data type with a value of `true` or a `false`, (`1` or `0`).

These are very convenient for turning things ON or OFF, or setting code flags (`isEnabled`, `isProcessing`), etc.

```
var isSuperDapper = true;
var isAnOldManFilledWithRegret = false;
```

> Don's Opinionated Note: I like to prefix `boolean` variables _(we'll learn about those soon)_ with "is" or "has" as much as possible - this makes code more consistent and easier to understand.

## Strings

These deserve a [whole chapter of their own](./06-strings.md).

## Null / Undefined

`null` and `undefined` are two very similar ways that Javascript uses to denote the absence of something.

A `null` value represents the _intentional_, _deliberate_ absence of a value.

An `undefined` value represents the absence of space and time. This is the dark void in which that one can lose themselves if they stare long enough. If something is `undefined` it's considered to _not exist_. _(We're really getting existential here aren't we...)_

> Note: every variable in Javascript will be `undefined` by default until it is explicitly assigned a value.

> Side note: `null` and `undefined` are what we call **falsey** values. You'll learn all about truthiness / falsiness later (and no, it unfortunately has nothing to do with Stephen Colbert).

**What you NEED TO KNOW about `undefined` vs. `null`?**

- Starting out, not much!
- `null` and `undefined` just mean that something isn't there
- `null` and `undefined` are NOT considered strictly identical _(key word "strictly")_

Run the following code in RunJS and ponder. If it goes over your head, DON'T WORRY! _(This is one of the quircks of Javascript; we also haven't covered logical operators yet)_:

```
null == undefined // >> true
null === undefined // >> false
```

**What you will _EVENTUALLY_ need to know:**

- `null` is used to intentionally denote the absence of something (think: a hole in a barrel, a car missing a VIN number, or a user not-yet logged into a website)
- `undefined` means that something does not exist in the known universe, for all intents and purposes

## Symbol

Symbols are a recent addition to Javascript, and are used to specify unique identifiers.

_No need to worry about `symbol`s for now._

&nbsp;

&nbsp;

Phew, that's a lot of information. Reward yourself with a scone and cup of coffee/tea/kombucha for all the knowledge you just gained.
