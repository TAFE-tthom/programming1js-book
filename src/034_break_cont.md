# Break and Continue

Within loops, we may have situations where we want to exit the loop early or indicate that we want to go next iteration early.

There are some useful cases for `break` and `continue` as they can use `labels`. These mechanisms allow us to change the control flow on another level, although you may not see them in practice often as it can make the code very difficult to read.


## Break and Continue

We will examine some scenarios where `break` and `continue` are used.

### Break

`break` keyword allows for us to break out of a loop early. This means that the condition in which we entered the loop isn't necessarily the reason it has stopped.

Let's take loop of the following snippet of code. 

```js

let hasMessages = true;

while(hasMessages) {

  let message = getMessage();

  let hasMessages = checkForMessage();

  // Empty message, should finish early
  if(messages === "") {
    break;
  } else {
    console.log("You have received: " + message);
  }
  
}
```

The snippet calls a function `getMessage` to retrieve the latest message for itself, it is a simple string in which we compare if the message received is an empty string.

If so, it does not matter if `hasMessages` is `true` or `false`.

 
### Continue

`continue` allows the code to go to next iteration. For loop statements where a particualr branch shouldn't be computed, this can be a useful tool.

```js
let numberOfMessages = getMessageCount();

for(let i = 0; i < numberOfMessages; i++) {
  let message = getMessage();

  if(message === "IGNORE") {
    continue;
  } else {
    console.log("You have received: " + message);
  }
}  
```

The above snippet outlines a case where given a message that specifies `"IGNORE"`, the program will go to the next message. Contrary to what the previous snippet was doing where it broke out the loop.


### Using Labels

We'll expand on the scenario from **Continue** but swap our `continue` for `break` in this case. When using `labels` within javascript, we usually have a point that we want to jump to that a nested branch has outlined.

However, we should outline the behavioural difference between `break` without a label and a `break` with a label. 

The snippet below has a `break` without a label, the logic here is that if it receives a message that matches `IGNORE`. It will break out of the loop and go to the next inbox.

```js
for(let inbox = 0; inbox < inboxes; inbox++) {

  let numberOfMessages = getMessageCountFor(inbox);

  for(let i = 0; i < numberOfMessages; i++) {

    let message = getMessage();

    if(message === "IGNORE") {
      break;
    } else {
      console.log("You have received: " + message);
    }
  }

}
```

However, the following snippet is different.

```js
inboxloop: for(let inbox = 0; inbox < inboxes; inbox++) {

  let numberOfMessages = getMessageCountFor(inbox);

  for(let i = 0; i < numberOfMessages; i++) {

    let message = getMessage();

    if(message === "IGNORE") {
      break inboxloop;
    } else {
      console.log("You have received: " + message);
    }
  }

}
```

When a `"IGNORE"` is received, it will break the outer loop. Result in no other inboxes being checked.
