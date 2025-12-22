# Exercises

Practice the following tasks, these will utilise different aspects of callbacks, IO and async.

## Tasks

### 1. Job List

A crafty way you can use `callbacks` is by maintaining a collection of them. Your task is to implement a class called `JobQueue` that will allow you to `addJob` and `getNextJob` them after you have added them.

`addJob(taskFn)` - This will add a function to the end of an array of functions inside the object.

`getNextJob()` - This will return next function inside the `JobQueue` and remove it from the list. If the list is empty, it will return `null`.

Example:

```js
function doHomework() {
  return "I am doing homework";
}

function playGames() {
  return "I am playing games"
}

function gotoSleep() {
  return "I am sleeping. Zzzz...";
}


let jobq = new JobQueue();

jobq.addJob(doHomework);
jobq.addJob(playGames);
jobq.addJob(gotoSleep);

let fn = jobq.getNextJob();
let result = fn(); // Will return 'I am doing homework'

fn = jobq.getNextJob();
result = fn(); // Will return 'I am playing games'
  
fn = jobq.getNextJob();
result = fn(); // Will return 'I am sleeping. Zzzz...'
```


### 2. Searching on Criteria

Your goal is to generalise a component of `searching`. You are to construct a function that would normally search an array and identify an element inside it, usually by a numeric or string value.

However, we are going to go one step closer to being able to support a search for any kind of object using `callbacks`.

Implement the following function:

```js
function searchArray(array, obj, comparator);
```

The function `searchArray` has 3 parameters, each parameter plays a significant role in generalisng the searching.

`array` - This collection could contain any kind of object, the assumption though is that an array contains only a particular type of object (an array contains numbers, we aren't mixing strings and numbers inside an array).

`obj` - This is the object we are looking for. This can be any kind of object, as it can be a number, string, instance of a `Person` class, who know!

`comparator` - This is what makes our search powerful. `comparator` is a callback function with two parameters, `a` and `b`. This function is given to `searchArray` to know how to compare two objects. If the two objects are the same, the function should return `true`, if not `false`. When the comparator returns `true`, the found object should be returned, otherwise return `null`.

Example:
```js
let people = [
  { name: 'Jeff', age: 33 },
  { name: 'Alice', age: 26 },
  { name: 'Bob', age: 92 },
  { name: 'Alice', age: 45 },
  { name: 'Jake', age: 22 },
]

function comparePeople(a, b) {
  if(a.name === b.name && a.age === b.age) {
    return true;
  } else {
    return false;
  }
}
let toFind = { name: 'Alice', age: 45 }
let result = searchArray(people, toFind, comparePeople); //Returns 4th entry

```


### 3. Selection Sort

You are to implement `selectionSort`, this is a simple sorting function that will follow the function signature below:

```js
function selectionSort(array);
```

* Finding the Smallest value/index inside an array using `getMinIndex`.

* Iterating through the array once identifying the smallest value, swapping it with the current location that is being operated on.

You can use the following pseudo-code to help guide your implementation:

```
array = [...] 
i = 0
N = number of elements in array

while i is less than N; do

  j = i+1
  minIndex = i
  
  while j is less than N; do

    if array[j] is less than array[minIndex]; do
      minIndex = j

  // Swaps
  
  tmp = array[i]
  array[i] = array[minIndex]
  array[minIndex] = tmp

```

Expand this search to then support any kind of object to be sorted using a `comparator`. You will need to support an additional parameter.


## Tasks with Test Cases

Please refer to the following code repository for the exercises <https://github.com/TAFE-tthom/programming1-js>.

Attempt the following exercises in the **Week07** folder.

Ensure you run `npm install` and `npm run test` while your shell is in the directory of a particular question. Run `npm run test` to check to see if your solution works as specified.

