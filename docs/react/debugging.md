# Debugging React Applications

Tools and techniques for identifying and fixing bugs in React.

## Browser DevTools

1.  **React Developer Tools**: Chrome/Firefox extension for inspecting component tree, props, and state.
2.  **Network Tab**: Check API request payloads and response status codes.
3.  **Console**: Check for errors, warnings, and custom `console.log()` outputs.

## Common Errors and Fixes

### 1. `Objects are not valid as a React child`
- **Cause**: Trying to render a JS object directly in JSX.
- **Fix**: Access a specific property (e.g., `user.name`) or stringify it for debugging.

### 2. `Hook called outside of component body`
- **Cause**: Using `useState`, `useEffect`, etc., in a regular JS function or outside the component.
- **Fix**: Move the hook inside the functional component or create a custom hook.

### 3. `Too many re-renders`
- **Cause**: Setting state directly in the component body or an infinite loop in `useEffect`.
- **Fix**: Wrap state setters in `useEffect` or an event handler.

## Logging Strategies

```javascript
// Debugging props and state
useEffect(() => {
  console.log('State updated:', state);
}, [state]);
```
## Useful Shortcuts

- `F12`: Open DevTools.
- `Ctrl + P`: Search for files in DevTools.
- `Ctrl + Shift + F`: Search globally in source code.


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
