# Exercises

## Tasks

### 1. RollerCoaster Height Checl

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

### 2. Sum of 4

You will need to implement a function that will sum 4 numbers given as arguments. You will need to implement the function below in the `sum.js` file.

```js
function sumOfFour(a, b, c, d)
```

The `sumOfFour` function has 4 parameters (`a`, `b`, `c`, `d`), each parameter is assumed to be a number and as such, when called, will be supplied with a number.

The function `sumOfFour` must add all 4 numbers together and return the result.

Example Usage 1:

```js

let result = sumOfFour(1, 2, 3, 4);

console.log(result); //Outputs: 10

```

Example Usage 2:

```js

let result = sumOfFour(4, 5, 1, 10);

console.log(result); //Outputs: 20

```

Example Usage 3:

```js

let result = sumOfFour(8, 9, 22, 10);

console.log(result); //Outputs: 49

```

### 3. Searching Arrays


A common problem within programming is searching and it is best you get familiar with
implementing solutions to these problems. You have been tasked with implementing two
methods.

Implement the following function:

```js

function findWord(words, word) {

  return -1; //You should return the index
} 
```

The `findWord` function will search an array of strings (`words`) and check to see if `word` matches one of those. When the first instance of a match is found, the index of where that word is, should be returned.

If no match is found, `-1` should be returned.

```js

let allwords = ['Hello', 'Good', 'Today', 'Tomorrow', 'Time', 'Puzzle']

let loc1 = findWord(allwords, 'Good'); // 1

let loc2 = findWord(allwords, 'Time'); // 4

let loc3 = findWord(allwords, 'Jigsaw'); // -1

```

Comment and explain your implementation, consider using the `break` [keyword](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/break) to help exit a loop early.

Explain why `-1` is reasonable return value if we can't find the the word within the array.


### 4. Character Occurrence

You are tasked with writing a function that will accept a string as an argument and a character as an argument. Your function will count the number of times that character shows up in the string and return that value.


Example 1:

Checking the number of times 'l' shows up in 'Hello'

```js

occurence("Hello", "l"); //2
```


Example 2:

Checking the number of times 't' shows up in 'What is the time'

```js

occurence("What is the time", "t"); //3
```

Your solution should be case-insensitive (lower case 'l' will also map to 'L' and vice-versa).


## Tasks with Test Cases

Please refer to the following code repository for the exercises <https://github.com/TAFE-tthom/programming1-js>.

Attempt the following exercises in the **Week04** folder.

Ensure you run `npm install` and `npm run test` while your shell is in the directory of a particular question. Run `npm run test` to check to see if your solution works as specified.

