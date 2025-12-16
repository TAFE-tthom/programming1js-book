# Node

What is `NodeJS`? We have so far been just exploring the *filesystem* through a *shell*. We are going to be learning another tool which is going to be a sigificant focus of this book.

If you have installed everything correctly as outlined earlier, you will have a command called `node` available in your shell.

The `node` command, is what `NodeJS` is. This command/program allows you to run `javascript` programs that you will write soon. Let's first get a bit of an understanding of `node` though.

## Concepts

* `node` command and javascript source code
* What a *Virtual Machine* is
* Compiled and Interpreted programs

## Javascript Programs and Node

When writing javascript programs, we will create a `.js` file. For example, if you wanted to create a simple program that outputs `Hello Javascript` as written in javascript, you would do the following.

```js
console.log("Hello Javascript");
```

The above snippet of code will print `Hello Javascript` when it is executed. Now to execute this, we need to use the `node` command and like other commands, the argument we provide is the filename.

Assume we saved the code snippet inside `hello.js`, we can do the following:

```
[user@hostname Projects]$ node hello.js
Hello Javascript
```

What has occured is:

* We ran the `node` command
* It received the `hello.js` text and found the file
* It read the file
* It started **interpreting** and **executing** the code from that file
* It finished because there was no more code to execute

Importantly, the *interpreting* part is indicating is actually indicating that we have a machine inside our machine. This is called a *Virtual Machine*. This is because `node` is a program designed to interpret and execute javascript code.

There are many different types of virtual machines out there, you may have encountered them when playing old video games, using a remote computer and running Java or C# code (like Minecraft).

In the spirit of things, it is usually ideal to consider `javasript` as an **interpreted* language, while programming languages like Java and C# are *interpreted* but they are also *compiled*.

What compilation means is that we are taking the source code and outputting machine code, normally something that is not pleasant for humans to read or write by hand.


