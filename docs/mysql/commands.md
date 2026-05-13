# MySQL CLI Commands

Common commands for the `mysql` terminal client.

## Connection

```bash
# Connect as root
```
```bash
mysql -u root -p
```
```bash
# Connect to specific database
```
```bash
mysql -u app_user -p my_app_db
```
```bash
# Connect to remote host
```
```bash
mysql -h host_address -u user -p
```
## Database Management

```sql
SHOW DATABASES;
```
```sql
USE database_name;
```
```sql
CREATE DATABASE database_name;
```
```sql
DROP DATABASE database_name;
```
## Table Management

```sql
SHOW TABLES;
```
```sql
DESCRIBE table_name;
```
```sql
CREATE TABLE table_name (
```
```sql
id INT AUTO_INCREMENT PRIMARY KEY,
```
```sql
name VARCHAR(255) NOT NULL,
```
```sql
created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
```
```sql
);
```
```sql
DROP TABLE table_name;
```
```sql
ALTER TABLE table_name ADD COLUMN age INT;
```
## Import / Export

```bash
# Export (Dump)
```
```bash
mysqldump -u user -p database_name > backup.sql
```
```bash
# Import
```
```bash
mysql -u user -p database_name < backup.sql
```
## Useful Shortcuts

- `\c`: Clear the current input statement.
- `\q`: Quit the mysql shell.
- `\G`: Send command and display results vertically.
- `source file.sql`: Execute SQL script from file inside shell.


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
