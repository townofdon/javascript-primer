# Printing && Logging

## Your first app - Hola Mundo

Copy and paste the following code block into RunJS:

```
console.log("hola mundo");
```

Pros of `console.log`

- great way to debug your app starting out
- spy on the value of a variable
- print helper/debug text
- no setup required - works out of the box

Cons of `console.log`

- some things are difficult to log, like deep function call stacks
- logging can get very tedious
- easy to forget to clean up logs once you don't need them anymore
- more sophisticated debugging exists, like setting breakpoints and attaching debugger processes, but these require 
  additional setup and can be confusing

## Other console logging (Advanced)

`console.log` is almost all you will ever need. So you can move on without feeling any anxiety at all.

&nbsp;

But, for those who like to dive deeper, here are some additional ways to log stuff:

**`console.error`**

- prints an error
- in a browser console this will show up as red text
- however, in the terminal / command line, will show up as regular text

**`console.table`**

- way to print tabular data, like an array of objects

  e.g.

  ```
  // copy and paste the following into RunJS:
  console.table([
    { name: 'Peter', age: 42, favoriteColor: 'orange' },
    { name: 'Paul', age: 33, favoriteColor: 'blue' },
    { name: 'Mary', age: 19, favoriteColor: 'green' },
  ]);
  ```

- as you can see, text is formatted in a way that makes it easy to read.

There are a bunch of other ways you can log stuff speficially for the browser - [see MDN console documentation](https://developer.mozilla.org/en-US/docs/Web/API/Console).
