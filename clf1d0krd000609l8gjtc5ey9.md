---
title: "useMemo - React Hooks"
datePublished: Thu Mar 09 2023 17:05:09 GMT+0000 (Coordinated Universal Time)
cuid: clf1d0krd000609l8gjtc5ey9
slug: usememo-react-hooks
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1678381473024/a6a6214c-e724-4bae-8afd-ed833fe30622.png
tags: reactjs, reacthooks

---

## What is useMemo?

The `useMemo` hook is used to memoize the result of a function. In other words, it allows you to cache the result of a function and use it later on, without having to recompute it every time. This can be especially useful when you have expensive computations that you don't want to perform unnecessarily.

To use the `useMemo` hook, you need to pass it a function and an array of dependencies. The function is the one that performs the computation you want to memoize, and the array of dependencies tells React when to recompute the result.

## Example.

```javascript
import React, { useMemo } from 'react';

function MyComponent(props) {
  const { value } = props;

  const memoizedValue = useMemo(() => {
    console.log('Computing expensive value...');
    let result = 0;
    for (let i = 0; i < value; i++) {
      result += i;
    }
    return result;
  }, [value]);

  console.log('Rendering component...');

  return (
    <div>
      <p>Value: {value}</p>
      <p>Memoized value: {memoizedValue}</p>
    </div>
  );
}
```

In this example, we have a `MyComponent` that takes a `value` prop. We want to compute an expensive value based on that prop, but we don't want to recompute it every time the component renders.

So, we use the `useMemo` hook to memoize the value. The function we pass to `useMemo` performs the computation, and we pass `value` as a dependency to the hook. This means that the memoized value will be recomputed whenever `value` changes.

When we render the component, we log a message to the console to indicate that we're rendering. We also log a message from the memoized function to indicate that we're computing the value.

## useCallback v useMemo.

Both `useCallback` and `useMemo` hooks are used to optimize the performance of a React application by avoiding unnecessary re-renders. However, they serve different purposes and are used in different scenarios.

`useCallback` is used to memoize a function, while `useMemo` is used to memoize a value.

The `useCallback` hook returns a memoized callback function. It is useful when you need to pass a function to a child component as a prop, and you want to ensure that the function reference remains stable across renders. This can prevent unnecessary re-renders of child components that depend on the function.