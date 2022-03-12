# How to run JavaScript code
How and where to run JavaScript code

You have several options to run your first hello world programming: Open your editor and create a file name `ìndex.js`

```js
console.log('hello world')
```

## How to run JavaScript from the command line

Running a JS program from the command line is handled by [NodeJS](https://fireship.io/snippets/install-nodejs/)

In VS Code :
```bash
node .

// or

node index.js
```

## How to run JavaScript from the browser

You can run code in the browser by creating an HTML file that references the script. In our case, we used the `defer`option, which will execture the JS after the HTML file is finished loading

### Run a script from an HTML file

```html
<html>
    <head>
        <script defer scr="./index.js"></script>
    </head>
</html>
```

Open this HTML file on your local machine and open the developer console (next step) to see the output.

### Inspect the browser console

The console allows you to run code in the browser
Windows: `Ctrl+Shift+J`
Mac: `Ctrl+Option+J`
Manually from the settings menu: `More Tools -> Developer Tools`

## Run JavaScript with a framework

Frameworks like React, Angular, Svelte, etc will take care of the building & running of your app automatically and provide framework specific tooling and steps for running code

## Run JavaScript in a sandbox

* [StackBlitz](https://stackblitz.com/)
* [Replit](https://replit.com/)
* [CodeSandbox](https://codesandbox.io/)
* etc











