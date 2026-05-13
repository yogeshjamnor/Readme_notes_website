# React CLI Commands

Essential commands for developing, building, and maintaining React applications.

## Development Commands

| Tool | Run Command | Description |
| :--- | :--- | :--- |
| **npm** | `npm run dev` | Starts the development server |
| **yarn** | `yarn dev` | Starts the development server |
| **pnpm** | `pnpm dev` | Starts the development server |

## Build Commands

```bash
# Production build
npm run build

# Preview build locally
npm run preview
```
## Testing Commands

```bash
# Run unit tests (Vitest/Jest)
npm test

# Run tests with coverage
npm run test:coverage
```
## Linting and Formatting

```bash
# Run ESLint
npm run lint

# Fix linting errors
npm run lint:fix

# Format with Prettier
npx prettier --write .
```
## Dependency Management

```bash
# Install new package
npm install <package-name>

# Install dev dependency
npm install -D <package-name>

# Remove package
npm uninstall <package-name>

# Update dependencies
npm update
```
## Useful CLI Shortcuts

- `rs`: Restart Vite dev server (type in terminal while running).
- `h`: Show help in Vite terminal.
- `o`: Open in browser.
- `u`: Show server URL.


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
