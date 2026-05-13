# PHP CRUD (PDO)

Basic CRUD with PDO using prepared statements.

## 1. Connect

```php
$pdo = new PDO(
  "mysql:host=localhost;dbname=mydb;charset=utf8mb4",
  "user",
  "pass",
  [
    PDO::ATTR_ERRMODE => PDO::ERRMODE_EXCEPTION,
    PDO::ATTR_DEFAULT_FETCH_MODE => PDO::FETCH_ASSOC,
  ]
);
```
## 2. CREATE

```php
$stmt = $pdo->prepare("INSERT INTO users (email, name) VALUES (?, ?)");
$stmt->execute([$email, $name]);
```
## 3. READ

```php
$stmt = $pdo->prepare("SELECT id, email, name FROM users WHERE email = ?");
$stmt->execute([$email]);
$user = $stmt->fetch();
```
## 4. UPDATE

```php
$stmt = $pdo->prepare("UPDATE users SET name = ? WHERE id = ?");
$stmt->execute([$name, $id]);
```
## 5. DELETE

```php
$stmt = $pdo->prepare("DELETE FROM users WHERE id = ?");
$stmt->execute([$id]);
```
> [!TIP]
> Use the **Copy** button in the top-right of code blocks to quickly copy commands to your clipboard.
