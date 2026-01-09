# Creating Modules and Organising Code

We should be well accusomted to `npm init` by now and using some of the basic `npm` commands. While we won't be really deviating too much outside of that we do need to understand how all these modules work.

## Creating a module

Let's start with a review of creating a node module.

1. Create a folder and initialise the package with `npm init`

2. Make sure the following inforation is outlined within `package.json` file.

  * name - Name of your package
  * main - Entry point of your package (refer to a javascript file)
  * version - Base is 1.0.0 however you can refer to another versioning system
  * license - You have specified an appropriate license
  * author - You are author of the module

  It is worth noting that `repository` should also be included in this well if you have a git repo already set up.

  Ideally you probably want to set up your module to use `es6` exports, specify `type` as `module.`

3. Make sure the file you want to be the main export is the one specified in `main`.


### Testing your module and scenario

We will go through a scenario of building a module. Our scenario is to include the following files into our codebase using.

**minmax.js**

```js

function findmin(array) {
  let f = null;
  for(let i = 0; i < array.length; i++) {
    if(f === null) {
      f = array[i];
    } else if(f > array[i]) {
      f = array[i];
    }

  }

  return f;
}

function findmax(array) {
  let f = null;
  for(let i = 0; i < array.length; i++) {
    if(f === null) {
      f = array[i];
    } else if(f < array[i]) {
      f = array[i];
    }

  }
  return f;
}
```


The above is a simple file with two functions that we want to export. The other is a generator of random numbers and will maintain the state of the iterator.

**randomiter.js**

```js

class RandomIntegerIter {
  toGen = 0;
  constructor(toGen) { this.toGen = toGen; }

  [Symbol.iterator]() { 
    const endpoint = this.toGen;
    let step = 0;
    return {
      next: () => {
        let res = {
            value: Math.floor(Math.random()* 100),
            done: step >= endpoint
        };
        step += 1;
        return res;
      }
    }
  } 
}   
  
```

When writing a library where we want to make classes or functions (or even variables) available. We need to use `export`.

For `minmax.js`, we would include `export function` in place of `function` or simple `export`. for `randomiter.js` we would have `export class` where there is normally just `class`.


```js
export function findmin(array) {
  let f = null;
  /** Rest Snipped */
}

export class RandomIntegerIter {
  toGen = 0;
  constructor(toGen) { this.toGen = toGen; }

  /** Rest Snipped */

}
```

However, this simply exports the function and classes from the file to be accessible by others. We now need to define an `index.js` file which will be our entrypoint (this is a bit of a convention but does not need to be strictly adhered to).

Within `index.js`, we want to re-export any function, class or variable.

```js
import { RandomIntegerIter } from './randomiter';
import { findmin, findmax } from './minmax';

export default {
  RandomIntegerIter,
  findmin, findmax
};
  
```

By using `export default` and exporting an object associated (`{ ... }`), we are able to indicate what we are re-exporting.
