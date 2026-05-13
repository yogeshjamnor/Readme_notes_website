# Installing Express.js

Guide to adding Express.js to your Node.js project.

## Basic Installation

```bash
# Initialize project if not done
npm init -y

# Install Express
npm install express
```
## TypeScript Setup

```bash
npm install -D @types/express
```
## Generators (Optional)

Use the Express generator for a quick boilerplate (though manual setup is often preferred for modern apps).

```bash
npx express-generator --view=pug myapp
```
## Dependencies Table

| Package | Purpose |
| :--- | :--- |
| `express` | The core framework |
| `cors` | Enable Cross-Origin Resource Sharing |
| `dotenv` | Load environment variables |
| `helmet` | Security middleware |
| `morgan` | HTTP request logging |

> [!NOTE]
> As of 2026, Express 5+ is standard, featuring better Promise handling and performance.


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