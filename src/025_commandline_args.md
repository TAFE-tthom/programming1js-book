# Command Line Arguments

This is specifically a desktop application component. As you have observed command line arguments from **Chapter 1**, you are able to build programs that are able to use command line arguments as well.

When executing code with `node`, you can pass command line arguments after the `.js` file has been specified. To access it within your codebase, you will need to `import` the `node:process` module.

## Using Command Line Arguments

To retrieve command line arguments from your application, you will need to use the following code segment:

```js
import process from 'node:process';

let arg1 = process.argv[2];
let arg2 = process.argv[3];

console.log(arg1);
console.log(arg2)
```

When retrieving arguments from environment, nodejs reserves the first two positions for the location of the `node` program itself and the other for the `script` location. 🖊️

Example:

```
node some_day.js Monday Tuesday
```

Given the snippet to retrieve the first two arguments given, `arg1` will map to `Monday` and `arg2` will map to `Tuesday`.

Keep this in mind as well, the datatype that `arg1` and `arg2` are associated with is the `string` datatype. Note down some of the concepts that may be new here. We will be revisiting some concepts like Arrays and Import later in the book. 📒
