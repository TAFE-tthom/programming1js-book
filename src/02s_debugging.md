# Supplementary - Debugging 💻

To visualise how a program executes, using `node` and the `inspect` flag to create a **breakpoint** and step through it.

Let use the following code snippet under the name `broken.js` to demonstrate this and with the scenario that we were expecting `30` to be printed but we got `1020` instead.

```js
let ten = "10";
let twenty = 20;

let result = ten + twenty;

console.log(result);
```

Within our terminal, we able to run `node inspect broken.js`. It will report the following output.

```
< Debugger listening on ws://127.0.0.1:9229/0e1daaa1-9728-495c-bb02-00ac999c57a6
< For help, see: https://nodejs.org/en/docs/inspector
< 
connecting to 127.0.0.1:9229 ... ok
< Debugger attached.
< 
Break on start in broken.js:1
> 1 let ten = "10";
  2 let twenty = 20;
  3 
debug>
```

Do note, this may not match **exactly** but if it is similar and importantly, it has `Break on start` then it is fine. To get the command list up, you can run `help` and it will show the list of commands that you can use within this mode.

Start by using `s` and pressing **Enter**, you will notice the following change.

```
step in broken.js:2
  1 let ten = "10";
> 2 let twenty = 20;
  3 
  4 let result = ten + twenty;
```

The `>` is indicating what line of code it is about to execute. Previously it executed line 1 and now it will execute line 2.

If we get to line 6, while it hasn't printed any data, we can observe what the value of that variable is beforehand.

```
step in broken.js:6
  4 let result = ten + twenty;
  5 
> 6 console.log(result);
  7 
  8 
```

Use the following bit `exec console.log(result)` and press **ENTER**. This will demonstrate that we can execute small pieces of javascript code while in the debugging mode to extract information from it.

```
debug> exec console.log(result)
< 1020
< 
debug>
```

Before it is printed out, we can observe the `result` variable is currently assigned to `"1020"`.

To simple let the program continue, you can use the `cont` command or `c` for its shorthand.

Now, it is easy to get stuck in the debugger when you are not familiar with commands running for too long. Please use `CTRL+D` in this instance to close the `stdin` buffer. This means the program will no longer be listening for input from the user.

```
debug> c
< 1020
< 
< Waiting for the debugger to disconnect...
< 
debug> (CTRL+D)
[user@hostname ~] 
```

In cases where the program isn't listening from input from the user, `CTRL+C` also works to interrupt the program.
