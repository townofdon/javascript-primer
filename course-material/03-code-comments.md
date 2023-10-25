# Code Comments

As a programmer / developer / engineer, it's vital to communicate the intent of a program.

One school of thought says that code should be as self-documenting and intuitive as possible.
Unfortunately, writing self-documenting code is not always feasible, and furthermore the dev
may want to communicate additional intent / program scope.

This is where code comments come in. They are SUPER important, and I want to win you over to
my philosophy of not being lazy and adding comments where they are needed.

## **Single-line comments**

These are denoted by two forward-slash characters: `//`

```javascript
// this is a single line comment

// single-line comments can go above an expression (RECOMMENDED)
console.log("hola mundo");

console.log("aloha aloha"); // they can also go beside a statement (NOT GENERALLY RECOMMENDED)

// comments can be also used to temporarily "turn off" code
// select the following lines and press `CMD + /` (Mac) or `CTRL + /` (Windows/Linux)
// ---------------------------------------------------
// console.log("This code will not run if commented out!");
// console.log("Try for yourself in RunJS or the browser console.");
```

> A note on "turning off" code using comments: it's usually considered bad practice to leave commented code
in a codebase. Instead, use a version control system like `Git` so you can go back to your code at a previous
point in history. `Git` version control will be covered in a later chapter.

> Typing "//" manually can become tedious REAL fast. In RunJS, VS Code, Sublime, and many other text editors,
a quick shortcut to quickly comment out multiple lines of code is to do the following: 1) select multiple lines that you want to comment, and 2) press `CMD + /` (Mac) or `CTRL + /` (Windows/Linux) - give it a try now and see what happens!

## **Multi-line comments**

Multi-line comments are denoted by starting with `/*` and ending with `*/`. Anything in between will
be treated as a comment.

```javascript
/*
This is commented code. You can tell a story about your best friend Dave, or probably more likely,
walk another developer (or in all likelihood future-you) through design decisions behind a feature,
pretty much whatever you like. There are all manner of opinions about how and where comments should be used,
and I could wax poetic about my own opinions (indeed I already touched on my philosphy above), but I'll keep
this short and just say that comments should be added anywhere you want to describe how an algorithm works
or what a function does.
/*

/**
 * This is a JSDoc comment.
 * Yes, there is an entire standard out there for how Javascript code should be documented.
 * If you're curious, check it out!! JSDoc comments are freaking awesome, and will automatically
 * be parsed by VSCode Intellisense.
 */
function awesomeSausages() {
  console.log('these sausages are pretty dang awesome');
}
```


