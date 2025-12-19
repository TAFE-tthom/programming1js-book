# Operators and Expressions

We have observed some basic operators in use. The most common kind of operator you will encounter are **binary operators**. However, there are two other kinds of operators you will use.

* **Unary operator**
* **Ternery operator**

The logic behind each one is that they are referring to the number of elements they are operting on. For a **unary** operator, it is needing one variable.

A common unary operator is `!`, which is applied to get the opposite result of a boolean expression.

Example:

```js
let r = !true; //Will be false

let i = 10;

i++;
```

In the snippet above, you will observe the `++` unary operator that will increment the value by 1 (i being changed from 10 to 11).

**Binary** operators will use the element on the *left* and the element on the *right*. This is common as most operators we use will be of this form. However, depending on the data type, they take on different behaviours.

Example:

```js
let y = 10 + 20;

let z = y * 2;
```

The above snippet demonstrates `+` addition operator for numbers and `*` multiplication operator. Both work on the left and right operands.

The above 

**Ternary** operators will appear in a particular instance where they use the `?` and `:` symbols together.

Example:

```js
let mark = 61;

let result = mark >= 50 ? "Pass" : "Failed";
```

The above snippet will evaluate if `mark` is greater than or equal to `50` and assign the value `"Pass"` or `"Failed"`.

## Datatypes changing operator behaviour 📒

Depending if the variables are strings or numbers will change what kind of operation we will get and if it is even supported.

Using the code snipept below:

```js
let numberX = 10; // Number
let numberY = 20.5; // Number
let stringX = "Ten"; // String
let stringY = 'Twenty'; // String
let booleanX = true;
let booleanY = false; //boolean is only: true or false

//number + number = number
console.log(numberX + numberY);

//number + string = string
console.log(numberX + stringY);

//string + number = string
console.log(stringX + numberY);

//string + string = string
console.log(stringX + stringY);

//boolean + boolean = number?
console.log(booleanX + booleanY);

//boolean || boolean = boolean (logical or)
console.log(booleanX || booleanY);

//boolean && boolean = boolean (logical and)
console.log(booleanX && booleanY);

//!boolean = boolean (logical not)
console.log(!booleanX);
```

We can observe how `number + number` will result in a number, but will be addition.

But `number + string` or `string + number` or `string + string` will result in a `string` and will be string concatentation.

## Common Operators and Expressions 📒

The follow below in which you can use the reference from MDN (Mozilla Developer Network), you will get a breakdown of some common operators and expressions (and literals).

Use the following reference here: [MDN Expressions and Operators](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators)

* `+` - If the type associated is a `number`, it will perform addition, if it is a `string`, it will perform concatenation

* `-` - When type `number`, it will perform `subtraction`

* `/` - When type `number`, it will perform `division`

* `*` - When type `number`, it will perform `multiplication`

* `"..."` or `'...'` - `'` and `"` pairs are used to indicate start and end point of a `string` literal

* `true` and `false` - boolean literals, commonly used with if statements to allow your program to make decisions

* `<` - Less than symbol, example: `5 < 10` would return `true`
* `>` - Greater than symbol, example: `10 > 5` would return `true`
* `>=` - Greater than or equal to symbol
* `<=` - Less than or equal to symbol
* `==` and `===` - Equality symbol, checks to see if two objects are the same, additional equal is ensuring type equality

* `!=` and `!==` - Inequality symbol, checks to see if two objects are not the same.

## Printing and Interpreting data

Within javascript, we will want to print data to standard output and interpret strings into integers and floats. Javascript provides the capabilities with the following functions:

* `console.log` - Allows you to print to standard output (terminal screen), `console.log('Hello!')` as an example.

* `parseInt` - Will attempt to convert a `string` to an `int`, this will convert to the type `Number`.

* `parseFloat` - Will attempt to convert a `string` to a `float`, this will convert to the type `Number`.


Notice that there are two different ways to interpret the string and translate it to a number. Consider what the difference between an `int` and a `float`. 📒

**Note:** Write an experiment and use the following text: 🖊️ 💻

  * `"2"`
  * `"2.5"`
  * `"2.33"`
  * `"1.99"`
  * `"5.0"`

Consider what the behaviour is between the two and what **number sets** they relate to.

Please refer to the following documentation at [MDN Expressions and Operators](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators)


