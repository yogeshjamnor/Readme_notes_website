# Installing React

Learn how to install React for various project types using modern tools in 2026.

## Using Vite (Recommended)

Vite is the standard for modern React development.

```bash
# Using npm
npm create vite@latest my-react-app -- --template react-ts

# Using yarn
yarn create vite my-react-app --template react-ts

# Using pnpm
pnpm create vite my-react-app --template react-ts
```
## Using Next.js (Fullstack)

For SEO and production-ready applications.

```bash
npx create-next-app@latest
```
## Installation Requirements

| Dependency | Version |
| :--- | :--- |
| Node.js | ^20.0.0 (LTS) |
| npm | ^10.0.0 |
| pnpm | ^9.0.0 |

## Global Packages

It is generally discouraged to install React-related CLI tools globally. Always use `npx` or local project dependencies.

> [!TIP]
> Use `npx` to run CLI tools without installing them globally to avoid version conflicts.

## Common Installation Issues

- **EACCES Error**: Use `nvm` to manage Node versions and avoid permission issues.
- **Peer Dependency Conflicts**: Use `--force` or `--legacy-peer-deps` sparingly; better to update conflicting packages.


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