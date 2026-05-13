# React 19 Cheatsheet

Quick reference for common React patterns and hooks.

## Component Structure

```tsx
import React, { useState } from 'react';

interface Props {
  title: string;
}

export const MyComponent: React.FC<Props> = ({ title }) => {
  const [count, setCount] = useState(0);

  return (
    <div>
      <h1>{title}</h1>
      <button onClick={() => setCount(count + 1)}>
        Count: {count}
      </button>
    </div>
  );
};
```
## Essential Hooks

| Hook | Purpose |
| :--- | :--- |
| `useState(val)` | Manage local state |
| `useEffect(fn, deps)` | Handle side effects |
| `useContext(ctx)` | Consume context values |
| `useMemo(fn, deps)` | Memoize expensive calculations |
| `useCallback(fn, deps)` | Memoize function references |
| `useRef(val)` | Access DOM or persist values without re-render |

## Event Handling

```tsx
const handleClick = (event: React.MouseEvent<HTMLButtonElement>) => {
  console.log('Clicked!');
};

<button onClick={handleClick}>Click Me</button>
```
## Conditional Rendering

```tsx
{isLoggedIn ? <UserDashboard /> : <LoginForm />}
{isLoading && <LoadingSpinner />}
```
## List Rendering

```tsx
<ul>
  {items.map((item) => (
    <li key={item.id}>{item.name}</li>
  ))}
</ul>
```
## Code Examples

### `useMemo` for derived values
```jsx
import { useMemo } from "react";

function Total({ items }) {
  const total = useMemo(
    () => items.reduce((sum, item) => sum + item.price, 0),
    [items]
  );

  return <div>Total: {total}</div>;
}
```
> [!TIP]
> Use the **Copy** button in the top-right of code blocks to quickly copy commands to your clipboard.
