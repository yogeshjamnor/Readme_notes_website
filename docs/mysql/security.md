# MySQL Security Checklist

Best practices for securing MySQL databases.

## 1. User & Authentication
- [ ] **Secure Installation**: Run `mysql_secure_installation`.
- [ ] **Remove Anonymous Users**: Ensure no anonymous accounts exist.
- [ ] **Disable Remote Root**: Never allow the `root` user to connect remotely.
- [ ] **Specific Privileges**: Grant only necessary permissions to application users.

## 2. Network Security
- [ ] **Firewall**: Restrict access to port 3306 to known IP addresses.
- [ ] **Bind Address**: Bind to `127.0.0.1` unless remote access is required.
- [ ] **SSL/TLS**: Enable and require encrypted connections for remote access.

## 3. Configuration Hardening
- [ ] **Local Infile**: Disable `local_infile` to prevent unauthorized file reads.
  ```sql
  SET GLOBAL local_infile = 'OFF';
  ```
- [ ] **Plugin Security**: Use `caching_sha2_password` (default in 8.0+).

## 4. Logging & Monitoring
- [ ] **Error Log**: Regularly check `/var/log/mysql/error.log`.
- [ ] **Audit Plugin**: Use an audit plugin to track sensitive data access.

## 5. Helpful SQL Commands
```sql
-- List users and their hosts
```
```sql
SELECT user, host FROM mysql.user;
```
```sql
-- Check grants for a specific user
```
```sql
SHOW GRANTS FOR 'app_user'@'localhost';
```
## 6. Backup Security
- [ ] **Secure Storage**: Encrypt your backup files (`.sql` or binary backups).
- [ ] **Off-site Backups**: Store backups in a separate, secure location.

> [!CAUTION]
> Always use prepared statements in your application code to prevent SQL injection attacks.


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
