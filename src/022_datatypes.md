# Datatypes

In majority of programming languages, the language gives us the capabilities to categorise data. This is no different in Javascript. Javascript supports the primitive datatypes that are usually used to help build abstract data types.

Javascript primitive datatypes are:

* String - Expressed by inputting text between `''` and `""`
* Number - This encapsulates both integers and floating point numbers such as 1 (integer), 2 (integer) and 4.5 (float).
* Boolean - Represents true or false

There are others like `bigint`, `null`, `undefined` and `symbol`. However, we will visit those in later chapters.



## Why do we have datatypes?

Each datatype have **operators** associated with it. These are operations that allow for the data to be used with another piece of data or expressed by itself.

For example, if we wanted to add two numbers together, we could write:

```js
let x = 10;
let y = 20;

let z = x + y;
```

The above does:

* Sets x to the number 10
* Sets y to the number 20
* Adds x and y which will compute 30
* Sets z to the number 30 (result of the calculation)

While we focused on the adding of numbers, there are **4** operators being used here. We can observe **3** uses of the `=` operator which is used to assign a value to a *variable*.

The `+` operator is used to perform addition with what is on the left and right side of it.


## Assigning the correct data type to a variable

Let's use the following snippet to help here. When assigning data to the variable, let's remember the pattern of `let <variable name> = <value>`.

```js

// let is a reserved keyword that is part of javascript
// var and const can also be used

let numberX = 10; // Number
let numberY = 20.5; // Number
let stringX = "Ten"; // String
let stringY = 'Twenty'; // String
let booleanX = true;
let booleanY = false; //boolean is only: true or false
```

The above snippet shows the different variables being assigned to different datatypes but also the pattern that we can rely on.
