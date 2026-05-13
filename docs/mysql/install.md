# Installing MySQL

Guide to installing MySQL Server and clients in 2026.

## 1. Local Installation (Ubuntu)

```bash
sudo apt update
```
```bash
sudo apt install mysql-server
```
```bash
sudo mysql_secure_installation
```
## 2. Docker Installation (Recommended for Dev)

```bash
docker run --name mysql-db -e MYSQL_ROOT_PASSWORD=my-secret-pw -d -p 3306:3306 mysql:latest
```
## 3. Cloud Options

- **Amazon RDS**: Fully managed MySQL.
- **PlanetScale**: Serverless MySQL (highly recommended for modern apps).
- **Google Cloud SQL**: Managed MySQL on GCP.

## Verifying Installation

```bash
mysql --version
```
## GUI Tools

| Tool | Purpose |
| :--- | :--- |
| **MySQL Workbench** | Official administrative tool |
| **DBeaver** | Universal database tool (Recommended) |
| **TablePlus** | Modern, native GUI for macOS/Windows |

> [!TIP]
> Use `mysql_secure_installation` after local install to remove anonymous users and disable remote root login.


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