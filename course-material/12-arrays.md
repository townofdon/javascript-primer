# Arrays

Think of an array as a collection of items. A list of things.

```
const radNumbers = [1, 2, 3, 4, 5];

radNumbers.length; // 5
```

Above, we assigned an **array** of number **primitives** to the variable `radNumbers`.

Arrays can have lots of different types of values:

- numbers
- strings
- booleans
- objects
- functions (you will learn about these soon!)

Take this hodge podge for instance:

```javascript
const anObfuscatedAndOverlyComplexCollection = [
  0, // number
  "howdy pardner!", // string
  false, // boolean
  { make: 'Honda', model: 'Accord', year: 2000 }, // object
  function() {
    console.log("I am a lonely function in a lonely array")
  }
];
```

The above is a perfectly syntactically valid array. Though, if I ever found you
writing an array like the above, I'd promptly drive to your house and
give you a proper whooping. (It's ugly and hard to read)

What's cool about arrays? Well, lots of things.

- We can **iterate** over arrays (evaluate each item one-by-one)
- We can add items to an array
- We can remove items from an array
- We can modify the array (`sort`, `shuffle`, `reverse`)
- We can find an array item at a specific **index**

## Accessing Array Elements

We get an individual element from an array by accessing its **index**.

Arrays are **zero-indexed**, which means we just start counting from 0 instead of 1.

```javascript
const llamas = [
  'fred',
  'susan',
  'tom',
  'jenny'
];

llamas[0]; // "fred"
llamas[1]; // "susan"
llamas[2]; // "tom"
llamas[3]; // "jenny"

// What happens if we go outside the bounds of the array????
// Try it yourself and find out:
llamas[5];  // ???
llamas[-1]; // ???
```

If we try and access an array element that does not exist, we simply get a value of `undefined`.

> (Refer back to the [Primitives chapter - Null / Undefined](./05-primitives) for a refresher of our
> ethereal friend `undefined` who is devoid of substance).

## Adding Items To Arrays

We can add items to an array two ways:

- method 1: `arr.push( ... )`

  ```javascript
  const dogs = [
    'fluffer',
    'ralph',
  ];

  dogs.push('wolfie');
  console.log(dogs); // outputs ["fluffer", "ralph", "wolfie"];
  ```

- method 2: `arr.concat([ ... ])`

  ```javascript
  const myDogs = [
    'maggie',
  ];

  const otherDogs = [
    'spike',
    'isaac',
  ];

  allDogs = myDogs.concat(otherDogs);

  console.log(allDogs); // outputs ["Maggie", "Spike", "Isaac"]
  ```

- notice that `push` **mutates** the original array, whereas `concat` leaves the original array unchanged

> There are also other methods for adding stuff to arrays (see [MDN Docs - Array Methods](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array#instance_methods)), but you can look into those on your own time. For now, these two methods give you all that you need.

## Removing Items from Arrays

Whenever you change original data, that is called a **mutation**.

Since computers nowadays are so fast, it is generally considered safer to NOT mutate the original data unless there is a good reason to.

I'll show how to remove items from an array both ways - with and without data mutation.

```javascript
const fruits = [
  'apple',
  'banana',
  'orange',
  'watermelon',
];

// remove the first item and return its value:
const removedFruit = fruits.pop();

// `fruits` has been altered!
console.log(fruits); // outputs ["banana", "orange", "watermelon"]

console.log(removedFruit); // outputs "apple"
```

We remove items from the end of an array by using the **mutating** method `arr.shift()`:

```javascript
const carManufacturers = [
  'Tesla',
  'Honda',
  'Ford',
  'GM',
];
const bankruptManufacturers = [];

// remove the last item and return it:
const removed = carManufacturers.shift();

// add it to the other array
bankruptManufacturers.push(removed);

console.log(carManufacturers); // outputs ["Tesla", "Honda", "Ford"]

console.log(bankruptManufacturers); // outputs ["GM"]
```

## Adding / Removing Without Mutating

This is an ADVANCED section. Feel free to move on if your brain already feels like jelly.

I mentioned earlier that often it's important to avoid mutating things. The **tl;dr:** is that
mutations make it difficult to debug things in our code.

So how the heck do we add stuff or remove stuff from an array without changing the damn thing?

Like this:

```javascript
const customerIds = [1441, 2992, 3443, 4004];

// REMOVE CUSTOMER "3443" FROM ARRAY:

// - using `filter`
const filteredCustomerIds = customerIds.filter((id) => id !== 3443);

// - using `slice`
const filteredCustomerIds2 = customerIds.slice(0, 2).concat(customerIds.slice(3));

// ADD A NEW CUSTOMER TO THE ARRAY

// - using spread operator `...`

const newCustomerIds = [...customerIds, 5775]; // adds to the end of the array
const newCustomerIds2 = [5775, ...customerIds]; // adds to the beginning of the array

// - using concat

const newCustomerIds3 = customerIds.concat([5775]); // adds to the end of the array
```

So as you can see, there are quite a few different ways around this dillema. Personally, I prefer
`filter` for removing items and the spread operator `...` for adding new items.

## Modifying Arrays

There are loads of ways to modify an array. Let me touch on a few things:

`arr.filter` returns a new array where the **predicate** (the callback function) evaluates to **truthy**.

```javascript
const people = [
 'bob',
 'dave',
 'samson',
 'delilah',
];

// get all people who are not named "Bob"

people.filter((person) => person.name !== 'bob'); // ["dave", "samson", "delilah"]
```

## Traversing Arrays

We can **traverse** (or **iterate**) over arrays by using a **loop**. We will learn about loops
in the next section, but take this simple example in the meantime:

```javascript
const presidents = [
  'George Washington',
  'John Adams',
  'Thomas Jefferson',
  'James Madison',
  'James Monroe',
  // obviously the list is longer but you get the point
];

for (let i = 0; i < presidents.length; i++) {
 // NOTICE - WE ARE JUST USING `i` AS THE INDEX OF THE ARRAY
 console.log(presidents[i]);
}

// PRINTS THE FOLLOWING:
// "George Washington"
// "John Adams"
// "Thomas Jefferson"
// "James Madison"
// "James Monroe"
```

> There are actually lots of algorithms for shuffling numbers around. Here is a simple algorithm
> I found on StackOverflow that mutates the array in-place and shuffles it:
> https://stackoverflow.com/a/12646864
