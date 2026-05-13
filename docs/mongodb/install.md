# Installing MongoDB

Guide to installing MongoDB Community Edition and MongoDB Atlas in 2026.

## 1. MongoDB Atlas (Cloud - Recommended)

The easiest way to get started with MongoDB.

1.  Sign up at [mongodb.com/cloud/atlas](https://www.mongodb.com/cloud/atlas).
2.  Create a free cluster (Shared).
3.  Whitelist your IP address.
4.  Create a database user.
5.  Get your connection string (e.g., `mongodb+srv://<user>:<pass>@cluster.mongodb.net/dbname`).

## 2. Local Installation (Docker)

```bash
docker run --name mongodb -d -p 27017:27017 mongo:latest
```
## 3. Direct Installation (Ubuntu)

```bash
sudo apt-get install -y mongodb-org
sudo systemctl start mongod
sudo systemctl enable mongod
```
## Verifying Installation

```bash
mongosh --version
```
## GUI Tools

| Tool | Purpose |
| :--- | :--- |
| **MongoDB Compass** | Official GUI for MongoDB |
| **Studio 3T** | Advanced IDE for MongoDB |
| **VS Code Extension** | MongoDB integration inside VS Code |

> [!TIP]
> Use `mongosh` instead of the legacy `mongo` shell for a modern interactive experience.


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