# Variables and Output

## Source Code

As part of structuring out application, we need to be able to write out code inside a **source file**. A common convention (and one which will you should adhere to) is to ensure your javascript source files end in `.js`.

Using a text editor of your choosen, make sure your can:

* Create a file and name it, make sure the file extension is `.js`.
* Write into the file and save it.

Let's take a peek at an example before moving on.

```js
let answer = 50;

if(answer > 50) {
    console.log("You passed!");
} else {
    console.log("Oh no, something went wrong");
}
```

The above is from a source file that is simply testing a variable (`answer`) abd checking to see if it is greater than `50` and outputting `You passed!` or going down the other path.

If we were to take this snippet and save it to `example.js`, we can run this example using the `node` command.


## Variables

To make our programs interesting, we need to record and hold data within our programs. To achieve this, we use **variables**. A **variable** is a symbol within our javascript program that we can read and write to.


We need to be mindful thought, we should name our **variables** sensibly and adhere to the **naming rules**.

### Variable assignment and rules

When creating a variable within javascript, we would commonly use the `let` or `const` keyword followed by the **name** of the symbol we want to make it.

Example:

```js
let message = 'Hello';
  
```

The above demonstrates:

* Usage of a **keyword** of `let`
* The nameof the variable **we** gave it is `message`
* We have assigned it to the **value** `'Hello'` using the `=` operator.

We are then able to refer to the variable in lines that follow afterwards.

