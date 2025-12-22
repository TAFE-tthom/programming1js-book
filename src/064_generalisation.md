# Generalisations

The function signature forms part of the type information for the variable which allows a linter to confirm that an appropriate function with the same signature has been assigned.

Within Javascript, while this signature is not strictly enforced, it can be enforced by a linter which checks it against the documentation or by employing typescript that will identify the type signature.

The utility here is similar to inheritance and polymorphism, we are able to set up a function that will expect a particular function to be given to it as an argument.

## Scenario - Sorting Algorithms

Within sorting and searching, this is a fairly powerful system, however you have already seen this with `.map` and `.filter` already.

Let's use the following scenario where we have an implementation of selection sort that has been generalised.

```js
function getMinIndex(numbers, offset, callback) {
  let currentIndex = offset;
  let currentValue = numbers[offset];
  for(let i = offset+1; i < numbers.length; i++) {
    
    if(callback(numbers[i]!, currentValue!) < 0) {
      currentValue = numbers[i];
      currentIndex = i;
    }
  }
  return currentIndex;
}

function selectionSort(numbers, callback) {

  for(let i = 0; i < numbers.length; i++) {
    const minIndex = getMinIndex(numbers, i,callback);

    //swap
    const tmp = numbers[i];
    numbers[i] = numbers[minIndex]!;
    numbers[minIndex] = tmp!;
  }
}
```

Within the snippet above we can observe the `callback` being used `getMinIndex` and `selectionSort`. This is used as a `comparator`, as in, since the sorting algorith can be used on **any** type, we must know how to best compare it.


The following usage of `selectionSort` will outline how we can compare and use different data sets with the same function.

```js
function strCompare(a, b) {
  return a.localeCompare(b);
}

function reverseNumberCmp(x, y) {
  return y - x;
}

function normalNumberCmp(x, y) {
  return x - y;
}

let names = [ 'jeff', 'alice', 'bob', 'zelda' ]
let numbers = [1, 10, 7, 8, -9, 4, 2, 88];

selectionSort(numbers, reverseNumberCmp);

selectionSort(numbers, normalNumberCmp);

selectionSort(names, strCompare);
```

We can see three difference instances and used with two different datasets. The comparators `strCompare`, `reverseNumberCmp` and `normalNumberCmp` give us the implementation on how to identify the difference between two values of a particular type.
