# Variables and Values

To make our programs interesting, we need to record and hold data within our programs. To achieve this, we use **variables**. A **variable** is a symbol within our javascript program that we can read and write to.

There are different keywords that can be used for declaring variables.

* Commonly `let` and `const` are used.
    * `let` allows the variable to be reassigned as well as read.
    * `const` does **not** allow for the variable to be re-assigned.  
* However, `var` typically shows up in legacy code and can still be used readily.
    * `var` allows the variable to be reassigned as well as read, however, it is discouraged since variables declared using `var` do not adhere to good **scope** rules while `let` and `cosnt` do.

For most demonstrations, we will be using `let` and `cosnt`.

## Variable naming 

We need to be mindful about how we name our variables. The name of a variable should be meaningful in the context of the problem it is trying to solve. By convention, Javascript leans in to `camelCase` variable naming. While you are not limited to other kinds of naming conventions, 

In addition to this convention, variables must start with a non-numeric character and not use any symbols that could be confused with an **operator**.

Consider the following scenarios and what variable name would be appropriate. 🖊️

* Number of soccer balls in a garage
* Players part of Red Team
* If a ligh is on or off
* Blood type
* Email message

You should name our **variables** sensibly and adhere to the **naming rules** that Javascript 

## Variable Values and Assignment 📒

When creating a variable within javascript, we would commonly use the `let` or `const` keyword followed by the **name** of the symbol we want to make it. To initialise the variable to a **value**, we use the `=` **operator** to assign it to the value on the right hand side.

Example:

```js
let message = 'Hello';
```

The above demonstrates:

* Usage of a **keyword** of `let`
* The name of the variable **we** gave it is `message`
* We have assigned it to the **value** `'Hello'` using the `=` operator.
* In reference with **operators**, a **binary** operator has two **operands**
    a **left** and **right** operand, with `=`, the variable name and `'Hello'`
    are the operands.

We are then able to refer to the variable in lines that follow afterwards.

