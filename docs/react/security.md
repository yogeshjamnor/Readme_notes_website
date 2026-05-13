# React Security Best Practices

Securing the frontend in React applications.

## 1. Prevent XSS (Cross-Site Scripting)
- [ ] **Data Binding**: React automatically escapes values in `{ }` to prevent XSS.
- [ ] **dangerouslySetInnerHTML**: Avoid using this unless absolutely necessary. If used, sanitize the content with `DOMPurify`.
- [ ] **URLs**: Be careful with `javascript:` links or dynamic `src` attributes.

## 2. Authentication & Authorization
- [ ] **JWT Storage**: Prefer `HttpOnly` cookies over `localStorage` for sensitive tokens.
- [ ] **Route Protection**: Use Higher-Order Components (HOCs) or Protected Route patterns.
- [ ] **Client-Side vs Server-Side**: Remember that client-side checks can be bypassed; always verify permissions on the server.

## 3. Environment Variables
- [ ] **Prefixing**: Only prefix variables with `VITE_` or `NEXT_PUBLIC_` if they *need* to be accessible in the browser.
- [ ] **Secrets**: Never store private API keys or database passwords in the frontend code.

## 4. Dependencies
- [ ] **Scan Regularly**: Use `npm audit`.
- [ ] **Trusted Packages**: Only use well-maintained libraries from reputable sources.

## 5. CSP (Content Security Policy)
- [ ] **Headers**: Configure CSP headers on the server to restrict where scripts and styles can be loaded from.

## 6. Helpful Tools
| Tool | Purpose |
| :--- | :--- |
| **DOMPurify** | Sanitize HTML for `dangerouslySetInnerHTML` |
| **eslint-plugin-react**| Catch common security mistakes in React |
| **Snyk** | Scan for vulnerable dependencies |

> [!WARNING]
> Frontend security is mostly about UX and preventing common browser-based attacks. The real security enforcement must happen on the backend.


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
## 7. Copy‑ready security patterns

### Sanitize HTML (only when you must render HTML)
```bash
npm i dompurify
```
```jsx
import DOMPurify from "dompurify";

export function SafeHtml({ html }) {
  const clean = DOMPurify.sanitize(html, { USE_PROFILES: { html: true } });
  return <div dangerouslySetInnerHTML={{ __html: clean }} />;
}
```
### Safe external links (avoid reverse‑tabnabbing)
```jsx
export function ExternalLink({ href, children }) {
  return (
    <a href={href} target="_blank" rel="noreferrer noopener">
      {children}
    </a>
  );
}
```
### Avoid leaking secrets in the browser
```js
// ✅ ok to expose
console.log(import.meta.env.VITE_PUBLIC_API_BASE);

// ❌ never expose real secrets
// console.log(import.meta.env.VITE_STRIPE_SECRET_KEY)
```
## 8. Libraries to know

- `dompurify`: sanitize untrusted HTML
- `zod` / `yup`: validate inputs before sending to backend
- `eslint-plugin-security` (general JS): catch risky patterns


> [!TIP]
> Use the **Copy** button in the top-right of code blocks to quickly copy commands to your clipboard.
