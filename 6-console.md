# [THE CONSOLE](https://www.youtube.com/watch?v=L8CDt1J3DAw)
Go beyond console.log() like and debug like a pro 

At this point in your JS career, you likely know what `console.log` does - but the [Console](https://developers.google.com/web/tools/chrome-devtools/console) API can do so much more! It can be an effective debugging tool, but it can also be a nightmare when abused. Let's take a look at some tricks that will keep your console output concise and beautiful. Open the console on your browser by running Ctrl + Shift + J to get started with this section.

First, inspect the methods on the console that go beyond `log`, by running:

```
console.log(console);
```

This article is focused on frontend browser JS, but the [Node Console API](https://nodejs.org/api/console.html) is almost identical.

## CONSOLE FAQ 

### HOW TO SHOW VARIABLE NAMES WHEN CONSOLE LOGGING?

It is easy for variable names to get jumbled-up when you have tons of output to the console. Wrap your variables in braces `{}` to make them an object, or brackets `[]` to make them an array, then use `console.table` to make them pretty.

```js
💩console.log(bar, foo);

// Wait, which variable is named foo? 

😐 console.log({ foo, bar });

// Better, but it's kinda hard to read...

😍console.table({ foo, bar });

// Noice!
```

### HOW TO GROUP CONSOLE LOGS?

You might not care about every line outputted into the console. Remove the clutter by grouping logs into a collapsible section with `group` or `groupCollapsed`.

```js
console.group();

console.log(1);
console.log(2);
console.log(3);

console.groupEnd();
```

### HOW TO CONDITIONALLY CONSOLE LOG?

Sometimes you want to log ONLY when a condition is falsey - this is known as an assertion. It will keep your code concise by eliminating the need for `if` statements.

```js
// verbose 💩
if (loggedIn) {
    console.error('user is logged in assertion failed');
}

// much better 😍 
console.assert(loggedIn, 'user is logged in');
```

### HOW TO INCREMENT A COUNTER IN THE CONSOLE?

Keep a counter running in your source code means managing mutable state - you probably don't want that extra complexity. Instead, use `count` to tell the browser to increment a counter for you.

```js
console.count();
console.count();
console.count();

console.countReset(); // reset to zero
```

### HOW TO SET A TIMER WITH THE CONSOLE?

You can start a timer with the console by calling `time`, then call `timeLog` to measure the elapsed time. It provides a simple solution for measuring performance.

```js
console.time();

// do stuff

console.timeLog('did stuff');


// do more stuff

console.timeLog('did more stuff');

console.timeEnd()
```

### HOW TO ADD CUSTOM CSS STYLES TO THE CONSOLE OUTPUT?

Use the special `%c` character to add some [custom CSS](https://stackoverflow.com/questions/7505623/colors-in-javascript-console) flavor to the console. This is a surefire way to impress other developers, especially if you maintain an open source library.

```js
console.log('%c YOUR_MESSAGE', 'YOUR_CSS')
```