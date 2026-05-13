# MySQL CRUD Operations

Standard SQL commands for data manipulation.

## 1. CREATE (Insert)

```sql
-- Insert one row
```
```sql
INSERT INTO users (name, email, age)
```
```sql
VALUES ('Alice', 'alice@example.com', 25);
```
```sql
-- Insert multiple rows
```
```sql
INSERT INTO users (name, email, age)
```
```sql
VALUES
```
```sql
('Bob', 'bob@example.com', 30),
```
```sql
('Charlie', 'charlie@example.com', 35);
```
## 2. READ (Select)

```sql
-- Select all columns
```
```sql
SELECT * FROM users;
```
```sql
-- Select specific columns with filter
```
```sql
SELECT name, email FROM users WHERE age > 25;
```
```sql
-- Sorting results
```
```sql
SELECT * FROM users ORDER BY age DESC;
```
```sql
-- Limiting results (Pagination)
```
```sql
SELECT * FROM users LIMIT 10 OFFSET 20;
```
```sql
-- Pattern matching
```
```sql
SELECT * FROM users WHERE email LIKE '%@gmail.com';
```
## 3. UPDATE

```sql
-- Update specific row
```
```sql
UPDATE users SET age = 26 WHERE name = 'Alice';
```
```sql
-- Update multiple rows
```
```sql
UPDATE users SET status = 'active' WHERE age >= 18;
```
> [!CAUTION]
> Always use a `WHERE` clause in `UPDATE` and `DELETE` statements to avoid modifying all rows.

## 4. DELETE

```sql
-- Delete specific row
```
```sql
DELETE FROM users WHERE id = 1;
```
```sql
-- Delete all rows (TRUNCATE is faster for all rows)
```
```sql
TRUNCATE TABLE users;
```
## Joins

```sql
SELECT orders.id, users.name
```
```sql
FROM orders
```
```sql
INNER JOIN users ON orders.user_id = users.id;
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
