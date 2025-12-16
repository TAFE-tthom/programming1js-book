# Control Flow

We will look into a few different conditional and loop constructs here and the patterns that are associated with them. These include for now:

* `if...else`
* `while`
* `for`
* `{ }`

## Concepts

The take away from this chapter is that you should understand the following and where to appropriately apply it:

* if, else and else if
* while and for
* { } usage and scope rules
* Boolean logic being utilised for control flow.


Important concept is to identify how all these concepts use scope and how we express variable scope using `{ }`.

## Variable Lifetime and Scope

To denote how long a variable lives for, we are able to outline its existance based on where it was declared within two curly-braces. This is a common idea between most C-derivative languages.

To note: Javascript scoping rules are a little funny, however, variables declared with `let` and `const` make them behave like others.

Let's take a snippet of how scope works below.


```js

let x = 10;
console.log(x);
{
  let y = 20 + x;
  console.log(y);
  {

    let z = x + y;
    console.log(z);
  }

  let z = 100 + y;
  console.log(z)
}
```

We would observe the following:

* `x` is declared and assigned 10
* `y` is declared and assigned 20 + x
* `z` is declared and assigned x + y
* `z` is dropped after printing 40
* `z` is declared and assigned 100 + 30
* `z` and `y` are both dropped

`y` and `z` are declared in *inner scope*, which means that when they are dropped (they live between the time they are created and the closing curly brance `}`), they become inaccessible. A new declaration is effectively treating as a brand new variable just under the same name.

The idea of **lifetime** is applied when the variable starts existing and when it is dropped. That is its lifetime. This is different to the lifetime of data, particularly **reference types**.

**Next Up: If-Else**
