# Polymorphism and Mixins

The phrase polymorphism can be considered a little strange within javascript. However it can be considered a bit of an `ad-hoc` approach to polymorphism. Due to javascript being a dynamically typed language, it is possible to associate methods and functions on fields that are expected to exist.

In addition `Mixins` are also a method to compose a new class. 

## Polymorphism

Let's demonstrate polymorphism in use with both `subtyping` and updating a field that is going to be used.

```js
class Canine {
  bark() {
    console.log("Awoo!");
  }
}

class Dog extends Canine {
  bark() {
    console.log("Woof!");
  }
}

function makeNoise(d) {
  d.bark();
}

let dog = new Dog();

let wolf = new Canine();

let cat = {
  bark() {
    console.log("Meow");
  }
}

makeNoise(wolf);
makeNoise(dog);
makeNoise(cat);
```

The above snippet demonstrates how `makeNoise` can be used with three different types of objects. Since `makeNoise` depends on a method called `bark` being available, each object has an implementation and therefore comply with its requirements.


## Mixins

A major limitation of inheritance within javascript is that it can only inherit from 1 other type. This can be quite limiting, a way to address this shortcoming is to associate methods that exist with an established class.

```js
class User {

  constructor(username) {
    this.username = username;
  }

  isAdmin() {
    return false;
  }
}

const AdminPermissions = {
  isAdmin() {
    return true;  
  }
}

Object.assign(User.prototype, AdminPermissions);

let user = new User('alice_ice');
console.log(user.isAdmin()); //true
```

We are able to observe that the output was `true`, it has overriden the initially assigned method for the type. The idea of a mixin is that we can construct and add capabilities to a type afterwards.

### Wait... what are classes?

A `class` is usually described as **syntatic sugar** which is mostly true because the way a class would represented was a `function`, where the `constructor` was the function.


```js
function User(username) {
  this.username = username;
}

let user = new User("alice_ice");
```

When printing out the variable `user`, we will notice the following. The representation looks similar to those of classes.

```
User { username: 'alice_ice' }
```

This is a different construction of a class and one which is valid although can be quite confusing for anyone coming from another programming language. 
