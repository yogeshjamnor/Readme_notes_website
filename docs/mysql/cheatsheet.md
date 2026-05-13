# MySQL Cheatsheet

Quick reference for SQL syntax and common MySQL functions.

## Data Types

| Type | Description |
| :--- | :--- |
| `INT` | Whole numbers |
| `VARCHAR(N)` | Variable length string (max N) |
| `TEXT` | Long text |
| `DATE` | YYYY-MM-DD |
| `DATETIME` | YYYY-MM-DD HH:MM:SS |
| `DECIMAL(P,D)`| Fixed-point decimal |

## String Functions

```sql
CONCAT(str1, str2) -- Join strings
```
```sql
UPPER(str)         -- Uppercase
```
```sql
LOWER(str)         -- Lowercase
```
```sql
LENGTH(str)        -- Character count
```
```sql
SUBSTRING(str, 1, 5) -- Extract part
```
## Aggregate Functions

```sql
COUNT(*) -- Number of rows
```
```sql
SUM(col) -- Sum of values
```
```sql
AVG(col) -- Average of values
```
```sql
MAX(col) -- Maximum value
```
```sql
MIN(col) -- Minimum value
```
## Transaction Control

```sql
START TRANSACTION;
```
```sql
-- SQL commands
```
```sql
COMMIT; -- Save changes
```
```sql
-- OR
```
```sql
ROLLBACK; -- Undo changes
```
## Useful Commands

- `DESC table_name;`: Show columns.
- `SHOW CREATE TABLE table_name;`: Show SQL to recreate table.
- `SELECT USER();`: Current user.
- `SELECT VERSION();`: MySQL version.


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
