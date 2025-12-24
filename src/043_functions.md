# Functions

Functions are an incredibly flexible construct in Javascript (and any programming language) that allow us to modularise our code. They serve the purpose or reducing repetition, creating clarity and effectively categorising logic.

There are a few ways to create a function in javascript. However, we will focus on the most intuitive version.

The pattern for a function follows:

```
function name_of_function(parameters) {

  return var_or_value;
}
```

`function` is a keyword that is reserved in javascript, after it has been specified, it will need a symbol associated with it which correlates to the name of the function.

## Parameters

As part of the function definition, you typically outline `parameters` that you want to use. A function can have 0 to many parameters, this is part of designing your functions.

Let's examine the following snippet below.

```js
function printingMessage(prefix, message) {
  console.log(prefix + ": " + message);
}
```

* `prefix` and `message` are paramters
* Both parameters are used within the function (similar to variables declared) but the role parameters play is to represent the data given to the function as arguments.

Looking at the callsite of the `printingMessage` function, we can see the arguments `"Admin"` and `"Restarting network"`.

```js
printingMessage("Admin", "Restarting network");
```

This function can be used in other sections of the code and with different arguments. Literals are not the only kind of data that can be inputted. The arguments can be the value assigned to a variable.

```js
let role = "Admin";
printingMessage(role, "Restarting network");
```

The above snippet shows the variable `role` used in place for an argument in the function call.

## Returning Data

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

Refer to the following link for further information [MDN function](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/function)


## Arrow Functions and Anonymous Functions

Functions within javascript and other programming languages can be assigned to variables. This will be covered in more detail in **Chapter 7, Callbacks** however it is valuable to at least see their construction and usage.

As part of a variable initialisation statement, we are able to construct an **anonymous** function that is then assigned to a variable.

```js
let hello = function(msg) {
  console.log("Hello! " + msg);
};

hello("Veronica");
```

Given the initial outline from this chapter, this can seem unintuitive as they somewhat go against readability and reuse. However, in certain contexts they can make more sense to be inlined as it is clear what function is being passed as an argument.

With acknowledgement that we can create **anonymous** functions, we are able to create what are called **arrow functions** which are a shorthand version of these.

Re-writing the snippet above, we can write the following.

```js
let hello = (msg) => console.log("Hello! " + msg);

hello("Veronica");
```

The above snippet is functionally equivalent to the previous one. It should be noted that arrow functions have an implicit **return** when **not** encapsulated in `{ }`.

```js
let lengthOfString = function(s) { return s.length; };

let len = lengthOfString("Trackwork"); // 9
```

By using an arrow function we can omit the `return` keyword here.

```js
let lengthOfString = (s) => s.length;

let len = lengthOfString("Trackwork"); // 9
```

Of course, as outlined, as soon as we want the arrow function to be multi-line, we need to use a `return` statement.


```js
let lengthOfString = (s) => {
  return s.length;
}

let len = lengthOfString("Trackwork"); // 9
```

In terms of advantages of using arrow functions over regular functions.

* Brevity, especially if the code is simple
* Usage with `const` and ensuring that the function cannot be redefined.
