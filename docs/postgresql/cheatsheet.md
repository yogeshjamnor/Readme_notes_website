# PostgreSQL Cheatsheet

Quick reference for Postgres-specific types and functions.

## Data Types (Unique to Postgres)

| Type | Description |
| :--- | :--- |
| `SERIAL` | Auto-incrementing integer |
| `UUID` | Universally Unique Identifier |
| `JSONB` | Binary JSON (Efficient for indexing) |
| `ARRAY` | Collection of values (e.g., `text[]`) |
| `INET` | IP Address |
| `TIMESTAMPTZ` | Timestamp with time zone (Recommended) |

## JSONB Functions

```sql
-- Access key
```
```sql
data->'key'
```
```sql
-- Access key as text
```
```sql
data->>'key'
```
```sql
-- Check if contains
```
```sql
data @> '{"status": "active"}'
```
```sql
-- Get array length
```
```sql
jsonb_array_length(data->'items')
```
## Useful Functions

```sql
COALESCE(val1, val2) -- Return first non-null
```
```sql
NOW()                -- Current timestamp
```
```sql
GEN_RANDOM_UUID()    -- Generate UUID
```
```sql
AGE(timestamp)       -- Interval since timestamp
```
## Aggregate Functions

```sql
STRING_AGG(name, ', ') -- Concatenate strings with delimiter
```
```sql
ARRAY_AGG(id)          -- Group values into an array
```
## Useful Commands

- `\x on`: Enable expanded mode.
- `\copy table FROM 'file.csv' WITH CSV`: Import CSV.
- `\df`: Show functions.
- `\timing`: Toggle query timing.


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
