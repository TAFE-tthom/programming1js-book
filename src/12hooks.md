# Hooks and Update Handling

Within `React` we have a few hooks we will utilise. A common hook is `useState` or in the case of class components, state and props are typically type-arguments for `React.Component`.

As an alternative, as this may seem a little more logical.

```tsx
class Message extends React.Component {

    render() {
        const msg = this.props.msg;

        return (
            <p>{msg>}</p>
        )
    }
}
```

## `useState` and render updates

A primary way to trigger a re-render of a component is to trigger a state change. This is typically combined with event handling.

To create a simple counting component, we will need to have:

* HTML Button
* State which is the number of times a user has clicked a button
* Event that can be triggered by the button and update the state

Lets go through a simple counter component. This will re-render on each click and update the state of the component.

```jsx
function Counter(props): ReactElement {

    const [counter, setCounter] = useState(0);
    const output = `${prefix}: ${counter}`;

    const mouseEvent = (e) => {
        const newValue = counter + 1;
        setCounter(newValue);        
    }
    return (<button onClick={mouseEvent}>
            {output}
            </button>)
}
    
```

## `useEffect` and updating components

When loading or handling data from an API, the time it takes to return is unknown, it is a case where we have to handle a situation when a state change is required but may be triggered after rendering or during rendering.

To do this, we have to set up a call back and also specify dependency object. 

Let's take a look at the following component and how it works.

```jsx
function NewsLetter() {
    const [newsItems, setNewsItems] = useState([]);
    useEffect(() => {
        // function that calls `fetch(...)`
        requestNewsItems().then(items => {
            setNewsItems(items); //Will trigger state change
        })
        return () => { } //Clean up function when completed
        // Consider this if multiple requests occur you only want to
        // take the first one.
        
    }, []) // Array for dependencies
    // Make sure any `reactive` dependency is listed here
    const renderedItems = newsItems.map((e) => <NewsItem news={e} />)
    return (<div>{renderedItems}</div>
}
```


## `useRef` - After rednering

`useRef` is used to construct a reference to a value that is likely to not require re-rendering. This places the object outside the context of react but can be interacted with react.

Some good examples for using this feature is to ensure that DOM elements are not reconstructed, this is useful for canvas, video and audio elements where the playback or rendering is handled by those elements themselves.

Within a component, we are able to hook into a component/element with ref and utilise mutate the properties without it needing to trigger a re-render for the data to be updated.

```jsx
function ButtonCounter() {
  let divRef = useRef(null);

  function handleClick() {
    const divInnerText = divRef.current.innerText;
    const num = Number(divInnerText);
    divRef.current.innerText = `${num + 1}`;
  }

  return (
    <>
      <div ref={divRef}>0</div> 
      <button onClick={handleClick}>
        Increment!
      </button>
    </>
  );
}
```

For elements like `canvas`, `iframe` or for transitions where the rendering is best left to be managed by the browser rather than by react, this is where it is ideal.


## `useContext` and wrapping components

`useContext` is used as part of a container object and is used with a context external from the application itself. The use-case here is when creating a context, it will be used by 

```jsx
import { createContext, useContext } from 'react';

const ThemeContext = createContext(null);

export default function MyApp() {
  return (
    <ThemeContext value="dark">
      <Form />
    </ThemeContext>
  )
}
```

Inside the component, they refer to the context via the name of it, given the above example where components are contained within `ThemeContext`, inside `From` you will have:

```
const theme = useContext(ThemeContext); 
```

This grabs the context using the name as the key.
