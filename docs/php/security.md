# PHP Security

Security practices for PHP web applications.

## 1. SQL injection
- Always use prepared statements (`PDO::prepare`) instead of string concatenation.

## 2. Passwords

```php
$hash = password_hash($password, PASSWORD_DEFAULT);
$ok = password_verify($password, $hash);
```
## 3. CSRF
- Use CSRF tokens for state-changing requests (POST/PUT/PATCH/DELETE).

## 4. XSS
- Escape output by default; sanitize HTML if you must render user-provided HTML.

## Code Examples

### Prepared statement pattern
```php
$stmt = $pdo->prepare(\"SELECT * FROM users WHERE email = ?\");
$stmt->execute([$email]);
```
> [!TIP]
> Use the **Copy** button in the top-right of code blocks to quickly copy commands to your clipboard.
