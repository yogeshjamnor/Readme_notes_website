# Debugging Express.js

Techniques for troubleshooting Express applications.

## Using the `debug` Module

Express uses the `debug` module. Enable it via environment variable.

```bash
# Debug all Express activity
DEBUG=express:* npm start

# Debug only router activity
DEBUG=express:router npm start
```
## Logging Middleware

Use `morgan` for HTTP request logging.

```javascript
import morgan from 'morgan';
app.use(morgan('dev')); // 'combined' for production
```
## Common Errors

### 1. `Cannot set headers after they are sent`
- **Cause**: Trying to send a response (e.g., `res.json()`) multiple times in a single request.
- **Fix**: Use `return` before `res.json()` or ensure logic branches are mutually exclusive.

### 2. `Route not found (404)`
- **Cause**: Incorrect path, method, or middleware order.
- **Fix**: Check `app.use()` and route definitions order.

## Tools

- **Postman / Insomnia**: Test API endpoints manually.
- **Jest + Supertest**: Automated API testing.
- **Sentry**: Capture production errors.


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
> [!TIP]
> Use the **Copy** button in the top-right of code blocks to quickly copy commands to your clipboard.
