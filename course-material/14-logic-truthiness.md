# Control Flow - Logic

Our examples until now have just dealt with strinctly `true` or `false` cases.

In the real world, things are often not that cut and dry. Is the airplane ready for flight? That is a whole checklist of items (conditions that need to be satisfied).

We need to figure out a way to boil lots of conditions down to a single `true` or `false` state.

Enter the world of logic!

## Logical Operators

- `!`  - logical NOT operator
- `||` - logical OR operator
- `&&` - logical AND operator

Here's how these operators work:

```javascript
// negate a condition
!true; // >> evaluates to `false`

// true if EITHER condition is true
false || true; // >> evaluates to `true`

// true if BOTH conditions are true
true && false; // >> evaluates to `false`;
```

Easy peasy.

Let's see how this aristotelian logic gets applied in an albeit contrived example:

```javascript
const hasWashedDishes = true;
const hasMowedGrass = false;
const hasCleanedRoom = true;

// use NOT to negate a condition
if (!hasWashedDishes) {
  console.log("Hey, I'm not your mom!");
} else {
  console.log("Thanks for doing the dishes!");
}

// use OR when only ONE of the conditions needs to be true
if (hasMowedGrass || hasCleanedRoom) {
  console.log("You can watch TV now!");
} else {
  console.log("You gotta finish your chores!");
}

// use AND when ALL of the conditions need to be true
if (hasWashedDishes && hasMowedGrass && hasCleanedRoom) {
  console.log("Okay, who are you and what have you done with my child?");
}
```

Conditionals can also be chained. Parentheses take precedence:

```javascript
// let's walk through these steps
(true && false) || !(false && true);
// this becomes:
(false) || !(false);
// which results in:
false || true;
// which evaluates to:
true;
```

We can also chain our logic into complex spaghetti-code! However just because you CAN do something doesn't mean that you SHOULD.

```javascript
// inferior way - logic is complex, brittle, and more error-prone
if (
  !isLoading &&
  !(hasError || errMessage) &&
  (isOwner || getHasPermission('view-all-grades')) &&
  getHasFeatureFlag('grade-management')
) {
  renderGradesListView();
}

// a better way - we can use the early return pattern (see end of chapter 09-conditionals)
// - easier to read && reason about code
// - easier to modify
// - easier to manage which conditions have priority
// - can more easily unit-test this function
function getShouldRenderGradesListView() {
  if (isLoading) return false;
  if (hasError || errMessage) return false;
  if (!getHasFeatureFlag('grade-management')) return false;
  if (!isOwner && !getHasPermission('view-all-grades')) return false;
  return true;
}

if (getShouldRenderGradesListView()) {
  renderGradesListView();
}
```

Ahhh, refactoring. Learn to love it.

Do future-you a favor. Rewrite your nested, complex logic until it's stupid-simple. You'll thank me later.

> Side note: it's an ongoing struggle to walk the tightrope of not refactoring enough, and over-engineering code for a feature that could wind up being thrown out entirely. A simple rule-of-thumb is to let yourself write messy code while prototyping, but clean it up after you find a pattern you want to commit to.

## Falsey Values

You'll hear the words "truthy" or "falsey" thrown around a lot as you start working in Javascript land.

Simply put, this just means some expressions will evaluate to `true`, and others to `false`. Expressions in programming are always deterministic, unlike Stephen Colbert's fuzzy definition of [Truthiness](https://www.cc.com/video/63ite2/the-colbert-report-the-word-truthiness)

Common values that evaluate to `false`:

```javascript
if (false) {
  console.log("this code will never run");
}

// the number zero
if (0) {
  console.log("this code will never run");
}

// an empty string
if ("") {
  console.log("this code will never run");
}

// a null value
if (null) {
  console.log("this code will never run");
}

// an undefined value
if (undefined) {
  console.log("this code will never run");
}
```

This may make more sense when we use variables inside of conditionals:

