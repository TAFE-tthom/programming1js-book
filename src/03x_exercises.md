# Exercises

Please refer to the following code repository for the exercises <https://github.com/TAFE-tthom/programming1-js>.

Attempt the following exercises in the **Week03** folder.

Ensure you run `npm install` and `npm run test` while your shell is in the directory of a particular question. Run `npm run test` to check to see if your solution works as specified.

## Tasks

### 1. Even of Odd

You have been tasked with writing a program that can identify a value or even or odd. The input will be given as a command line argument.

Consider what operator you may want to use that could easily tell you if number is even or not.

Restrictions: You cannot use any `built-in` javascript functions, only operators and if statements. You are also being asked to avoid the `/` operator and `Math.*` functions.

Your program should not be more than 10 lines.

Example 1:

```
node even_or_odd.js 23
Odd
```

Example 2:

```
node even_or_odd.js 52
Even
```

Example 3:

```
node even_or_odd.js 101
Odd
```

### 2. Summation of an array

Lets assume you have been given an array of numbers that you will need to produce compute the total of.

You have been given the following array:

```
let nums = [10, 20, 30, 40, 50];
```

Using a `loop` construct, your task is to write a program that will calculate the total.

With the above example, the total should be `150`.

If you have a program that matches that, consider changing the values and see if it still calculate the total correctly.

Within mathematics, this operation can be expressed with the following notation:

$$\sum\limits_{i=0}^{n} nums_i$$

Where:

* `n` is the total number of elements. In this case, `nums.length`;
* `i` is the index

Save your file as `simple_sum.js` and provide comments to the different components of your program.

Do note: Your program should be able to scale with the number of elements in the array, if there is a hardcoded value in your loop condition or you aren't using a loop, your program probably doesn't scale.


### 3. Command Line Sum

Using what you have learned from last week and the previous exercise, you will now be extending your program to be able to calculate the total from command line inputs.

Create a file called `cmdsum.js` in which you will write your code. Your program will be used in the following manner:

```
node cmdsum.js 10 20 30 40 50
```

The above program should output `150`, similar to before, however you have two issues:

* The command line arguments are strings
* The arguments may not represent a number (what happens when `five` is inputted?)
* Accessing the first command line argument that isn't `node` or `cmdsum.js` is not at index 0.

Consider using the `isNaN` function to check if the argument is a number, if it isn't a number, you can safely ignore it from your total.

Refer to `isNaN` from [MDN isNaN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/isNaN).

Comment how you have adapted your code from the previous exercise and how you have checked for bad inputs.


### 4. Roller Coaster

This program requires you to implement a function called `checkHeight`. Firstly, construct a file called `rollercoaster.js`, afterwards define the following function:

```js
function checkHeight(height, threshold) {

  return 0;
}
```

You will need to implement `checkHeight` to do the following. Given that the function has two parameters `height` and `threshold`, your function is to check to see if the height matches or exceeds the threshold.

Consider the following usage, the heights are and threshold are assumed to be integers that correlate to centimetres:

```js

//Paul is 180cm, the threshold is 160
let doesPaulPass = checkHeight(180, 160); //true;

//Alice is 160cm, the threshold is 160
let doesAlicePass = checkHeight(160, 160); //true;

//Jeff is 150cm, the threshold is 160
let doesJeffPass = checkHeight(150, 160); //false;
  
```

Comment on the usage of the parameters and how you have tested your function implementation outside of the example given.

