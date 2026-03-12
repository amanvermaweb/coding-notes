# ![ ](../assets/react_light.svg#only-light) ![ ](../assets/react_dark.svg#only-dark) useEffect Hook

The `useEffect` hook lets you perform **side effects** in functional components — like fetching data, setting up subscriptions, timers, or manually changing the DOM.

## 1. Basic Syntax

```jsx
useEffect(() => {
  // code to run after render
}, [dependencies]);
```

* Runs **after every render** by default
* The second argument (dependency array) controls **when** it runs

## 2. No Dependency Array

```jsx
useEffect(() => {
  console.log("Runs after every render");
});
```

* Executes after **every re-render**

## 3. Empty Dependency Array `[]`

```jsx
useEffect(() => {
  console.log("Runs after the initial mount");
}, []);
```

* Runs after the **initial mount** in production
* In development with **Strict Mode**, React may run the effect, clean it up, and run it again to help detect side effects

## 4. With Dependencies

```jsx
useEffect(() => {
  console.log("Runs when count changes");
}, [count]);
```

* Runs when `count` **changes**
* Add all **external state/props** used in the effect to the array

## 5. Cleanup Function

Return a function inside `useEffect` to handle **cleanup** (e.g., remove event listeners, clear intervals):

```jsx
useEffect(() => {
  const id = setInterval(() => {
    console.log("tick");
  }, 1000);

  return () => {
    clearInterval(id); // cleanup on unmount or re-run
  };
}, []);
```

## 6. Fetching Data Example

```jsx
import { useState, useEffect } from "react";

function Users() {
  const [users, setUsers] = useState([]);

  useEffect(() => {
    fetch("https://api.example.com/users")
      .then(res => res.json())
      .then(data => setUsers(data));
  }, []);

  return (
    <ul>
      {users.map(user => <li key={user.id}>{user.name}</li>)}
    </ul>
  );
}
```

## 7. Multiple Effects

You can use `useEffect` multiple times per component for separation of concerns.

```jsx
useEffect(() => {
  // first effect
}, [a]);

useEffect(() => {
  // second effect
}, [b]);
```

## 8. Infinite Loop Warning

**Don’t update state directly inside `useEffect`** without a condition or it will cause an infinite render loop.

```jsx
useEffect(() => {
  setCount(count + 1); // BAD: triggers render → runs again
});
```
