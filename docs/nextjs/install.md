# Installing Next.js

Guide to starting a new Next.js project in 2026.

## Using `create-next-app` (Recommended)

The standard way to initialize a Next.js project with all modern features (App Router, Tailwind, TypeScript).

```bash
npx create-next-app@latest
```

During setup, follow these recommended choices:
- **Project Name**: `my-app`
- **TypeScript**: Yes
- **ESLint**: Yes
- **Tailwind CSS**: Yes
- **src/ directory**: Yes
- **App Router**: Yes
- **Import Alias**: Yes (`@/*`)

## Manual Installation

```bash
npm install next react react-dom
```

## System Requirements

| Dependency | Version |
| :--- | :--- |
| Node.js | ^20.0.0 |
| npm / pnpm | Latest stable |

## Global Packages

No global packages are required for Next.js. Always use `npx` or local project scripts.

> [!TIP]
> Use `pnpm` with Next.js for faster installation and better disk space management.


## Code Examples

### Environment variables
```bash
# .env.local
NEXT_PUBLIC_API_BASE=https://api.example.com
```

```javascript
// Use NEXT_PUBLIC_* only in the browser.
console.log(process.env.NEXT_PUBLIC_API_BASE);
```
