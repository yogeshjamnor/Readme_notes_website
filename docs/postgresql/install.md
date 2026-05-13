# Installing PostgreSQL

Guide to installing PostgreSQL Server and clients in 2026.

## 1. Local Installation (Ubuntu)

```bash
sudo apt update
```
```bash
sudo apt install postgresql postgresql-contrib
```
## 2. Docker Installation (Recommended for Dev)

```bash
docker run --name postgres-db -e POSTGRES_PASSWORD=mysecretpassword -d -p 5432:5432 postgres:latest
```
## 3. Cloud / Managed Options

- **Neon**: Serverless Postgres with branching (Highly recommended).
- **Supabase**: Open-source Firebase alternative based on Postgres.
- **AWS RDS / Google Cloud SQL**: Traditional managed Postgres.

## Verifying Installation

```bash
psql --version
```
## GUI Tools

| Tool | Purpose |
| :--- | :--- |
| **pgAdmin 4** | Official, feature-rich GUI |
| **DBeaver** | Excellent multi-db tool |
| **Postico** | Premium, native client for macOS |

> [!TIP]
> Use `Neon` or `Supabase` for rapid development without managing server infrastructure.


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