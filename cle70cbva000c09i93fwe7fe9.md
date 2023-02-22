# useEffect - React Hooks

## What is useEffect?

The `useEffect` hook is a built-in hook in React that allows you to handle side effects in functional components. Side effects are anything that affects the state of the application outside of the component, such as fetching data, modifying the DOM, or subscribing to events.

The `useEffect` hook takes two parameters: a callback function and an array of dependencies. The callback function is called after the component is rendered, and can be used to perform any side effects. The array of dependencies is optional and is used to control when the callback function is called.

## Data fetching using API example.

```javascript
import { useState, useEffect } from 'react';

function MyComponent() {
  const [data, setData] = useState([]);

  useEffect(() => {
    fetch('https://example.com/api/data')
      .then(response => response.json())
      .then(data => setData(data));
  }, []);

  return (
    <div>
      {data.map(item => <div key={item.id}>{item.name}</div>)}
    </div>
  );
}
```

In this example, the `useEffect` hook is used to fetch data from an API when the component is first rendered. The `useState` hook is used to store the data in the component's state. The empty array `[]` is passed as the second parameter to `useEffect`, which means that the callback function will only be called once when the component is first rendered.

## **Dependency Array.**

To make the Hook run on a particular state change, we can supply the variable as a dependency in the array.

```javascript
 useEffect(() => {
    console.log("Count variable has changed!")
 }, [count]);
```

In this example, the `useEffect` Hook will run on the first render and after every time the variable `count` has changed its value.

We can also specify multiple variables in array and when one of them changes `useEffect` will run again.

## Rendering Cycle.

When a component that uses the `useEffect` hook is rendered, the following steps occur:

1. The component is rendered for the first time.
    
2. React calls the function passed to the `useEffect` hook.
    
3. The callback function executes and can perform any side effects, such as fetching data or updating the DOM.
    
4. After the callback function completes, React updates the component to reflect any changes caused by the side effects.
    

The `useEffect` hook is also called during subsequent re-renders of the component, but only if the array of dependencies passed to `useEffect` changes between renders. If the dependencies are the same, React skips the `useEffect` call and goes directly to updating the component.

It's important to note that the `useEffect` hook can cause the component to re-render, which can result in an infinite loop if not used correctly. To prevent this, you should be careful to specify the correct dependencies in the array passed to `useEffect`, and ensure that the callback function doesn't cause unnecessary updates to the component's state.

`useEffect` runs after a prop, state or context changes. It runs after every render unless specified by the dependency array.

## Clean Up function.

We can return a function from useEffect which will run right before the component will unmount.

```javascript
useEffect(() => {
    console.log('This hook is running.');

    return () => {
        console.log('This hook is now unmounting.');
    };
});
```