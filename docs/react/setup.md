# React Project Setup

Setting up a robust React project with best practices for 2026.

## Recommended Folder Structure

```text
src/
├── assets/          # Static files (images, icons)
├── components/      # Reusable UI components
│   ├── ui/          # Generic UI components (buttons, inputs)
│   └── common/      # Feature-specific common components
├── hooks/           # Custom React hooks
├── layouts/         # Page layouts
├── pages/           # Page components (routed)
├── services/        # API calls and external services
├── store/           # State management (Zustand, Redux)
├── types/           # TypeScript interfaces/types
├── utils/           # Helper functions
├── App.tsx          # Main entry point
└── main.tsx         # Root mounting
```
## Environment Variables

Create a `.env` file in the root directory.

```env
VITE_API_URL=https://api.example.com
VITE_APP_NAME="My React App"
VITE_DEBUG_MODE=true
```
> [!IMPORTANT]
> Always prefix variables with `VITE_` when using Vite to expose them to the client.

## ESLint & Prettier Setup

Ensure your `.eslintrc.cjs` is updated for React 19+ and TypeScript.

```javascript
module.exports = {
  extends: [
    'eslint:recommended',
    'plugin:@typescript-eslint/recommended',
    'plugin:react-hooks/recommended',
  ],
  // ... configuration
}
```
## Best Practices

1.  **Functional Components**: Use arrow functions and hooks exclusively.
2.  **TypeScript**: Always use TypeScript for type safety.
3.  **Component Splitting**: Keep components small and focused (Single Responsibility Principle).
4.  **State Management**: Use Zustand for simple state or TanStack Query for server state.


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
