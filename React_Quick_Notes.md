# React Quick Notes

## 📘 Table of Contents
- [1. Components](#1-components)
- [2. Props and State](#2-props-and-state)
- [3. Events](#3-events)
- [4. Conditional Rendering](#4-conditional-rendering)
- [5. Lists and Keys](#5-lists-and-keys)
- [6. Hooks](#6-hooks)
- [7. useEffect Example](#7-useeffect-example)
- [8. Forms](#8-forms)
- [9. Fetching Data](#9-fetching-data)

---

## 1. Components
```jsx
function Welcome() {
  return <h1>Hello, React!</h1>;
}

export default Welcome;
```

## 2. Props and State
```jsx
import { useState } from "react";

function Counter({ start }) {
  const [count, setCount] = useState(start);
  return (
    <div>
      <p>Count: {count}</p>
      <button onClick={() => setCount(count + 1)}>+</button>
    </div>
  );
}
```

## 3. Events
```jsx
function Button() {
  const handleClick = () => alert("Clicked!");
  return <button onClick={handleClick}>Click me</button>;
}
```

## 4. Conditional Rendering
```jsx
function Greeting({ loggedIn }) {
  return loggedIn ? <h1>Welcome back!</h1> : <h1>Please log in</h1>;
}
```

## 5. Lists and Keys
```jsx
function UserList({ users }) {
  return (
    <ul>
      {users.map(user => (
        <li key={user.id}>{user.name}</li>
      ))}
    </ul>
  );
}
```

## 6. Hooks
- `useState` — store component state  
- `useEffect` — perform side effects  
- `useRef` — access DOM nodes or store mutable values  
- `useContext` — share data across components  
- `useMemo` / `useCallback` — optimize performance  

## 7. useEffect Example
```jsx
import { useState, useEffect } from "react";

function Timer() {
  const [seconds, setSeconds] = useState(0);

  useEffect(() => {
    const interval = setInterval(() => setSeconds(s => s + 1), 1000);
    return () => clearInterval(interval);
  }, []);

  return <p>Timer: {seconds}s</p>;
}
```

## 8. Forms
```jsx
function Form() {
  const [name, setName] = useState("");

  const handleSubmit = e => {
    e.preventDefault();
    alert(`Hello ${name}`);
  };

  return (
    <form onSubmit={handleSubmit}>
      <input value={name} onChange={e => setName(e.target.value)} />
      <button type="submit">Submit</button>
    </form>
  );
}
```

## 9. Fetching Data
```jsx
import { useEffect, useState } from "react";

function Users() {
  const [users, setUsers] = useState([]);

  useEffect(() => {
    fetch("https://jsonplaceholder.typicode.com/users")
      .then(res => res.json())
      .then(data => setUsers(data));
  }, []);

  return (
    <ul>
      {users.map(u => <li key={u.id}>{u.name}</li>)}
    </ul>
  );
}
```
