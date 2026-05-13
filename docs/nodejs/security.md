# Node.js Security Best Practices

Guidelines for building secure backend applications with Node.js.

## 1. Dependency Management
- [ ] **npm audit**: Regularly check for vulnerabilities in your packages.
- [ ] **Snyk / Socket.dev**: Use automated tools to scan for supply chain attacks.
- [ ] **Minimize Dependencies**: Only install what you actually need.

## 2. Input Validation
- [ ] **Always Validate**: Never trust user input. Use libraries like `Zod`, `Joi`, or `Yup`.
- [ ] **Sanitize**: Clean data before using it in queries or rendering.

## 3. Avoid Command Injection
- [ ] **Never use `eval()`**.
- [ ] **Avoid `child_process.exec()`**: Use `child_process.spawn()` with arguments instead.

## 4. Error Handling
- [ ] **Centralized Catch**: Use a global error handler.
- [ ] **No Leaks**: Don't expose internal stack traces or database info to the client in production.

## 5. System Hardening
- [ ] **Non-root User**: Run the Node process as a limited user (e.g., `www-data` or `node`).
- [ ] **Environment Secrets**: Use `dotenv` or secret managers.
- [ ] **Memory Limits**: Monitor for memory leaks that could lead to DoS.

## 6. Security Tools
| Tool | Purpose |
| :--- | :--- |
| **npm audit** | Basic vulnerability check |
| **Snyk** | Comprehensive security scanning |
| **Helmet** | HTTP security headers (for web servers) |
| **Winston** | Secure logging (masking sensitive data) |

> [!IMPORTANT]
> Keep your Node.js version updated to the latest LTS to receive critical security patches.


## Code Examples

### `fetch` + timeout (Node 18+)
```javascript
const controller = new AbortController();
const timeout = setTimeout(() => controller.abort(), 5000);

try {
  const res = await fetch("https://example.com", { signal: controller.signal });
  console.log(await res.text());
} finally {
  clearTimeout(timeout);
}
```
### Read file as JSON
```javascript
import { readFile } from "node:fs/promises";

const data = JSON.parse(await readFile("config.json", "utf8"));
```
## Extra security notes (copy‑ready)

### Basic hardening (Express)
```bash
npm i helmet cors express-rate-limit
```
```javascript
import helmet from "helmet";
import rateLimit from "express-rate-limit";

app.set("trust proxy", 1);
app.use(helmet());
app.use(rateLimit({ windowMs: 60_000, max: 100 }));
```
### Validate inputs (example)
```bash
npm i zod
```
```javascript
import { z } from "zod";

const CreateUser = z.object({
  email: z.string().email(),
  name: z.string().min(1).max(100),
});

export function parseCreateUser(body) {
  return CreateUser.parse(body);
}
```
> [!TIP]
> Use the **Copy** button in the top-right of code blocks to quickly copy commands to your clipboard.
