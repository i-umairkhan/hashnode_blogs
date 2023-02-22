# useContext - React Hooks

## What is useContext?

`useContext` is a React hook that provides a way for functional components to consume data from a parent component without having to pass it down through each level of the component tree explicitly as props.

It is a central store where any child component can consume data from it and change it.

## Usage of useContext.

The context in React is a way to share data between components without having to pass it through props. It is often used for data needed by many application components, such as the user's authentication status or the current theme.

To use the `useContext` hook, you first need to create a context using the `createContext` method provided by React. This method returns an object with two properties: `Provider` and `Consumer`. The `Provider` component is used to wrap the parent component that will provide the context data, while the `Consumer` component is used to access the data from within child components.

Once you have created a context and wrapped your parent component with the `Provider`, you can then use the `useContext` hook within any child component that needs access to the context data. To use the `useContext` hook, you simply pass in the context object as an argument and it will return the current value of the context.

## Creating Context.

We will take an example of authentication where the login component can change the `AuthContext` and any other component can consume that `AuthContext`

```javascript
import { createContext } from "react";

const AuthContext = createContext();

export default AuthContext;
```

Here we created `AuthContext` using `createContext` and exported it.

## Creating Provider.

As we will need `AuthContext` in the whole app so we will wrap all children with the `AuthContext.Provider` so any child component can consume it.

```javascript
const app = () => {
    const [auth,setAuth] = useContext({});
    return (
        <AuthContext.provider value={{auth,setAuth}}>
            <Login/>
            <Home/>
        </AuthContext.provider>
    )
}
```

In order to store and change `auth` we must use `useState` hook because we can not directly change the state of our application and then that state is provided to `<AuthContext.provider value={{auth,setAuth}}>` . So now `Login` and `Home` both can consume `auth` and `setAuth` .

# Consuming form context.

We will use `useContext` hook in `Login` to set the value of `auth` in our `AuthContext` that will be used `Home` component.

We must provider `AuthContext` to `useContext` in order to consume from context.

```javascript
const Login = () => {
    const {setAuth} = useContext(AuthContext);
    // we can get authObject from our authentication provider and set using setAuth
    setAuth(authObject);
}
```

Now that we have set our `auth` in `Login` . We can use it in `Home`

```javascript
const Home = () => {
    const {auth} = useContext(AuthContext);
    return (
        <h1>
            {auth.name} is logged in.
        </h1>
    )
}
```

This is how we can use `useContext` in our applications to store and consume data in a centralized way without passing props.