# Debugging MySQL

Troubleshooting queries and server issues.

## Slow Query Log

Identify queries that take too long to execute.

```sql
-- Enable slow query log temporarily
```
```sql
SET GLOBAL slow_query_log = 'ON';
```
```sql
SET GLOBAL long_query_time = 1; -- seconds
```
## EXPLAIN Plan

Analyze how MySQL executes a query.

```sql
EXPLAIN SELECT * FROM users WHERE email = 'test@example.com';
```
Key columns to look at:
- `type`: `const` or `ref` is good; `ALL` (full table scan) is bad.
- `key`: The index used.
- `rows`: Estimated number of rows scanned.

## Common Errors

### 1. `Too many connections`
- **Cause**: Application not closing connections or traffic spike.
- **Fix**: Increase `max_connections` or implement connection pooling.

### 2. `Lock wait timeout exceeded`
- **Cause**: Transactions holding locks for too long.
- **Fix**: Check for long-running transactions and optimize them.

### 3. `Access denied for user`
- **Cause**: Wrong password, host, or missing privileges.
- **Fix**: Check `GRANTS` and connection string.

## Process List

See what the server is currently doing.
```sql
SHOW PROCESSLIST;
```
```sql
-- Or for more detail
```
```sql
SELECT * FROM information_schema.processlist;
```
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
