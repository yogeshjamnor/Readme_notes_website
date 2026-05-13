# PostgreSQL CRUD Operations

Standard SQL commands with PostgreSQL-specific features.

## 1. CREATE (Insert)

```sql
-- Insert and return the ID
```
```sql
INSERT INTO users (name, email)
```
```sql
VALUES ('Alice', 'alice@example.com')
```
```sql
RETURNING id;
```
```sql
-- Upsert (Update on Conflict)
```
```sql
INSERT INTO users (id, name)
```
```sql
VALUES (1, 'Alice New')
```
```sql
ON CONFLICT (id) DO UPDATE SET name = EXCLUDED.name;
```
## 2. READ (Select)

```sql
-- Select with JSON output
```
```sql
SELECT json_build_object('id', id, 'name', name) FROM users;
```
```sql
-- Select with limit and offset
```
```sql
SELECT * FROM users LIMIT 10 OFFSET 5;
```
```sql
-- Pattern matching (ILIKE for case-insensitive)
```
```sql
SELECT * FROM users WHERE name ILIKE 'a%';
```
## 3. UPDATE

```sql
-- Update with join
```
```sql
UPDATE orders
```
```sql
SET status = 'shipped'
```
```sql
FROM users
```
```sql
WHERE orders.user_id = users.id AND users.membership = 'gold';
```
## 4. DELETE

```sql
-- Delete and return deleted rows
```
```sql
DELETE FROM users WHERE age < 18 RETURNING *;
```
## JSONB Operations (Postgres Unique)

```sql
-- Insert JSON data
```
```sql
INSERT INTO products (metadata) VALUES ('{"color": "red", "size": "M"}');
```
```sql
-- Query JSON data
```
```sql
SELECT * FROM products WHERE metadata->>'color' = 'red';
```
> [!TIP]
> Use `RETURNING *` after an `INSERT` or `UPDATE` to get the final state of the row without a separate `SELECT` query.


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