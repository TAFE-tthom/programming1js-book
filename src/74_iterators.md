# Iterators and Iterables

The thing to note here is that all these components relate to an interesting pattern called an `iterator`.

An iterator is object that allows reading through a collection. It maintains state within the collection and where to go next. A collection itself could be something where it generates or retrieves input on demand.

Generally, iterators have their place in any domain where a series or sequence can be an expression.

This can include:

* Database Cursors
* Line Retrieval from a file
* Data Streams
* Data Structure Traversals (Trees, Graphs, Grids...)
* ... everywhere

## What is the advantage here?

We get to maintain state during the iteration, linking back to our time-complexity of our `get(...)` call on a linkedlist, this can be **O(n)**. This will result in the following code being O(n^2).

```js
let list = new LinkedList();
// adds

for(let i = 0; i < list.size(); i++) {
    const e = list.get(i);
    // other things
}
    
```

Maintaining the state of the cursor means we aren't always restarting from the beginning and to find the **next** element.

The current iterators that have been outlined isn't the same as what Javascript expects but it at least breaks down the different components of it.

If we want our iterators, we need to leverage `Symbol.iterator` and implement a method that corresponds with this builtin.

```js
class RandomIntegerIter {
  toGen = 0;
  constructor(toGen) { this.toGen = toGen; }

  [Symbol.iterator]() { 
    const endpoint = this.toGen;
    let step = 0;
    return {
      next: () => {
        let res = {
            value: Math.floor(Math.random()* 100),
            done: step >= endpoint
        };
        step += 1;
        return res;
      }
    }
  } 
}   
```

Afterwards, we are able to construct a the above iterator and use it in a `for..of` loop.

```js
let count = 0;
let randiter = new RandomIntegerIter();

for(const i of randiter) {
  console.log(i);
  
  // using count for breaking out after 5 iterations
  if(count >= 5) {
    break;
  }
  count++;
}
  
```

We can then observe the following output from the snippet above.

```
14
49
48
23
66
```
