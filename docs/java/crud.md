# Java CRUD Examples

Implementing CRUD operations using JDBC (Standard) and Spring Data JPA (Modern).

## 1. Standard JDBC CRUD

```java
import java.sql.*;

public class JdbcExample {
    public static void main(String[] args) throws SQLException {
        String url = "jdbc:postgresql://localhost:5432/my_db";
        try (Connection conn = DriverManager.getConnection(url, "user", "pass")) {
            
            // CREATE
            String sql = "INSERT INTO users (name, email) VALUES (?, ?)";
            PreparedStatement ps = conn.prepareStatement(sql);
            ps.setString(1, "Alice");
            ps.setString(2, "alice@example.com");
            ps.executeUpdate();

            // READ
            ResultSet rs = conn.createStatement().executeQuery("SELECT * FROM users");
            while (rs.next()) {
                System.out.println(rs.getString("name"));
            }

            // UPDATE
            String updateSql = "UPDATE users SET name = ? WHERE id = ?";
            ps = conn.prepareStatement(updateSql);
            ps.setString(1, "Alice New");
            ps.setInt(2, 1);
            ps.executeUpdate();

            // DELETE
            String deleteSql = "DELETE FROM users WHERE id = ?";
            ps = conn.prepareStatement(deleteSql);
            ps.setInt(1, 1);
            ps.executeUpdate();
        }
    }
}
```
## 2. Spring Data JPA CRUD (Modern)

```java
@Entity
public class User {
    @Id @GeneratedValue
    private Long id;
    private String name;
    private String email;
    // Getters/Setters
}

public interface UserRepository extends JpaRepository<User, Long> { }

@Service
public class UserService {
    @Autowired private UserRepository repo;

    public void crud() {
        // CREATE
        User user = repo.save(new User("Alice", "alice@example.com"));

        // READ
        List<User> users = repo.findAll();
        Optional<User> u = repo.findById(1L);

        // UPDATE
        user.setName("Alice New");
        repo.save(user);

        // DELETE
        repo.deleteById(1L);
    }
}
```
## Best Practices

- **Use Connection Pooling**: (HikariCP) instead of opening a connection per request.
- **SQL Injection**: Always use `PreparedStatement` or an ORM (JPA/Hibernate).
- **Transactions**: Use `@Transactional` in Spring.


## Code Examples

### Streams: filter + map + collect
```java
import java.util.List;

List<Integer> numbers = List.of(1, 2, 3, 4);
List<Integer> doubledEvens = numbers.stream()
  .filter(n -> n % 2 == 0)
  .map(n -> n * 2)
  .toList();
```
> [!TIP]
> Use the **Copy** button in the top-right of code blocks to quickly copy commands to your clipboard.
