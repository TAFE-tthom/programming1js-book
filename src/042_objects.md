# Objects

Objects are a very broad concept in both javascript and other programming languages. It is common to refer values assigned to variables as objects as it is a generalisation. Specifically, objects usually refer to another aggregate type which is specifically composed of fields, properties and methods.

## Initialising Objects

Within javascript, an anonymous object can be constructed with curly braces `{` and `}`. This can seem confused with **scope** but given what is defined prior to the curly braces, the parser can identify the object initialisation braces.

To construct an empty object, you can do the following.

```js
let obj = { };
```

While, not encourage or common, you can update `obj` with new fields. However this is 
typically discouraged as it does not make it obvious what fields an object has outside of its initialisation.

## Fields

Fields are associated with the object and usually referred using `.`. To initialise a object you can specify the field names.

```js
let person = {
  name: "Jeffrey",
  age: 34
};
```

The above snippet initialises an object with the fields `name` and `age`. Accessing these fields, such as `name`, we are able to use `.name` or explicitly `person.name` to get the value associated with that field.

```js
let person = {
  name: "Jeffrey",
  age: 34
};

console.log(person.name);
  
```

It is equivalent and more accurately represented as part of the `JSON` specification, that you can use `"name": "Jeffrey"` as part of initialisation. Similar to an array, an object is able to aggregate multiple pieces of data. However, instead relying or memorising indexes, programmers can rely on the field name.


## Reference Types, Indirection and Aliasing

It has been discussed that both **Arrays** and **Objects** are reference types. As outlined in **Index Calcuation**, Arrays are assigned to a memory address, Objects are also assigned to a similar value or modelled as such.

> **Author's note**: It is reasonable to assume that how objects and classes are modelled are offset calculations from a base address. However, in reality, objects are implemented similarly to HashMaps.

A powerful feature with objects is that we can nest objects inside objects.

### Indirection

Let's look at a simple form of indirection using objects.

```js
let x = { msg: 'Hello' };
let a = {
  msg: x,
  empty: []
};
```

Our challenge here is to retrieve the string `'Hello'` without explicitly using the variable `x`, this means we want to use `a` and fields associated with `a ` to do this.

We are able to refer to the field inside `x` via `a.msg.msg`. This is because what we assigned to `a.msg` is the object that `x` is assigned to and this grants us access to that field.

### Nesting and more indirection

This now leads into a more complex topic, **Indirection with nesting**, we are now going to be using objects as a way to nest and group data but we can also group it up quiite a bit where it has layers!

Let's examine this onion!

```js
let onion = {
  layer: 1,
  next: {
    layer: 2,
    next: {
      layer: 3,
      next: {
        layer: 4
        
      }
    }
  }  
} 
```

The above snipper demonstrates how we can nest objects inside other objects, we do not necessarily need to have separate variables for each layer or an array but we can actively place another object inside one.

So, a question here is how dow e get the layers from the `onion` variable?

Remember, `onion` has the fields `layer` and `next`. The `layer` field is simply allowing us to know what layer we are at. To get layer 2, we will need to do:

```js
onion.next
```

The above is getting layer 2 in which we can retrive the value using `.layer`.

To get layer 3, we simply just use `.next` again as we can see they follow the same pattern. This is an effective use of nesting.


### Aliasing

Aliasing is an interesting concept where we can have 2 or more **references** to the same object (or allocation).

Let's look at the following:

```js
let a = [1, 2, 3, 4, 5];

let b = a;

b[2] = 100;

console.log(a[2]);
console.log(b[2]); //What's the print out here?
```

Specificaly we are leaning into some particular ideas when using **reference** types where if we were to do a similar operation but on a `number` or `boolean`, this will not be observable.

In short, there is a difference between **Reference** types and **Value** types, anything that is a reference like a `object` or `array` will copy the address while value types like `number` or `boolean` will copy the value.

The outcome from the snippet above is one where we observe the output for both was `100`. This is because both `a` and `b` are mapped to the same allocation (or memory address).
