# Go CRUD (`database/sql`)

Basic CRUD patterns using `database/sql`.

## 1. Connect

```go
db, err := sql.Open(\"mysql\", dsn)
if err != nil { /* handle */ }
defer db.Close()
```
## 2. CREATE

```go
_, err := db.Exec(\"INSERT INTO users (email, name) VALUES (?, ?)\", email, name)
```
## 3. READ

```go
row := db.QueryRow(\"SELECT id, email, name FROM users WHERE id = ?\", id)
err := row.Scan(&user.ID, &user.Email, &user.Name)
```
## 4. UPDATE

```go
_, err := db.Exec(\"UPDATE users SET name = ? WHERE id = ?\", name, id)
```
## 5. DELETE

```go
_, err := db.Exec(\"DELETE FROM users WHERE id = ?\", id)
```
> [!TIP]
> Use the **Copy** button in the top-right of code blocks to quickly copy commands to your clipboard.
