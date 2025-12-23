# Classes Structure

Within Javascript, defining a class is also defining a type. This acts as template for objects that are instantiated as this type. Given that more than 1 object can be instantiated as this type, we are able to gaurantee certain behaivours and fields from that object.

It is easy to view a class as a **template** or **blueprint**. Objects instantiated as that type adhere to that blueprint. This is a very useful concept when structure your data within Javascript.


## Class Anatomy

A class can range from being a fairly complex description or simple, it depends on the scenario it is being used. Similar with objects and other constructs, we are able to compose a class with other classes, objects and types.

 


## Constructing our own

You have already interacted with classes before through `Array` and other builtins such as `Number` and `String`. What has not be shown is that part of instantiating an object from that type is done using the `new` keyword.

Let's look into the different components, while this isn't all the components, it is outlining the most critical ones.

```js
class ClassName {

  instanceField; //Field just not initialised

  initialisedField = "Hello!"; //Field but is initialised with a string value

  static staticField; //Field but for the class, not initialised
  
  static staticInitialisedField = "And again!"; //Field but for the class, initialised

  constructor() { } // Optional, when omitted, a constructor exist just with no params

  aMethod() { //Similar to a function but operations on the object
    //Can have a return statement or not
  }

  static aStaticMethod() { // Method that is associated with the class but not object
    //Similar to a function and method, can have a return statement
  }
  
}
```

Something to note is that `field` specifiers do not **need** to exist in class scope, they can be created and assigned during execution of the constructor.

### Field Initialisation

We will construct our own class and focus on the field variations that can be utilised. The following is an example a `Cupcake` class.

```js
class Cupcake {
  delicious = false;
  name = 'Chocolate Cupcake';
}

let cupcake1 = new Cupcake();

console.log(cupcake1.name);
console.log(cupcake1.delicious);
```

The above snipet defines a class with two instance fields, we then print out the values. Since the fields are assigned already, we get the output.

```
Chocolate Cupcake
true
```

However, it may seem quite redundant to have a whole concept that doesn't differentiate itself from objects that much. Lets consider how we could parameterise the fields themselves, we can do this through a **constructor**.

```js

class Cupcake {
  delicious;
  name;

  constructor(name, delicious) {
    this.name = name;
    this.delicious = delcious;
  }
}

let cupcake1 = new Cupcake("Chocolate Cupcake", true);

console.log(cupcake1.name);
console.log(cupcake1.delicious);
```

We have been able to observe that we can parameterise what the field will be, similar to a **function**. However, if wanted, we can consider the declarations of the fields **redundant**.


```js
class Cupcake {
  constructor(name, delicious) {
    this.name = name;
    this.delicious = delcious;
  }
}

let cupcake1 = new Cupcake("Chocolate Cupcake", true);

console.log(cupcake1.name);
console.log(cupcake1.delicious);
```

We have removed the fields specified at class scope, this is allowed because they are specified during the constructor. **However**, it is reasonable to have a **default** value and that having a field specified at the class level can make it a little more **readable**.

**What about this `this`** keyword?

The `this` keyword has a lot of utility within javascript and within the context above it is both addressing the ambiguity and also referring to the current reference.

> Note: As outlined in the previous chapter regarding **memory addresses**, you can consider `this` as the memory address of the current object executing the method.

We will be exploring the `this` keyword in more depth later on.

### Methods

Methods are closely related to a `function`, in fact we could rewrite methods as functions and vice-versa fairly easily. However, the novelty with a method is that we are associating a block of code with the data and type itself.

To examine a method, you will likely not see too much of a difference between a function and method.

```
// Assume inside class scope

  theMethod(parameter) {

    // optional return statement
  }
```

Let's say we want to have some function to serve the purpose of printing out the name the cupcake and if it is delicious or not. This is where **methods** can be effectively be utilised.

```js

class Cupcake {
  constructor(name, delicious) {
    this.name = name;
    this.delicious = delcious;
  }

  printDetails() {
    console.log(this.name);
    console.log(this.delicious);
  }
}

let cupcake1 = new Cupcake("Chocolate Cupcake", true);
cupcake1.printDetails();
```

We can observe that the output logic has been incorporated into the `Cupcake` class. We can refer to it by using `printDetails`.


