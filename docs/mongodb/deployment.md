# MongoDB Deployment

Best practices for deploying MongoDB in production.

## Replica Sets

Always use a replica set (minimum 3 nodes) for high availability and data redundancy.

- **Primary**: Handles all writes.
- **Secondary**: Replicates data from primary; can handle reads.
- **Arbiter**: (Optional) Participates in elections but doesn't hold data.

## Backup Strategies

1.  **Atlas Backups**: Automated snapshots and point-in-time recovery.
2.  **`mongodump` / `mongorestore`**:
    ```bash
    # Backup
    mongodump --uri="mongodb://localhost:27017" --out=/backup/dir
    # Restore
    mongorestore --uri="mongodb://localhost:27017" /backup/dir
    ```

## Performance Optimization

- **Indexing**: Ensure all frequent queries are covered by indexes.
- **WiredTiger Cache**: Adjust cache size based on available RAM.
- **Connection Pooling**: Configure the driver to use an appropriate pool size.

## Security Hardening

- [ ] **Disable Default Port**: (If possible) to avoid automated scans.
- [ ] **Enable Auth**: Ensure `--auth` is enabled in `mongod.conf`.
- [ ] **Bind IP**: Only bind to internal network interfaces.
- [ ] **Encryption at Rest**: Use encrypted storage engines.


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
