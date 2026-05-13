# PostgreSQL Setup

Configuring PostgreSQL for security and development.

## Accessing the Shell

By default, Postgres creates a user named `postgres`.

```bash
# Switch to postgres user
```
```bash
sudo -i -u postgres
```
```bash
# Open shell
```
```bash
psql
```
## Creating a Database and User

```sql
-- Create database
```
```sql
CREATE DATABASE my_app_db;
```
```sql
-- Create user
```
```sql
CREATE USER app_user WITH ENCRYPTED PASSWORD 'password123';
```
```sql
-- Grant privileges
```
```sql
GRANT ALL PRIVILEGES ON DATABASE my_app_db TO app_user;
```
```sql
-- Grant schema privileges (Required for Postgres 15+)
```
```sql
\c my_app_db
```
```sql
GRANT ALL ON SCHEMA public TO app_user;
```
## Environment Variables

```env
DATABASE_URL=postgresql://app_user:password123@localhost:5432/my_app_db
```
## Node.js Connection (node-postgres / pg)

```javascript
import pkg from 'pg';
const { Pool } = pkg;

const pool = new Pool({
  connectionString: process.env.DATABASE_URL,
});

const res = await pool.query('SELECT NOW()');
```
> [!IMPORTANT]
> Post-Postgres 15, you must explicitly grant permissions on the `public` schema to new users even if they own the database.


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
