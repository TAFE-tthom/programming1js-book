# Source Files

With any programming language, we typically want to translate the keystrokes we input into our text editor that we will use to save the file that stores them.


This is no-different with Javascript.


Using the text editor of your choice, make sure you get familiar with the basics

* Opening a file
* Opening a folder
* Creating a new file
* Saving a file
* Writing and deleting text inside that file.

Prior to executing code, make sure you have saved your files so when the interpreter works with it, it has the latest updates.

## Okay! But what is a source file?

A source file is typically a text file that will contain **source code**. The kind of **source code** is going to be of the javascript variety. As per convention, when we save a javascript file, we should use the `.js` extension.

By using the appropriate extension, this will give a hint to the operating system about what app to open it with. Hopefully it should default to your text editor however you can adjust this setting for your own benefit.

## What do we do with source files? 📒

In our current context? We will write code and then execute it using `nodejs`. Later on, we will see how it will take on a different roles and purposes.

The tooling in the javascript ecosystem 

* Transform the code written into more optimised and minified code
* Create a superset of Javascript called Typescript
* Embed XML directly into Javascript for building web applications (`.jsx` files)
* Much more...

For our purpose and what is typically common regardless of what is mentioned above. We write code into a `.js` file and either reference it in a `HTML` document or execute it using the `node` command.


## Are source files the program? 📒

In the context of javascript, this is true. This is because it is an interpreted language and therefore the `node` virtual machine or the javascript virtual machine in the browser is not expecting a **compiled** file that does not resemble the source. 

In the context of **C#** and **Java**, these are languages that are compiled languages. The compiler assists with catching some issues that the programmer may have left in if they were not mindful at the time.

## Walkthrough 💻

Using your chosen text editor, make sure your can:

* Create a file and name it, make sure the file extension is `.js`.
* Write into the file and save it.

Refer to the example below and how it is laid out.

```js
let answer = 50;

if(answer >= 50) {
    console.log("You passed!");
} else {
    console.log("Oh no, something went wrong");
}
```

The above is from a source file that is simply testing a variable (`answer`) and checking to see if it is greater than `50` and outputting `You passed!` or going down the other path.

If we were to take this snippet and save it to `example.js`, we can run this example using the `node` command.

To execute code using `node`, you can do the following.

```
node example.js
You passed!
```

You will the notice the output from the program on the next line.


## Structuring Your Source File 📒

While it is implied from the snippet above, the execution of program starts at the **top** of the file and goes down. While it isn't always going to be as simple as that, it is a crucial bit of information to hold onto.

When structuring your program it is best to form some good habits and reserve some space for when certain things are to be appropriately placed and clustered.

We will look at the following snippet.

```js
import process from 'node:process'


// Formatting output and printing it
function outputFilePath(filepath) {
  let output = `The file that will be used is: ${filepath}`
  console.log(output);
}


let filepath = 'example.txt';

if(process.argv.length >= 2) {
  filepath = process.argv[2];
}

outputFilePath(filepath);

```

* Import statements, which are useful when using **nodejs** functionality and other libraries. Import statements are typically placed at the top of a file before any other code is read.

* Function definitions are placed next, any code that is not immediately being executed by the interpreter should be declared after the import statements but before variable declarations that will be used immediately. other constructs fit this as well, such as **Classes**.

* Variable declarations and initialisation (top-level) along with other statements, these come after function definitions. Top-level variables and statements are different to those made inside functions and classes.

