# Java Security Checklist

Guidelines for building secure Java applications.

## 1. Dependency Management
- [ ] **OWASP Dependency-Check**: Use the Maven/Gradle plugin to identify vulnerable libraries.
- [ ] **Keep Updated**: Regularly update your JDK and third-party dependencies (especially Spring, Log4j, etc.).

## 2. Web Security (Spring Boot)
- [ ] **Spring Security**: Use Spring Security to handle authentication and authorization.
- [ ] **CSRF Protection**: Ensure CSRF protection is enabled for state-changing requests.
- [ ] **Security Headers**: Use `Strict-Transport-Security`, `X-Content-Type-Options`, and `X-Frame-Options`.

## 3. Input Validation & Data Handling
- [ ] **Bean Validation**: Use JSR 380 (Hibernate Validator) for input validation.
- [ ] **XSS**: Use template engines that auto-escape (Thymeleaf).
- [ ] **SQL Injection**: Always use `PreparedStatement`, JPA, or MyBatis.

## 4. Code Hardening
- [ ] **Avoid Serialization**: Native Java serialization is often vulnerable. Use JSON (Jackson/Gson) instead.
- [ ] **Secure Random**: Use `java.security.SecureRandom` for cryptographic needs.
- [ ] **Reflection**: Be cautious with reflection on untrusted input.

## 5. JVM Security
- [ ] **Security Manager**: (Deprecated in newer versions) Use OS-level permissions instead.
- [ ] **Memory Protection**: Monitor for heap exhaustion and memory leaks.

## 6. Security Tools
| Tool | Purpose |
| :--- | :--- |
| **SpotBugs** | Static analysis (with `FindSecBugs` plugin) |
| **Snyk** | Dependency and code scanning |
| **SonarQube** | Code quality and security dashboard |

## 7. Example: Secure Random
```java
import java.security.SecureRandom;

SecureRandom random = new SecureRandom();
byte[] bytes = new byte[20];
random.nextBytes(bytes);
```
> [!IMPORTANT]
> Never hardcode credentials in your code or `application.properties`. Use environment variables or a vault service.


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
## Extra security notes (copy‑ready)

### Dependency scanning
- Keep dependencies updated
- Use the ecosystem scanner (`npm audit`, `pip-audit`, etc.)

### Secrets hygiene
- Do not commit `.env` / private keys
- Rotate leaked keys immediately


> [!TIP]
> Use the **Copy** button in the top-right of code blocks to quickly copy commands to your clipboard.
