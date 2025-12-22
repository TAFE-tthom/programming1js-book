# Data Structure Details

Genrally, a data structure can be just a class or some aggregate of data. This usually relates to an (ADT) Abstract Data Type, where we can construct a type (class, type, interface) which are some kind of abstract on top of the primitives.

However, when we talk about data structures, we are usually referring to how we can efficienctly access, insert, update and/or allocate/position data.

*Why is it foundational?*

Everything you have been using, `Array`s in JS, `List` and `Dictionary` in C# are data structures. They are powerful types that allow us to build more complex things and not bog down the computation.

*What do I need to know this stuff?*

The quick answer is that, without building and understanding how these things work, you will be limited in what you can create and their efficiency.

*Where is it used?*

* Databases
    Tables with an index, usually has a Tree data structure supporting it.
    Tables are also just arrays but we need to be flexible with representation
    of the data in the columns

* Compilers
    So, C# and Typescript compilers can be efficient we want to index files for
    quickly access.
    
* Mobile Applications
    Doing searches on data in memory or on disk, making sure you only display what
    is in view... with desktop and mobile applications, anything can show up.



## Built-In Data Structures

There are two very common categories of collections we have seen and used but may not have formally leveraged.

* Sets
* Maps

### Sets


A Set is a collection of elements where each element is unique. This means that you do not have duplicate entries in the set. The following are the basic operations for sets:

* Intersection - Given two sets (A and B), an intersection of both sets would result in another set in which elements in A are also in B.

* Union - Given two sets (A and B), the union of two sets will result in all elements of A and B in a signle set.

* Difference - Given two sets (A and B), the difference (A \ B) is all elements in A that are also not in B. (This is not the same as symmetric difference).

* Symmetric Difference - Similar to difference but it is the union of the:
    A \ B and B \ A. For all elements in A that are not in B and for all elements in B that are not in A.

You have access to this type in javascript via the `Set` datatype.

### Maps

Similarly to sets, Maps have the same constraint where each key is considered unique. However, Maps are an association between a key and a value (conventionally, expressed as K and V).

The `Map` datatype in javascript is similar to an object that has much stricter properties and a clearer usage.

\newpage

You are able to use the `Map` like so:

```js

const addresses = new Map();

// uses the email address as the key
// Associates it with the person's full name
addresses.set('lauren@live.co.uk', 'Lauren Smith'); 
addresses.set('jeff@jeff.co', 'Jeff Fern'); 

//Using the email address, we can get the full name
const result = addresses.get('lauren@live.co.uk');
console.log(result);

```
