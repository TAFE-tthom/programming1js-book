# Datatypes

In majority of programming languages, the language gives us the capabilities to categorise data. This is no different in Javascript. Javascript supports the primitive datatypes that are usually used to help build abstract data types.

Javascript **primitive** datatypes are 📒:

* `Number` - This encapsulates both integers and floating point numbers such as 1 (integer), 2 (integer) and 4.5 (float).
* `Boolean` - Represents true or false

There are others like `bigint`, `null`, `undefined` and `symbol`. However, we will visit those in later chapters.

The other kind of datatypes are **reference** datatypes 📒.

These will include the following types:

* `Array` - An array holds many objects, it is a contiguous block of data which can hold other kinds of data.
* `Object` - An object is composed of fields and/or methods. These are used to compose data together and group them together.

One of the datatypes that falls into both categories is the `String` datatype. While `String` is a reference datatype, its semantics are similar to that of a primitive datatype. 📒

A major distinction between the two categories is how assignment works between the two.

## Why do we have datatypes?

Each datatype have **operators** associated with it. These are operations that allow for the data to be used with another piece of data or expressed by itself.

For example, if we wanted to add two numbers together, we could write:

```js
let x = 10;
let y = 20;
let z = x + y;
```

The above snippet can be explained with the following:

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

## Categorising data and converting data 🖊️

When developing a program, you will need to know what data you will be using and how to process it. Consider what would be an appropriate data type for the following data.

* The name of a colour
* The number of participants in a survey
* Recording the grade as A, B, C, D, E, F
* If a subscription is active or not
* Representing tax from an income statement
* Recording the age of a person

Choosing a suitable datatype assists with the kind of operations we may want to perform with that data.

### Data conversion

Data can come in many different forms. Commonly, data is usually represented as text itself and then converted into something more appropriately like a number of boolean.

Conversion methods are associated with the following **types**

* Number
* String
* BigInt

It is common to observe conversion methods from text/string to its own relevant representation. Commonly, you will see `Number.parseInt` or `Number.parseFloat` as a method utilised to convert a `string` to a `number` datatype.

For `Boolean`, if the string represents the text as `true` or `false`, it is possible to perform a string comparison to resolve this.

Going from `Number` to `String` or some other type, each object would use a `toString`. However, each type usually has a want it can be converted into a string when used with a string.

Please refer to the [MDN's `Number` type documentation](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Number#static_methods);
