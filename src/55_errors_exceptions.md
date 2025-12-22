# Errors and Exceptions

Errors are goiing to be a fact of life for any programmer. You have likely made a number of mistakes during this book and with the code you have produced. **This is normal**, no programmer will get it right the first try without having a large amount of experience behind them.

The kind of errors that are discussed in this section are going to be ones we can handle but may be outside of our program's control.

To categorise, we have the following errors.

* Syntax Errors - These are basic errors and ones which we need to fix as part of programming.

* Outside Our Program - This could be trying to access a file but the file does not exist. In the event of a case like this, we should have a way of handling this.

* Cause By Our Program - This is a mixture where we need to consider if we have created an issue that we may need to handle it or we could conclude that the program is not suitable. It is **very unlikely** you have produced an unsuitable program as of yet but something to at least consider.

Kinds of issues that can be caused by our program could be an attempt to `parseInt` or use `fetch` and that the string given to `parseInt` isn't suitable or the response we got from `fetch` was a 404 or invalid.


## Handling Errors

When **handling** was mentioned, it is meaning to `catch` the error. We can **wrap** a segment of code within a `try-catch` block where given a block of code that could error, we can catch it and process it.

Let's demonstrate what happens in the following segment of code.


```js
const invalidJsonData =' { "name": "Jerry", "age": 33 ';

let details = {};

try {
  details = JSON.parse(invalidJsonData);
  
} catch(error) {
  console.warn(error);
}
```

We have purposely design a situation that the `invalidJsonData` variable cannot be parsed and will `throw` an error. Without the `try-catch` block, the program would actually halt here.

