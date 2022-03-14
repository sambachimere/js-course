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