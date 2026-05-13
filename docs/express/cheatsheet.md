# Express.js Cheatsheet

Quick reference for Express APIs and patterns.

## Route Methods

```javascript
app.get('/path', (req, res) => { ... });
app.post('/path', (req, res) => { ... });
app.put('/path', (req, res) => { ... });
app.patch('/path', (req, res) => { ... });
app.delete('/path', (req, res) => { ... });
app.all('/path', (req, res) => { ... });
```
## Request Object (`req`)

- `req.params`: URL parameters (e.g., `/:id`).
- `req.query`: Query string parameters (e.g., `?search=foo`).
- `req.body`: Parsed request body (requires middleware).
- `req.headers`: Request headers.
- `req.ip`: Client IP address.

## Response Object (`res`)

- `res.send()`: Send a basic response.
- `res.json()`: Send a JSON response.
- `res.status(404)`: Set HTTP status.
- `res.redirect('/path')`: Redirect.
- `res.setHeader('Key', 'Value')`: Set header.
- `res.cookie('name', 'value')`: Set cookie.

## Routing with `Router`

```javascript
const router = express.Router();
router.get('/profile', (req, res) => { ... });
app.use('/user', router); // Accessible at /user/profile
```
## Status Codes Quick Ref

- `200 OK`: Success.
- `201 Created`: Post success.
- `400 Bad Request`: Client error.
- `401 Unauthorized`: Missing authentication.
- `403 Forbidden`: Insufficient permissions.
- `404 Not Found`: Route doesn't exist.
- `500 Internal Server Error`: Server crash.


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
