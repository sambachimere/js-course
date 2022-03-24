# [MODULES](https://www.youtube.com/watch?v=qgRUr-YUk1Q)
Learn how to import and export JS code as a module or package.

A [module](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Modules) is just a fime that exports some JavaScrip code.

First, a file exports (package) something useful...

```js
export default '🧁';
```

Second, a different file uses this code by importing it.

```js
import cupcake from '../path/to/awesome-package.js';
```

Pretty simple! But there more you should know.

## DEFAULT EXPORTS

A module can specify at most 1 default export.

```js
export default '🧁';
```

This allows the consumer to name the module whatever it prefers when importing.

```js
// wait, that's not pizza...
import pizza from '../path/to/awesome-package';
```

This is the ideal for modules that export a single class or function.

## NAMED EXPORTS

Some modules might offer a collection of independent helper functions, like RxJS or Lodash. A better option for such packages is __name exports__

```js
export const cupcake = '🧁';
export const pizza = '🍕';
```

If the consumer only wants pizza, they can import it by name - this is called [treeshaking](https://webpack.js.org/guides/tree-shaking/) or dead code elimination.

```js
import { pizza } from '../path/to/awesome-package'; 
```

### HOW TO CHANGE THE NAME OF AN IMPORT?

If you don't like the exported name, you can change it with the `as` keyword.

```js
import { pizza as awesomePizza } from '../path/to/awesome-package'; 

console.log(awesomePizza);
```

### HOW TO EXPORT A LIST OF VARIABLES?

A module may have many variables to export and this can get messy. Use an export list to make your code more succint and organized.

```js
const cupcake = '🧁';
const pizza = '🍕';

export { 
    cupcake,
    pizza
}
```

## ADDITIONAL RESOURCES
> * Samantha Ming's [Module Cheatsheet](https://www.samanthaming.com/tidbits/79-module-cheatsheet/)