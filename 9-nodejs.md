# [Node.js Quickstart](https://www.youtube.com/watch?v=ENrzD9HAZK4)
Learn the basics of Node.js in 7 easy steps

## STEP 1 - WHAT IS NODE?

Node is a runtime that allows you to run JavaScript on the server. Learn more in the [how JavaScript works](https://fireship.io/courses/javascript/intro-how-js-works/)

## STEP 2 - INSTALL NODE

Follow these instructions to [install NodeJS](https://fireship.io/snippets/install-nodejs/). This course uses Node version 12, `nvm install 12`.

## STEP 3 - HELLO WORLD

Create a JavaScript file.

```js
console.log('hello world');
```

Run it with `node`.

```console
node . # points to index.js

node index.js
```

## STEP 4 - BUILTINS & GLOBALS

Node has several global variables that you should know about:

  * `global` use it to save global throughout the app. Similar to `window` in the browser.
  * `process` interact with the current process to information like the OS platform or environment variables.

## STEP 5 - EVENTS & EMITTERS

In most cases, you will find yourself listening to events and handling them with callbacks, but you can create your own events with an `EventEmitter`.

```js
// Create
const { EventEmitter } = require('events');
const eventEmitter = new EventEmitter();

// Handle
eventEmitter.on('lunch', () => {

    console.log('yum 🍣');

});

// Emit
eventEmitter.emit('lunch');
eventEmitter.emit('lunch');

// yum 🍣
// yum 🍣
```

## STEP 6 - WORK WITH THE FILE SYSTEM

Many APIs in Node are callback based.

```js
const { readFile, readFileSync } = require('fs');

// Blocking!
const txt = readFileSync('./hello.txt', 'utf8');
console.log(txt)


// Non-blocking
readFile('./hello.txt', 'utf8', (err, txt) => {
    console.log(txt)
});

// Promise based, also non-blocking
const { readFile } = require('fs').promises;

const txt = await readFile('./hello.txt', 'utf8');
```

## STEP 7 - MODULES AND NPM

A [module](https://fireship.io/courses/javascript/concepts-modules/) is just a file that exports its code.

```js
module.exports = {
    hello: 'world'
}
```

Another file can use this code by importing it.

```js
const { hello } = require('./cool.js');

console.log(hello);
// world
```

Install remote modules by initializing an NPM project.

```console
npm init -y

npm install express
```

## BUILD A FULL STACK WEB APP

### USE EXPRESS TO CREATE AN HTTP ENDPOINT

Create an HTML file.

```html
<html>
<head>
    <title>Hi Mom!</title>
</head>

<body>
    <h1>This is my web app!</h1>
</body>
```

1. Use [express]() to build an HTTP endpoint
2. Read the HTML file
3. Send it back to the client

```js
const express = require('express');
const app = express();
const { readFile } = require('fs').promises;

app.get('/', async (request, response) => {
    response.send( await readFile('./home.html', 'utf8') );
});

app.listen(process.env.PORT || 3000, () => console.log(`App available on http://localhost:3000`))
```

### DEPLOY THE APP TO GOOGLE APP ENGINE

Create a Google Cloud account and install the [gcloud SDK](https://cloud.google.com/sdk).

Configure your server.

```yaml
runtime: nodejs12
```

Deploy it.

```console
gcloud app deploy
```