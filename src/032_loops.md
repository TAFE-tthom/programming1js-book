# Loops

Two primary loop constructs are `while` and `for`. `while`'s layout is very similar to an if statement and simply needs a boolean expression.

```
while( boolean_expression ) {
  
}
```

However, what happens if the expression is true? Well, if it is its first time evaluating it, it will enter the loop scope `{ ... }` and execute code in between.

If it is, the second or third or ... nth iteration and the expression remains true, it will continue executing the statements within the scope.

Example:

```js
let x = 0;

while(x < 10) {
  console.log(x);
  x += 1;
}
```

The above snippet will print numbers 0 to 9. When `x` eventually reaches the value 10. It will exit the loop.

This leaves the `for` loop construct. This is where the construct has three parts but we will link it to how our previous `while` loop.

With a `for` loop, it follows the pattern:

```
for(initialisation; boolean_expression; updates) {
  
} 
```

To write a similar loop to the previous javascript snippet, we can write the following:

```js

for(let x = 0; x < 10; x += 1) {
  console.log(x);
}

```

We can now see that the initialisation which was once outside of the `while` loop is now in the `initialisation` position, the similarity of the boolean expression and the position of the update is different.

