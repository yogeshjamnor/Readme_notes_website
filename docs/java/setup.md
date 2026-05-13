# Java Project Setup

Setting up a structured Java project using Maven and Gradle.

## Recommended Folder Structure (Maven/Gradle Standard)

```text
my-project/
├── src/
│   ├── main/
│   │   ├── java/        # Source code (.java files)
│   │   │   └── com/example/app/
│   │   └── resources/   # Config files (application.properties)
│   └── test/
│       ├── java/        # Test code
│       └── resources/   # Test config
├── target/ (Maven)      # Compiled classes/JARs
├── build/ (Gradle)       # Compiled classes/JARs
├── pom.xml (Maven)       # Project config
└── build.gradle (Gradle) # Project config
```
## Environment Variables

Ensure `JAVA_HOME` is set correctly.

```bash
# Linux/macOS (.bashrc or .zshrc)
export JAVA_HOME=$(sdk home java 21.0.2-tem)
export PATH=$JAVA_HOME/bin:$PATH
```
## Initializing a Project

### 1. Using Maven
```bash
mvn archetype:generate -DgroupId=com.example -DartifactId=my-app -DarchetypeArtifactId=maven-archetype-quickstart -DinteractiveMode=false
```
### 2. Using Spring Initializr (Spring Boot)
Go to [start.spring.io](https://start.spring.io/) or use the CLI:
```bash
spring init --dependencies=web,data-jpa,h2 my-spring-app
```
## Best Practices

1.  **Package Naming**: Use reverse domain name notation (e.g., `com.company.project`).
2.  **Lombok**: Use Lombok to reduce boilerplate (Getters, Setters, Constructors).
3.  **Modern Java Features**: Utilize Records (Java 16+), Pattern Matching, and Virtual Threads (Java 21+).
4.  **Testing**: Use JUnit 5 and AssertJ for robust testing.

> [!IMPORTANT]
> Always use a build tool (Maven/Gradle) instead of manual compilation for real projects.


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
