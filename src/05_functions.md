# Functions

Functions are an incredibly flexible construct in Javascript (and any programming language) that allow us to modularise our code. They serve the purpose or reducing repetition, creating clarity and effectively categorising logic.

There are a few ways to create a function in javascript. However, we will focus on the most intuitive version.

The pattern for a function follows:

```js
function name_of_function(parameters) {

  return var_or_value;
}
```

However, you will find that there are many different ways that you can construct functions.

`function` is a keyword that is reserved in javascript, after it has been specified, it will need a symbol associated with it which correlates to the name of the function.

As part of the function definition, you typically outline `parameters` that you want to use. A function can have 0 to many parameters, this is part of designing your functions.

Every function can `return` a value (from a variable, literal or result from an expression) or may only be used to do an action (like print to the screen). 

```js
function addTwo(x, y) {
  return x + y;
}
```

The above function is going to add the values stored in x and y together and then return them.

So, after defining a function, how can we use them? Using the example above, we can make a function call. This invokes the function to perform the statements enclosed inside them.

```js

let result1 = addTwo(2, 2); //4

let result2 = addTwo(4, 10); //14

let result3 = addTwo(result1, 50); //54

```

The above statements are different function calls of the same function `addTwo`.
