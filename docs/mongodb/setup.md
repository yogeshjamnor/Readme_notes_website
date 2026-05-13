# MongoDB Setup

Configuring MongoDB for development and production.

## Connection String Format

```text
mongodb://[username:password@]host1[:port1][,...hostN[:portN]][/[defaultauthdb][?options]]
```
Example (Local):
```text
mongodb://localhost:27017/my_database
```
Example (Atlas):
```text
mongodb+srv://admin:password@cluster0.abcde.mongodb.net/my_database?retryWrites=true&w=majority
```
## Security Configuration

1.  **Authentication**: Always enable authentication (default in Atlas).
2.  **IP Whitelisting**: Only allow trusted IPs to connect.
3.  **TLS/SSL**: Use encrypted connections for all production traffic.
4.  **Role-Based Access Control (RBAC)**: Create users with specific privileges (e.g., `readWrite`, `dbAdmin`).

## Recommended Database Structure

- **Database**: `my_application`
- **Collections**: `users`, `products`, `orders`
- **Documents**: JSON-like BSON objects.

## Mongoose Setup (Node.js)

```javascript
import mongoose from 'mongoose';

const connectDB = async () => {
  try {
    await mongoose.connect(process.env.MONGO_URI);
    console.log('MongoDB Connected');
  } catch (err) {
    console.error(err.message);
    process.exit(1);
  }
};
```
> [!IMPORTANT]
> Never commit your connection string with credentials to version control. Use environment variables.


## Code Examples

### Find with projection + sort
```javascript
// mongosh
use mydb;

db.users
  .find({ status: "active" }, { name: 1, email: 1 })
  .sort({ createdAt: -1 })
  .limit(20);
```
### Basic aggregation
```javascript
db.orders.aggregate([
  { $match: { status: "paid" } },
  { $group: { _id: "$userId", total: { $sum: "$amount" } } },
  { $sort: { total: -1 } },
]);
```
> [!TIP]
> Use the **Copy** button in the top-right of code blocks to quickly copy commands to your clipboard.
