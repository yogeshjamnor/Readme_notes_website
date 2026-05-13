# Debugging PostgreSQL

Troubleshooting performance and query issues.

## Query Performance (EXPLAIN ANALYZE)

Unlike `EXPLAIN`, `EXPLAIN ANALYZE` actually executes the query and provides real timing data.

```sql
EXPLAIN ANALYZE SELECT * FROM users WHERE email = 'test@example.com';
```
## Logging Slow Queries

Edit `postgresql.conf`:
```text
log_min_duration_statement = 500  # Log statements taking > 500ms
```
## Monitoring Active Queries

```sql
SELECT pid, now() - query_start AS duration, query, state
```
```sql
FROM pg_stat_activity
```
```sql
WHERE state != 'idle'
```
```sql
ORDER BY duration DESC;
```
## Common Errors

### 1. `FATAL: remaining connection slots are reserved for non-replication superuser connections`
- **Cause**: Max connections reached.
- **Fix**: Use `PgBouncer` or increase `max_connections`.

### 2. `ERROR: relation "table_name" does not exist`
- **Cause**: Case sensitivity (Postgres lowercases unquoted names) or wrong schema.
- **Fix**: Use lowercase table names or quote them `"TableName"`.

### 3. `Deadlock detected`
- **Cause**: Two transactions waiting for locks held by each other.
- **Fix**: Ensure consistent locking order in application code.

## Tools

- **pg_stat_statements**: Extension to track execution statistics of all SQL statements.
- **Explain.dalibo.com**: Visualizer for Postgres EXPLAIN plans.


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
