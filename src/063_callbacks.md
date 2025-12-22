# Callbacks

An important piece in javascript and most programming languages is the idea of a `callback` or `function pointer`. The idea with callbacks is that, like other bits of data that we can pass as arguments as part of function calls, we can also pass a function as an argument as part of a function call.

*Why would you do this?*

Primarily, we can usually identify an algorithm that is mostly agnostic to the data it is using with the exception to when it needs to do something with that data.

A great example is **sorting**, this is because sorting algorithms are typically focused on how to traverse a collection efficiently 

## Examples of a callback

Let's look at a realworld example where we would 

```js
function numberCompare(x, y) {
  return x - y;
}

let nums = [ 5, 2, 7, 8, 1 ];

nums.sort(numberCompare); // nums is now [1, 2, 5, 7, 8 ]
```

The above snippet outlines how we provided a callback outline the difference between two numbers. The `numberCompare` function is passed as an argument to be used to compare two numbers when sorting.

You'll also find that javascript exposes a functional api on some of its collections which allow you to use `.map`, `.filter`, `.forEach` and `.reduce`. These functions accept a callback to assist with the operation as we can see with `.map` below.

```js
//Assuming s is a string
function getLength(s) {
  return s.length;
}

let words = [ 'One', 'Zip', 'Flower' ]
let wordLengths = words.map(getLength); //[ 3, 3, 6 ];
  
```

The above would typically require us to utilise a loop while the `.map` call has the loop built into and will call the `getLength` function during it.


## Usage of callbacks

Callbacks can be utilised within a synchronous and asynchronous context.

In the previous example we saw a synchronous usage of a callback that passed an object and allow us to utilise it in a method without that method directly calling a method by its identifier.

Commonly, you will see **arrow-functions** used with callbacks as they can inlined easily. Let's re-write the previous example with an arrow function.

```js
let words = [ 'One', 'Zip', 'Flower' ]
let wordLengths = words.map((e) => e.length); //[ 3, 3, 6 ];
```

It has eliminated some **verbosity** although there is no significant difference between the two.
