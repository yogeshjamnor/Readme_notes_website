# Next.js Security Checklist

Best practices for securing Next.js App Router applications.

## 1. Server Actions Security
- [ ] **Authentication**: Always verify the user is logged in inside each Server Action.
- [ ] **Authorization**: Check if the user has permission to perform the specific action.
- [ ] **Input Validation**: Use `zod` to validate all `formData` or arguments.

## 2. Environment Variables
- [ ] **NEXT_PUBLIC_**: Only prefix variables with `NEXT_PUBLIC_` if they *must* be accessible on the client.
- [ ] **Secrets**: Keep sensitive keys (Stripe secret, DB URL) without the prefix to ensure they never leave the server.

## 3. Middleware Security
- [ ] **Route Protection**: Use `middleware.ts` for global authentication checks.
- [ ] **Headers**: Use middleware to set security headers (CSP, X-Frame-Options, etc.).

## 4. Data Fetching
- [ ] **Safe Rendering**: Use Server Components for sensitive data to avoid exposing it to the client bundle.
- [ ] **Tainted Data**: Use `experimental_taintUniqueValue` (if enabled/available) to prevent accidental leakage of sensitive keys.

## 5. XSS & CSRF
- [ ] **Link Components**: Use `<Link>` and `<Image>` which have built-in security features.
- [ ] **CSRF**: Server Actions have built-in CSRF protection, but ensure you follow standard practices for custom API routes (`app/api/`).

## 6. Helpful Tools
| Tool | Purpose |
| :--- | :--- |
| **Next-Safe-Action** | Type-safe and secure Server Actions |
| **Zod** | Runtime schema validation |
| **Iron-Session** | Secure, stateless session management |

> [!IMPORTANT]
> Because Server Components run only on the server, they are a powerful tool for security. Keep your data-heavy logic there to minimize the client-side attack surface.


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


## Extra security notes (copy‑ready)

### Set security headers (middleware example)
```javascript
export function middleware(req) {
  const res = new Response(null, { status: 200 });
  res.headers.set("X-Content-Type-Options", "nosniff");
  res.headers.set("Referrer-Policy", "strict-origin-when-cross-origin");
  return res;
}
```

### Cookies for auth tokens (server‑set, HttpOnly)
```javascript
// Pseudocode (server): set HttpOnly cookie for session/JWT
// Set-Cookie: session=...; HttpOnly; Secure; SameSite=Lax
```


> [!TIP]
> Use the **Copy** button in the top-right of code blocks to quickly copy commands to your clipboard.
