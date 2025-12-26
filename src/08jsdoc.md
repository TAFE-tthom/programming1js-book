# Documentation

Documentation with your code is incredibly important not only within a collaborative project but also for yourself. It is quite easy to forget what a certain function and how classes and variables relate to each other.


## Documentation using **JSDoc**

`jsdoc` is a tool and documentation standard for javascript and typescript. It is inspired by Java Documentation format and generation. You'll notice that there are two common elements within `jsdoc`.

* Documentation segments start with `/**` and end with `*/`
* Documentation properties start with `@`, for example `@class` and `@paramter`

Just to reiterate, you can two kinds of comment styles.

* `/*  */` - Block comment
* `//` - Inline comment

Some well known properties to be mindful of and keep in memory are.

* `@param {type} description` - Parameter type and variable for a method or function
* `@return {type} description` - Return type and value of a method or function
* `@exteds type` - Specify the type that the class extends from
* ``
* ``

The layout of a JSdoc object usually follows one of these two patterns. The first is used for methods and functions primarily.

```
/**
 * Description of the function or method
 * @param {type} brief description of paramter
 * @return {type} brief description of return 
 */
```

The second is used for exportable objects, modules and globals.

```
/** @module module description */
```
or

```
/** description of object or global */
```

Part of adhering to this format is that it is possible to easily construct documentation from the code and comments given using the `jsdoc` tool.

## Documentation Guidelines

Take the following segment as guidelines as these can be broken for the sake of clarity/better solution. However, these guidelines are to help with applying intuition with documentation and get into documenting.

The primary components to document within javascript are the following.

* Functions
* Classes
* Methods
* Modules
* Exported Variables and Globals




### Classes, Methods and Functions

Classes and what they extend from are usually simply named. We'll look at the following snippet and examine it. The following snippet will include methods, however the same style applies to functions.

```js
/**
 * Class representing Admin
 * @extends User
 */
class Admin extends User {


  /**
   * Returns the permissions for the admin
   * @return {Permissions} permissions object
   */
  getPermissions() {
    // ...   
  }

  /**
   * Deletes a post that the admin can delete
   * @param {Post} post - post object
   * @return {boolean} true if the post is deleted
   */
  deletePost(post) {
    // ...   
  }
}
```

We can see how it has been used to describe the methods and the class. This information can be extracted by the jsdoc tool, while the implementation is not provided, we get a lot of insight into what the methods are doing.



### Modules, Variables and Globals

Modules and variables are fairly straight forward. They typically require a brief description. The modules description is specified at the top of a file while documentation for variables is just above the variable declaration.


```js
/** @module user module */


/** Default permissions */
export const permissions = { read: true, createPost: true  }
```

You can look at the above snippet, it outlines how it is used in practice. Do note, unless it is very important to document it, it isn't usually a practice to document variables **inside functions or methods**.

## Using jsdoc

You are able to generate documentation and output files that would correspond with html. You are able to use this on an individual file like so.

```
jsdoc somefile.js
```

Or you can operate on a whole directory.

```
jsdoc -r src
```

Ideally, when you are using `jsdoc` with node, make sure to not include `node_modules` when generating the documentation.

**Note**, if you do not have `jsdoc` available to you as a command but you have used `npm install jsdoc`, you may want to try `npx jsdoc`.
