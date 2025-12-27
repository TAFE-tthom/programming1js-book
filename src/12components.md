# Components and JSX

We will be exploring how components and specifically how JSX will work. JSX is a mixture of XML and Javascript within the same file. It allows representing UI components in a XML format while providing the ability for your javascript to directly interact with it.

## Components and Properties

Let's go through what is involved in a component by creating our own.

As a task, let's create a component which displays a message and colours it. By defining a function called Message and making it return `JSX`, this conforms to what React expects a component to be.

```tsx
function Message(props) {
    return (
        <div style={{color: textColor}}>
            {msg}
        </div>
    )
}
    
```


If we want to explicit, the function can return `ReactElement`.

There is a single parameter, however this can be expressed as an object and fields of that object can be used inside the component.

```tsx
function Message(props) {
    return (
        <p style={{color: textColor}}>
            {msg}
        </p>
    )
}
    
```

Using the `Message` component will require another component to have linked to it or be in the same file. Within `App.tsx`, we will reset the output to only contain:

```jsx
<div>
    <Message msg={"Hello World"} textColor={"#00FF00"}/>
</div> 
```

We can observe that the properties that are set in the component match the fields of the `Message` function.

```
    msg={"Hello World"}  textColor={"#00FF00"}
          |                   |
Message({msg,              textColor })    
```

When the react application is rendered, the components are transformed into the final state of the render (for that instance).

So, given:

```
<App />
    -> <div><Message msg={"Hello World"} textColor={'#00FF00'} /></div>
       -> <div><p style="color:'#00FF00'">Hello World</p></div>   

```


## Aggregates

To handle collections or aggregates, we can usually trigger rendering of multiple elements as mapped to components.

Using the `Message` component from before, if we have the following:

```js
const messages = ["Hello World", "It is a good day!", "See you later!"] 
```

We could create a list of components by constructing them and adding them into an array, or simply using `.map` method associated with collections.

```tsx
const renderedMessages = messages.map((e) => <Message msg={e} />)
```


## How Components Work - Meta Programming

A major area of programming is called **Meta Programming**, in effect, it is the idea of programs writing programs.

Within react and jsx, we have this idea of encoding functions as components inside a HTML like syntax.

* With this convenience, the `build system` has to leverage a `JSX` parser to interpret it to javascript.

As outlined previously, the JSX parser will go through the `.jsx` files first and convert the usage of the user defined components into function calls.

```
<div>
    <Message msg={"Hello World"} textColor={"#00FF00"}/>
</div>  
```

Will be converted to the following.

```
    msg={"Hello World"}  textColor={"#00FF00"}
          |                   |
Message({msg,              textColor })    
```

While you may be getting use to throwing your program into the interpreter, within this build system, your files will go through a number of other programs. One them is the JSX parser and this will occur before what you have written gets executed.
