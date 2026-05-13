# PostgreSQL Security Checklist

Security guidelines for PostgreSQL databases.

## 1. Connection Security
- [ ] **pg_hba.conf**: Restrict connections to specific users and IP ranges. Use `scram-sha-256` for authentication.
- [ ] **SSL/TLS**: Force SSL connections in `postgresql.conf` using `ssl = on`.

## 2. Role & Privilege Management
- [ ] **Least Privilege**: Grant only the required permissions on specific tables and schemas.
- [ ] **Public Schema**: Revoke `CREATE` permission on the `public` schema from `PUBLIC`.
  ```sql
  REVOKE CREATE ON SCHEMA public FROM PUBLIC;
  ```
- [ ] **Non-Superuser**: Run applications with a non-superuser role.

## 3. Data Protection
- [ ] **Row Level Security (RLS)**: Use RLS to restrict which rows a user can see based on their identity.
- [ ] **Encryption at Rest**: Use tools like TDE or file-system level encryption.

## 4. Auditing & Logging
- [ ] **pgaudit**: Use the `pgaudit` extension for detailed session and object logging.
- [ ] **Log Duration**: Log slow queries to identify potential DoS vectors.

## 5. Security Queries
```sql
-- List all roles and their attributes
```
```sql
\du
```
```sql
-- Check table permissions
```
```sql
\z table_name
```
## 6. Server Hardening
- [ ] **File Permissions**: Ensure the Postgres data directory has restrictive permissions (typically `0700`).
- [ ] **Updates**: Regularly update PostgreSQL to the latest minor version for security fixes.

> [!IMPORTANT]
> PostgreSQL 15+ has more restrictive default permissions on the `public` schema. Ensure your setup scripts account for this.


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
## Extra security notes (copy‑ready)

### Least privilege (roles/users)
- Create separate DB users for app vs migrations/admin
- Grant only required permissions (avoid `SUPER` / `ALL PRIVILEGES`)

### Parameterized queries (avoid string concatenation)
```sql
-- ✅ good (parameterized) — syntax depends on client library
```
```sql
SELECT * FROM users WHERE email = ?;
```
```sql
-- ❌ bad
```
```sql
-- SELECT * FROM users WHERE email = '" + input + "';
```
### Backups + encryption
- Encrypt backups at rest
- Restrict backup access (IAM/ACL)


> [!TIP]
> Use the **Copy** button in the top-right of code blocks to quickly copy commands to your clipboard.
