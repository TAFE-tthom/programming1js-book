# Callbacks and Async

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

## Promises

A promise is a proxy object that represents a value that will eventually be available. It maintains the states: `Pending`, `Fulfilled` and `Rejected`. Promises are used in situations where the result may not be known or could fail.

Some scenarios such as:

  * Network requests where the endpoint may not be available
  * Reading from a hard disk but the file may not exist or you may not have permission to access it

Promises are used in callbacks and async operations.

If a `promise` is rejected, it will be able to throw an error that can be caught.


## Async and Await

`async` and `await` are keywords within javascript that are required to return a promise. In more modern javascript, `async` and `await` are typically used over callbacks or promise chaining however you will still see these techniques used.

### Async and Await Functions

To create an `async` function it is a matter of specifying `async` infront of the function declaration. When specifi

```js
async function readFile(path) {

  // Rest of the code base

  return "Some data";
}


const dataPromise = readFile("some_file.txt"); //Gets a promise here

// current, await statements cannot be used at top level
dataPromise
  .then((data) => console.log(data));

```


### How async functions work

These functions can be quite confusing as they can break our current understanding of execution. This is because the sequence of events are bnot how they may appear in code. What is revealed is how the javascript virtual machine **schedules execution**.

Let's reveal how it schedules works.

```js
async function calledFirst() {
  console.log("Started"); //2
  
  await new Promise(function(resolve, reject) { //3
    resolve(); //5
  });
  console.log("This is first"); // 6
}

calledFirst(); //1 

console.log("This is second"); // 4
```

The code snippet has annotations associated to what statements will be executed in order. So, lets break it down.

* Async function `calledFirst` is called
* The function has been entered and will execute `Started`
* It sees `await` and will yield the rest of the function to scheduler
* It continues executing after the `calledFirst` callsite, and hits `This is second`, this is because the rest of the code is already ready to execute, we haven't `resolved` the other part
* No other code is left, the remaining operation in the queue is in the `await` statement and finishes executing `calledFirst`

