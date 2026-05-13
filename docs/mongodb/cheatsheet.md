# MongoDB Cheatsheet

Quick reference for MongoDB operators and shell commands.

## Query Operators

| Operator | Description |
| :--- | :--- |
| `$eq` | Equals |
| `$ne` | Not equals |
| `$gt` / `$gte` | Greater than / or equal |
| `$lt` / `$lte` | Less than / or equal |
| `$in` | Matches any value in an array |
| `$nin` | Matches none of the values in an array |
| `$exists` | Matches documents that have the specified field |

## Update Operators

| Operator | Description |
| :--- | :--- |
| `$set` | Sets the value of a field |
| `$unset` | Removes a field |
| `$inc` | Increments a field value |
| `$push` | Adds an item to an array |
| `$pull` | Removes an item from an array |
| `$rename` | Renames a field |

## Aggregation Framework

```javascript
db.orders.aggregate([
  { $match: { status: "A" } },
  { $group: { _id: "$cust_id", total: { $sum: "$amount" } } },
  { $sort: { total: -1 } }
])
```
## Useful Commands

- `db.collection.countDocuments()`: Get count.
- `db.collection.distinct("field")`: Get unique values.
- `db.getCollectionNames()`: List all collections.
- `db.help()`: Show help.


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
