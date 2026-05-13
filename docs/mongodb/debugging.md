# Debugging MongoDB

Tools and methods for troubleshooting MongoDB issues.

## Profiling Slow Queries

Enable the database profiler to identify slow-running queries.

```javascript
// Enable profiling for queries taking longer than 100ms
db.setProfilingLevel(1, 100)

// View slow queries
db.system.profile.find().sort({ ts: -1 })
```
## Explain Plan

Use `.explain()` to see how MongoDB executes a query.

```javascript
db.users.find({ email: "alice@example.com" }).explain("executionStats")
```
Look for `stage: 'IXSCAN'` (index scan) vs `stage: 'COLLSCAN'` (collection scan).

## Common Issues

### 1. `Connection Refused`
- **Cause**: MongoDB service not running or wrong IP/port.
- **Fix**: Check `systemctl status mongod` or verify IP whitelisting in Atlas.

### 2. `Cursor Timeout`
- **Cause**: Iterating through a large result set too slowly.
- **Fix**: Use `.noCursorTimeout()` (use with caution) or process data in smaller batches.

### 3. `Write Conflict`
- **Cause**: Multiple operations trying to modify the same document simultaneously.
- **Fix**: Implement retry logic in the application.

## Logs

Check the MongoDB log file (usually `/var/log/mongodb/mongod.log`) for server-side errors and warnings.


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
