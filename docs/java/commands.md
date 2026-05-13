# Java CLI Commands

Essential commands for compiling, running, and building Java projects.

## Compilation & Execution (Basic)

```bash
# Compile a single file
javac Main.java

# Run the compiled class
java Main

# Run a single file directly (Java 11+)
java Main.java
```
## Maven Commands

| Action | Command |
| :--- | :--- |
| **Clean build** | `mvn clean install` |
| **Run tests** | `mvn test` |
| **Run application**| `mvn exec:java -Dexec.mainClass="com.example.Main"` |
| **Package to JAR** | `mvn package` |
| **Dependency tree**| `mvn dependency:tree` |

## Gradle Commands

| Action | Command |
| :--- | :--- |
| **Build** | `./gradlew build` |
| **Clean** | `./gradlew clean` |
| **Run tests** | `./gradlew test` |
| **Run app** | `./gradlew bootRun` (Spring Boot) |
| **List tasks** | `./gradlew tasks` |

## JAR Management

```bash
# Create executable JAR (Maven)
mvn package
java -jar target/my-app-1.0.jar

# Inspect JAR content
jar tf my-app.jar
```
## Useful CLI Shortcuts

- `jshell`: Interactive Java REPL (Java 9+).
- `jps`: List running Java processes.
- `jmap -heap <pid>`: View heap memory usage.
- `jstack <pid>`: Get thread stack traces.


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
