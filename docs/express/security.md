# Express.js Security Checklist

Essential security measures for production Express applications.

## 1. Use Helmet (HTTP Headers)
[Helmet](https://helmetjs.github.io/) helps secure your app by setting various HTTP headers.
```bash
npm install helmet
```
```javascript
import helmet from 'helmet';
app.use(helmet());
```
## 2. Rate Limiting
Prevent brute-force and DoS attacks.
```bash
npm install express-rate-limit
```
```javascript
import { rateLimit } from 'express-rate-limit';

const limiter = rateLimit({
  windowMs: 15 * 60 * 1000, // 15 minutes
  limit: 100, // Limit each IP to 100 requests per windowMs
});

app.use(limiter);
```
## 3. Data Sanitization (XSS)
Sanitize user input to prevent Cross-Site Scripting.
```bash
npm install xss-clean
```
```javascript
import xss from 'xss-clean';
app.use(xss());
```
## 4. Prevent Parameter Pollution
```bash
npm install hpp
```
```javascript
import hpp from 'hpp';
app.use(hpp());
```
## 5. Additional Protections
- [ ] **CORS**: Enable it only for trusted origins using the `cors` package.
- [ ] **CSRF**: Use `csurf` or similar for form protection.
- [ ] **Secure Cookies**: Use `httpOnly`, `secure`, and `sameSite` flags.
- [ ] **Environment Variables**: Never hardcode secrets. Use `dotenv`.
- [ ] **Avoid `eval()`**: Never use `eval()` as it can execute malicious strings.
- [ ] **Dependencies**: Regularly run `npm audit` to check for vulnerabilities.

> [!CAUTION]
> Always set `NODE_ENV=production` to ensure Express doesn't leak stack traces to the client.


## Code Examples

### Centralized error handler
```javascript
app.use((err, req, res, next) => {
  const status = err.statusCode ?? 500;
  res.status(status).json({
    message: err.message ?? "Internal Server Error",
  });
});
```
### Async route wrapper
```javascript
export const wrap = (fn) => (req, res, next) =>
  Promise.resolve(fn(req, res, next)).catch(next);
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
