# Express.js CLI & Scripts

Common scripts and commands for Express.js development.

## package.json Scripts

```json
"scripts": {
  "start": "node src/server.js",
  "dev": "node --watch src/server.js",
  "test": "jest",
  "lint": "eslint ."
}
```
## Running the App

```bash
# Development
npm run dev

# Production
npm start
```
## Security & Maintenance

```bash
# Check for outdated packages
npm outdated

# Check for security vulnerabilities
npm audit
```
## Environment Variable Setup

```bash
# Set port temporarily (Linux/macOS)
PORT=5000 npm start

# Set port temporarily (Windows PowerShell)
$env:PORT=5000; npm start
```
## Useful CLI Shortcuts

- `rs`: Restart the watcher (if using nodemon or node --watch).
- `Ctrl + C`: Stop the server.
- `npx kill-port 3000`: Quickly free up a stuck port.


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
