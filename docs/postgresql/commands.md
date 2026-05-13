# PostgreSQL CLI Commands

Essential commands for the `psql` terminal client.

## Connection

```bash
# Connect to default database
```
```bash
psql -U postgres
```
```bash
# Connect to specific database
```
```bash
psql -U app_user -d my_app_db
```
```bash
# Connect via URI
```
```bash
psql postgresql://user:pass@host:5432/dbname
```
## Internal `psql` Commands (Slash Commands)

| Command | Description |
| :--- | :--- |
| `\l` | List all databases |
| `\c dbname` | Connect to database |
| `\dt` | List all tables in current db |
| `\d table` | Describe table structure |
| `\du` | List all users/roles |
| `\dn` | List schemas |
| `\df` | List functions |
| `\q` | Quit psql |

## Database Management

```sql
CREATE DATABASE name;
```
```sql
DROP DATABASE name;
```
## Backup and Restore

```bash
# Export (Dump)
```
```bash
pg_dump -U user dbname > backup.sql
```
```bash
# Import
```
```bash
psql -U user dbname < backup.sql
```
## Useful Shortcuts

- `\x`: Toggle expanded display (useful for wide rows).
- `\watch 2`: Re-run the last command every 2 seconds.
- `\timing`: Show how long each query takes.
- `\e`: Open last command in external editor.


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
