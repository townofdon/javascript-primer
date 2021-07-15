# Objects

In Javascript, almost everything is an object. Every stinkin thing. (Except for primitives).

A car is an object. A person is an object. A house is an object. The sun is an object.

We use objects to represent (model) things in the real world. At least that's how I think about objects.

## Basic object syntax

```
const car = {
  make: 'Honda',
  model: 'Accord',
  year: 2000, // trailing comma
};
```

Trailing commas make it easy to add new information to an object without worrying about syntax errors.
(They also help with Git diffs - you'll learn about Git version control soon).

Object can have **properties**:

```
const person = {
  name: 'Dave', // string
  age: 32, // number
  isMarried: true, // boolean
};
```

Objects can have **methods** (these are just **functions**):

```
const person = {
  applyToJob() {
    console.log('applying to a rad job!');
  },
  driveCar() {
    console.log('driving the cool car');
  }
};
```

Objects can even have nested **objects** and **arrays** (we will cover arrays in the next section):

```
const airplane = {
  // NESTED OBJECT:
  manufacturer: {
    id: 1234,
    name: 'Boeing',
    email: 'support@boeing.com',
  },
  airportOrigin: {
    name: 'Los Angeles International Airport',
    code: 'LAX',
  },
  airportDestination: {
    name: 'Dulles International Airport',
    code: '??',
  },
  timeDeparture: '2021-07-01 19:30:00',
  timeArrival: '2021-07-02 21:21:00',
  // ARRAY:
  passengers: [
    {
      firstName: 'Dave',
      lastName: 'Debonair',
      age: 23,
      seatType: 'first-class',
    },
    {
      firstName: 'Sally',
      lastName: 'Salamander',
      age: 44,
      seatType: 'coach',
    },
  ],
};
```

The above is a SUPER simple data model representing an airplane.

The possibilities are limitless.

## Accessing Object properties

We access properties and methods of an object by using the dot `.` notation.

```
const superhero = {
  power: 100,
  specialAbility: 'super-smash',
  name: 'Dapper Debonair',
  alias: 'Dominique Dubois',
  useAbility: () {
    console.log('SMAAASH!!);
  },
};

// we access properties like so:
superhero.power; // 100
superhero.specialAbility: // "super-smash"

// methods are accessed the same way, and invoked (fired) via parentheses:
superhero.useAbility(); // outputs "SMAAASH!!"
```

## Advanced - by reference passing

We need to talk about pointers briefly.

I'm sorry.

Actually I'm not sorry. This is crucial knowledge. And I'm trying to save you from the pain I experienced
when I first started using Javascript.

All object **assignment** happens **by reference**.

I know this is Greek to you right now. I'll try to explain.

### Pointers

Pointers just mean that we are pointing to a memory address on our computer's RAM.

Anytime we instantiate a new object, we are actually creating a new **pointer** (as well as the underlying data).

```
// first, we instantiate a new object and assign it to the variable `x`
const x = { a: 1 };

// next, we assign `x` to a new variable `y`
const y = x;

// then, we change `y`:
y.a = 2;

// `y` was changed as expected
console.log(y); // outputs: "{a: 2}"

// however, `x` was ALSO CHANGED:
console.log(x); // outputs: "{a: 2}"
```

Whaaaaat? Let me try and explain why both `x` and `y` were changed in the previous example.

When we called `const y = x`, `y` was created with a **reference** to the same place in memory as `x`.
So when we mutated (updated) `y`, we ALSO mutated `x`.

I highly recommend you copy the example above into RunJS and play around with things to see what happens.
The best way to learn is to try things yourself.

**What you need to know:**

- Objects are assigned **by reference**
- In other words, anytime you assign one object to another object, they are essentially the _same object_
