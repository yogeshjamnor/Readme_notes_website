# MySQL Deployment

Deploying MySQL for production usage.

## High Availability

- **MySQL Replication**: Master-Slave or Master-Master setup.
- **MySQL Group Replication**: Native HA solution for MySQL.
- **ProxySQL**: High-performance SQL proxy for load balancing.

## Backup and Recovery

1.  **Logical Backups**:
    ```bash
    mysqldump --all-databases --single-transaction --quick --lock-tables=false > full_backup.sql
    ```
2.  **Physical Backups**: Using tools like Percona XtraBackup for large databases.
3.  **Cloud Backups**: Use managed service snapshots (RDS, PlanetScale).

## Performance Tuning (my.cnf)

Key parameters to tune in `/etc/mysql/my.cnf`:
- `innodb_buffer_pool_size`: Set to ~70-80% of system RAM.
- `max_connections`: Adjust based on expected load.
- `slow_query_log`: Enable to find performance bottlenecks.

## Security Checklist

- [ ] **Remote Root Access**: Disable it.
- [ ] **Firewall**: Restrict port 3306 to known application servers.
- [ ] **Encryption**: Enable TLS for connections.
- [ ] **User Privileges**: Grant only necessary permissions (Principle of Least Privilege).


## Code Examples

### Transaction pattern
```sql
BEGIN;
```
```sql
-- Your statements here
```
```sql
COMMIT;
```
```sql
-- or: ROLLBACK;
```
### Upsert (insert or update)
```sql
INSERT INTO users (id, name, email)
```
```sql
VALUES (1, 'Alice', 'alice@example.com')
```
```sql
ON DUPLICATE KEY UPDATE
```
```sql
name = VALUES(name),
```
```sql
email = VALUES(email);
```
> [!TIP]
> Use the **Copy** button in the top-right of code blocks to quickly copy commands to your clipboard.
