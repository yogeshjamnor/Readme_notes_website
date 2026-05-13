# Express + MongoDB CRUD APIs

Implementing a full CRUD (Create, Read, Update, Delete) API using Express and Mongoose.

## 1. Define the Model

```javascript
import mongoose from 'mongoose';

const userSchema = new mongoose.Schema({
  name: String,
  email: { type: String, unique: true },
  age: Number
});

export const User = mongoose.model('User', userSchema);
```
## 2. Implement CRUD Routes

```javascript
import express from 'express';
import { User } from './models/User.js';

const router = express.Router();

// CREATE
router.post('/users', async (req, res) => {
  const newUser = new User(req.body);
  await newUser.save();
  res.status(201).json(newUser);
});

// READ ALL
router.get('/users', async (req, res) => {
  const users = await User.find();
  res.json(users);
});

// READ ONE
router.get('/users/:id', async (req, res) => {
  const user = await User.findById(req.params.id);
  res.json(user);
});

// UPDATE
router.put('/users/:id', async (req, res) => {
  const updatedUser = await User.findByIdAndUpdate(req.params.id, req.body, { new: true });
  res.json(updatedUser);
});

// DELETE
router.delete('/users/:id', async (req, res) => {
  await User.findByIdAndDelete(req.params.id);
  res.status(204).send();
});

export default router;
```
## Best Practices

- **Validation**: Use `mongoose` built-in validation or `zod`.
- **Pagination**: Use `.limit()` and `.skip()` for large datasets.
- **Error Handling**: Wrap route logic in try/catch or use an async middleware.
- **Project Structure**: Separate routes, controllers, and models.


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
