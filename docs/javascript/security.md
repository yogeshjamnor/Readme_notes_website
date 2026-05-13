# JavaScript Security Best Practices

Core security concepts for JavaScript developers.

## 1. Avoid `eval()` and `new Function()`
Executing strings as code is one of the most common security vulnerabilities.
```javascript
// BAD
const userCode = "alert('Hacked!')";
eval(userCode);

// GOOD
const userCode = "alert('Hacked!')";
// Use safer alternatives like JSON.parse() or specific logic
```
## 2. Secure Data Storage
- [ ] **Don't store sensitive data in `localStorage` or `sessionStorage`**: They are accessible via any script running on the page (XSS).
- [ ] **Use `HttpOnly` Cookies**: For session tokens and sensitive identifiers.

## 3. Handle Untrusted Data
- [ ] **Escape User Input**: When rendering data to the DOM, use `textContent` instead of `innerHTML`.
- [ ] **Validate API Responses**: Don't assume the server always returns safe data.

## 4. Modern JS Security Features
- [ ] **Use `Strict Mode`**: Catches common coding errors and prevents some unsafe actions.
  ```javascript
  'use strict';
  ```
- [ ] **Object.freeze()**: Use to prevent modification of sensitive configuration objects.

## 5. Helpful APIs
| API | Purpose |
| :--- | :--- |
| **crypto.getRandomValues()** | Cryptographically strong random numbers |
| **URL.createObjectURL()** | Secure way to handle local files/blobs |
| **window.crypto.subtle** | Web Crypto API for encryption/hashing |

## 6. XSS Prevention Example
```javascript
// Unsafe
document.body.innerHTML = `<h1>Welcome ${userName}</h1>`;

// Safe
const heading = document.createElement('h1');
heading.textContent = `Welcome ${userName}`;
document.body.appendChild(heading);
```
> [!IMPORTANT]
> JavaScript runs in the user's browser, which means the user has full control over the environment. Never rely on client-side JavaScript for security enforcement.


## Code Examples

### Common patterns
```javascript
// Deep clone (modern runtimes)
const clone = structuredClone({ a: 1, b: [2, 3] });

// Create a random id (browser + node)
const id = crypto.randomUUID();
```
## Extra security notes (copy‑ready)

### Dependency scanning
- Keep dependencies updated
- Use the ecosystem scanner (`npm audit`, `pip-audit`, etc.)

### Secrets hygiene
- Do not commit `.env` / private keys
- Rotate leaked keys immediately


> [!TIP]
> Use the **Copy** button in the top-right of code blocks to quickly copy commands to your clipboard.
