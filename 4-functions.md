# [Functions](https://www.youtube.com/watch?v=gigtS_5KOqo)
Key concepts and practical examples of JavaScript functions.

[Functions](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Functions) are the backbone of JavaScript development, but perhaps the most difficult concept to master.

## Anatomy of a function

A function is piece of code that can be _called_ during the lifecycle of the app to perform a task or return a value. A function declaration can be broken down into the following pieces.

1. Name.
2. Parameters. A list of inputs that can be passed into a function.
3. Body. The logic or statements that perform the computation.

A function declaration on its own does not do anything. You make use of functions by calling them. The return value of the functon can be assigned to a variable.

1. Function call. Executes the inside the function body.
2. Arguments. The values to be used as parameters in the function.
3. Return value. By default functions will return `undefined`, but can return the result of a computation when the body contains a `return`statement.

## Function Declarations vs Expressions

A function _declaration_ is a statement that describe what your code does. Declarations are [hoisted](https://fireship.io/courses/javascript/beginner-js-survival-guide/), which means they are loaded at the top of the scope before any other code runs.

```js
makeBread(2); // Call still works here

function makeBread(qty) {
  return '🍞'.repeat(qty);
}
```

An alternative approach is use a function as a value or _expression_ by assigning an anonymous function to a variable or parameter.

```js
const makeBeer = function(qty) {
  return '🍺'.repeat(qty);
}
```

While not common, it is possible to also assign a name to a function expression.

```js
const makeBeer = function beerFun(qty) {
  return '🍺'.repeat(qty);
}
```

## 🤔 Should you use declarations or expressions?

There is no universally accepted best-practice, but function expressions are commonly preferred for (1) their ability to be reassigned, (2) flexibility when composing higher order functions, and (3) the fact that they don't pollute the global scope.

## Parameters and Arguments

You have a variety of ways to structure parameters in a function. Below are examples of positional, named, and rest parameters:

```js
// Positional
function makeBreakfast(main, side, drink) {
  console.log(arguments);
  return `Breakfast is ${main}, ${side}, and ${drink}.`;
}

// Named
function makeLunch(opts) {
  const { main, side, drink } = opts;
  return `Lunch is ${main}, ${side}, and ${drink}.`;
}

// Rest params
function makeDinner(main, ...args) {
  console.log(main, args);
  return `Dinner includes ${main} and ${args.join('')}.`;
}

makeBreakfast('🥞', '🥓', '🥛');

makeLunch({ main: '🥙', side: '🍟', drink: '🥤' });

makeDinner('🍜', '🥘', '🍙', '🥠', '🍑');
```

## Arrow functions

Arrow functions provide syntactic sugar for writing compact code, while also omitting a new `this` object, which solves common pain points when writing object-oriented code. An arrow function is unique because it:

1. Does not have its own `this` object.
2. Implicit return value when brackets are omitted. i.e. `() => true` return true.
3. Always an expression, never a statement.

```js
const makeBeer = function beerFun(qty) {
  return '🍺'.repeat(qty);
}

const makeWine = (qty) => '🍷'.repeat(qty);
```

## Pure Functions

A _pure_ function is one that only relies only its inputs, produces no side effects, and does not modify values outside its local scope.

Notice how the impure function below mutates a global variable and uses it to calculate the return value. In other words, it depends on values outside of its own function parameters and/or body.

```js
let global = 0;
const impure = () => {
  global++;
  return global ** 2;
}

const pure = (x) => x ** 2;
```

## Higher Order Functions

A _higher order_ function is created by combining (or composing) multiple functions together by passing (1) functions as arguments or (2) returning functions. There are many built-in JS functions that use HOF, for example `setTimeout` and `Array.map`.

```js
// Anonymous
setTimeout(() => console.log('hello!'), 2000);

// Named
const log = () => console.log('hello');
setTimeout(log, 2000);

// Array Map
[1,2,3,4].map(v => v ** 2);
```

## Recursive Function

A recursive function is one that calls itself from inside its own function body. If a terminating condition is not provided it will create an infinite loop. Recursive functions are commonly used in algorithm implementations to efficiently to efficiently handle tasks like binary-tree traversal. Below is an example of a recursive function that traverses the file system using NodeJS.

```js
const fs = require('fs');
const { join } = require('path');

const traverse = (dir) => {
  const subfolders = fs.statSync(dir).isDirectory() && fs.readdirSync(dir);

  if (subfolders) {
    console.log('👟👟👟 Traversing ', dir);

    subfolders.forEach(path => {
      const fullPath = join(dir, path);

      traverse(fullPath);
    });
  }
}

traverse(process.cwd());
```




