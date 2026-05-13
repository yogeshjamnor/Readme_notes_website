# MySQL Setup

Configuring MySQL for security and performance.

## Initial Configuration

After installation, run the security script:
```bash
sudo mysql_secure_installation
```
## Creating a User and Database

```sql
-- Login as root
```
```sql
mysql -u root -p
```
```sql
-- Create database
```
```sql
CREATE DATABASE my_app_db;
```
```sql
-- Create user with restricted permissions
```
```sql
CREATE USER 'app_user'@'localhost' IDENTIFIED BY 'password123';
```
```sql
-- Grant privileges
```
```sql
GRANT ALL PRIVILEGES ON my_app_db.* TO 'app_user'@'localhost';
```
```sql
-- Apply changes
```
```sql
FLUSH PRIVILEGES;
```
## Environment Variables

```env
DB_HOST=localhost
DB_USER=app_user
DB_PASSWORD=password123
DB_NAME=my_app_db
DB_PORT=3306
```
## Node.js Connection (mysql2)

```javascript
import mysql from 'mysql2/promise';

const connection = await mysql.createConnection({
  host: process.env.DB_HOST,
  user: process.env.DB_USER,
  password: process.env.DB_PASSWORD,
  database: process.env.DB_NAME
});
```
> [!IMPORTANT]
> Never use the `root` user for your application. Always create a dedicated user with limited privileges.


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
