# vitest - Testing Framework for javascript

While javascript has a large number of testing frameworks. `vitest` is a fairly universal and easy to use framework. It takes a lot of the ideas from `jest` and modernises them while also making it easier to be compatible with typescript.

While it typically is included within `vite` itself, it can be used standalone. Once installed using `npm`, you can modify `package.json` and update the `test` field within `scripts` to invoke `vitest`.

## Setting up Tests

To set up test cases, the convention employed by `vitest` and other testing frameworks is to include `.test` between the filename and the file extension. This will usually mimic the source file name.

Given the filename `instructions.js`, the test file would be named `instructions.test.js`. `vitest` will be able to identify these files within the project's directory.

We'll get the output from an example project.

```
[user@hostname ./project/vm] ls
instructions.js instructions.test.js main.js node_modules package.json
```

It is also appropriate for source code for test files to be stored in a `test` folder. However, some amount of configuration will need to be done **if the importing of the files is done without using relative pathing**.

## Writing test cases

To start writing test cases for your application, you will need to ensure you have the following things done.

* You have a `.test.js` file
* You have imported `expect` and `test` from `vitest`
* You have made the functions/classes/components you are testing available via `export` and have imported them into your project

Use the following snippet to 

```js
import { expect, test } from 'vitest';
import { Tutorial } from './tutorial.js'

/**
 * Checks if duration and capacity getters are working correctly
 */
test('Tutorial - Specify duration and capacity', function() {

  const tutorial = new Tutorial('TestTutorial');

  tutorial.setDuration(4);
  tutorial.setCapacity(20);

  expect(tutorial.getDuration()).toBe(4);
  expect(tutorial.getCapacity()).toBe(20);
  
})
  
```

Writing these test cases isn't too tricky but the pattern it utilises may seem unintuitive. Within the snippet above, the `test` function serve the fucntion of
  providing a test case description and how the test will be conducted.

The anonymous function given, initialises a tutorial and sets particular fields to ensure that the correct values are being set and retrieved correctly. This is done using `expect` which will accept the **actual** value being reported and check it agaisnt the `toBe(<expected value>)` segment.

> For anyone who is curious, the pattern utilised is a form of **builder** pattern.


## Code-Coverage

Once you have constructed your test cases, you can generate how much code your test cases are covering. This provides insight into the effectiveness of your test cases.

You will need to add an additional script to your packagejson that will allow you to trigger `vitest` with coverage. Under `scripts`, you can add `coverage` to run the command `vitest run --coverage`.

You can then run the coverage with `npm run coverage`. It will output the coverage results to the terminal. You will observe the columns, `% stmts`, `% branch`, `% functions`, `% Lines`, these outline the percentage of code that are executed during a test case.