```javascript
// EDGE-CASE: change this to a negative value and see what happens
const numDollars = 0;
if (numDollars) {
  console.log("you got money in the bank!");
} else {
  console.log("you broke!");
}
```

The above example contains a seemingly innocuous bug. This is because bank balances can go negative, and negative values are NOT falsey. The bug fix would be as follows:

```diff
const numDollars = 0;
- if (numDollars) {
+ if (numDollars > 0) {
  console.log("you got money in the bank!");
} else {
  console.log("you broke!");
}
```

> Best practice: prefer explicit logic over falsey values when possible. It's worth the slight increase in code size to have better app stability. Always assume bad input is possible. Only utilize falsey conditional checks if you REALLY understand the implications forwards and backwards.

## Short Circuiting

The Javascript interpreter is pretty lazy. It wants to do the least amount of work possible.

Take this logic for example:

```javascript
const a = () => { console.log('a'); return false; }
const b = () => { console.log('b'); return true; }
// what will get printed?
if (a() && b()) { console.log('c'); return true; }
```

**Q**: Will `"b"` ever be printed to the console?

**A**: No! After evaluating `a()`, the result is `false`. Since `false && <any_value>` evaluates to `false`, we can safely ignore anything that follows the `&&` operator. And this is exactly what the interpreter does.

## ADVANCED - Optional Chaining

There are times an object's property may not yet be defined.

Consider this conundrum:

```javascript
// we have a person with an address
const personA = {
  address: {
    line1: '1134 Merrymont Ln',
    zip: 90210,
  },
}
// and looking up the address works just fine:
const street = personA.address.line1;

// but what if the person does not have their address filled in?
const personB = {
  address: undefined,
}

// This will result in `Uncaught TypeError: Cannot read properties of undefined (reading 'streetNumber')`:
const addressInfo1 = personB.address.line1;

// instead we must ensure `person.address` exists:
const addressInfo2 = personB.address && personB.address.line1;

// what's more, we can provide a sensible default if there is no address:
const addressInfo3 = personB.address && personB.address.line1 || 'Unknown';
```

But this is unwieldy. We can do better.

Enter **optional chaining** and **nullish coallescing**.

...Er, what?

Fancy words. Just means we can do more with less code:

```javascript
const person = {
  address: undefined,
}

const street = person.address?.line1 ?? 'Unknown';
```

The **optional chaining operator** (`?.`) only evaluates a nested value if the property is not `null` or `undefined`.

The **nullish coallescing operator** (`??`) only evaluates the right-hand operand if the left-hand operand is `null` or `undefined`.

Okaaaaaay who's confused? :raised_hand: I think this is easier explained by examples.

See if you can guess what the values will be in this example:

```javascript
const a = 0 ?? 1;

const b = 0 || 3;

const c = false ?? true;

const d = null || true;

const e = '' ?? 'Atta boy, Clarence!';

const f =  "" || 'Hot dog!';

console.table({ a, b, c, d, e, f }); // run this code to see the values
```

Were you surprised by any of the values?

I find it helpful to think of it this way:

- `||` applies for any **falsey** value
- `??` only applies for `null` and `undefined`

## Takeaways

Logic is a core part of programming. And it will seem daunting at first. But you will get the hang of conditionals and logical operators quickly. And when in doubt (and skepticism is GOOD), just add unit tests to verify your assumptions!

Consider that the most experienced programmers are often the ones who are trying to _simplify_ logic, reduce code paths, and delete unused / unnecessary parts. Those who intentially obfuscate and write clever code are good for not much other than 

## Additional Resources

- [MDN docs - Logical AND (&&)](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Logical_AND)
- [MDN docs - Logical OR (||)](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Logical_OR)
- [MDN docs - complete list of JavaScript falsy values](https://developer.mozilla.org/en-US/docs/Glossary/Falsy)
- [MDN docs - Optional chaining (?.)](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Optional_chaining)
- [MDN docs - Nullish coalescing operator (??)](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Nullish_coalescing)
