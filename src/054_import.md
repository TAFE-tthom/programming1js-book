# Modularising, Import and Export

## Organising Source Code

For a substantial portion of this, we have been constructing singular files. However you have likely observed that the projects and tasks are starting to get little more complex for a single file.

Especially when starting to bring files that of different languages and their own opinionated structure. These will be hard lessons to learn because it can be difficult to avoid and identify when you have structured your code poorly.


## Exporting Variables, Objects, Classes and Functions

To reference different javascript files within nodejs and browser based javascript, we can use `modules`. Specifically, ESM, which allow us to structure our code and allow code to be `import`ed and also outline when code can be used outside of the file/`export`ed.

Let's assume we have the following function.

```js
function GenerateNumbers(start, end) {
  // ...
}
```

Where it has been defined, it is typically scoped to that file unless bound to global/window scope. However if we want to utilise that function outside of the file, we have to use `export`.

This can be done by doing the following:

```js
export function GenerateNumbers(start, end) { 
```

This will allow the function to be usable outside of the file when typically applied in strict mode. An important take away is that this is when the code is treated as a module though.


## Importing Modules

When using this function in another file, we are required to import it. We can do this by importing the file within our JS codebase.

```js
import { GenerateNumbers } from '/numbergen.js';
```

The above snippets outlines how we are able to import the function from `numbergen.js`, assuming it has been defined in that file and exported.



### Some Good Practices

Good practices will only do so much but they are best to keep in mind about as you are developing software. It is also important to not let structuring your code into something aesthetically pleasing to get in the way of solving a problem but you might find issues when the code structure has reached a form of complexity which is hard to maintain.

Some best practices to try to avoid, especially when your codebase is starting to exceed 500 lines:

* No magic numbers - Don't use arbitrary indexes on arrays or values that are not intuitive to someone who isn't familiar with the code base.

* No magic string literals - String literals which are used as part of a composition or used in multiple locations are normally candidates for formatting issues, considerring string interpolation and declaring format strings.

* Reduce Repeating code - When the same code-segment exists in more than one place rather than being its own module, it can leave the codebase prone to N+1 bug issues (where N is the number of times the segment has been repeated).

* Keep your functions and method short - When the code segment is beyond 30-50 lines (evaluate on a case-by-case basis), it may be worth investing some time to eliminate repetition or modularise components of it.

* Keep your variable declarations near the top of a function - declaring variables midway through a segment or function usually indicates that the function is doing more than 1 thing. This isn't always the case but when a block is normally showing many variables being declared mid-way, it may be time to break it off into another function.

* No import cycles - When using functions or classes from another file, this should be a one-way relationship. This is to eliminate file-pairs from being broken apart. If you find yourself in this situation, you may want to evaluate if both files are actually better being one.

* The file structure should be tree like - This can be difficult to get right but when structuring your project, your files should be modelled by category and levels. We'll take the following as an example:

```
                      battleships_game.js
                               |
           --------------------------------------------
          |                          |                 |
        ./objects                 ./logic            ./ui
          |                           |                |
     ----------------+ ..           ------             ------------------
    |           |   destroyer.js   |      |           |         |        |
   boat.js    submarine.js       state.js strat.js   menu.js  setup.js game.js
```


The above snippet has group up objects which are going to be in the game, logic that is used to maintain the state of the game and provide different strategies for a computer player and ui which is used as part of the interactions and displaying the game.

It makes it clear from each level where we may want to go next. In this case, it is likely the `./logic` and `./ui` folders will use the `./objects` files but the `./objects` files will not use components from the others.

