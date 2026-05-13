# Debugging Next.js

Finding and fixing issues in Next.js applications.

## Browser Debugging (Client Side)

Use React DevTools and Chrome DevTools as usual for components with `'use client'`.

## Server Debugging (Server Side)

For Server Components and Server Actions:

```bash
# Debugging with VS Code
NODE_OPTIONS='--inspect' npm run dev
```

## Common Errors

### 1. `Hydration failed because the initial UI does not match...`
- **Cause**: Server-rendered HTML differs from the first client-side render (e.g., using `new Date()` or `window` directly).
- **Fix**: Move environment-specific logic into `useEffect` or use a `useEffect` to ensure client-side rendering only after mount.

### 2. `Invalid link: /...`
- **Cause**: Missing `href` or incorrect path in `<Link>`.
- **Fix**: Verify paths or use the `Link` component correctly.

### 3. `Server Action not found`
- **Cause**: Action not exported or missing `'use server'`.
- **Fix**: Ensure the action is in a separate file with `'use server'` at the top.

## Logging

- **Server-side**: Use `console.log` in Server Components to see output in the terminal.
- **Client-side**: Use `console.log` in Client Components to see output in the browser console.

## Performance Debugging

Use the `next-bundle-analyzer` to find large dependencies.
```bash
ANALYZE=true npm run build
```


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


> [!TIP]
> Use the **Copy** button in the top-right of code blocks to quickly copy commands to your clipboard.
