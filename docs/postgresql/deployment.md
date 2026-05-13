# PostgreSQL Deployment

Deploying PostgreSQL for production.

## High Availability & Scaling

- **Streaming Replication**: Standard master-slave setup.
- **Patroni**: Template for HA PostgreSQL using ZooKeeper/etcd/Consul.
- **PgBouncer**: Lightweight connection pooler (Essential for high concurrency).

## Backup Strategies

1.  **WAL Archiving**: Point-in-time recovery (PITR) using Continuous Archiving.
2.  **pg_dump**: For logical backups (suitable for smaller DBs).
3.  **Barman**: Backup and Recovery Manager for PostgreSQL.

## Performance Optimization (postgresql.conf)

- `shared_buffers`: Set to ~25% of system RAM.
- `work_mem`: Memory for internal sort operations and hash tables.
- `maintenance_work_mem`: Memory for maintenance tasks (VACUUM, CREATE INDEX).
- `effective_cache_size`: Total memory available for disk caching.

## Security Checklist

- [ ] **pg_hba.conf**: Restrict access to specific IP ranges and use `scram-sha-256`.
- [ ] **SSL/TLS**: Force encrypted connections.
- [ ] **Row Level Security (RLS)**: Restrict data access within a table based on user.
- [ ] **Audit Logging**: Use `pgaudit` for detailed operation logs.


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
### INSERT with `RETURNING`
```sql
INSERT INTO users (name, email)
```
```sql
VALUES ('Alice', 'alice@example.com')
```
```sql
RETURNING id;
```
> [!TIP]
> Use the **Copy** button in the top-right of code blocks to quickly copy commands to your clipboard.
