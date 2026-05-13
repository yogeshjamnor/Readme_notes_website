# Java Deployment

Best practices for deploying Java applications.

## Packaging for Production

1.  **JAR (Java Archive)**: For standalone applications (Standard for Spring Boot).
    ```bash
    mvn clean package
    java -jar target/app.jar
    ```
2.  **WAR (Web Archive)**: For deployment to application servers like Tomcat or JBoss.

## Containerization (Docker)

Multi-stage build for a Spring Boot application:

```dockerfile
# Build Stage
FROM maven:3.9-eclipse-temurin-21 AS build
WORKDIR /app
COPY pom.xml .
RUN mvn dependency:go-offline
COPY src ./src
RUN mvn package -DskipTests

# Run Stage
FROM eclipse-temurin:21-jre-alpine
WORKDIR /app
COPY --from=build /app/target/*.jar app.jar
EXPOSE 8080
ENTRYPOINT ["java", "-jar", "app.jar"]
```
## Cloud Platforms

- **AWS Elastic Beanstalk**: Easy JAR deployment.
- **Google App Engine**: Managed environment for Java.
- **Heroku**: Native Java support.
- **Azure App Service**: Support for JAR/WAR and Docker.

## JVM Tuning for Production

- **Memory Settings**: `-Xms` (Initial heap) and `-Xmx` (Max heap).
- **GC Choice**: `-XX:+UseG1GC` (Standard) or `-XX:+UseZGC` (Low latency).
- **Container Awareness**: Java 10+ handles container limits automatically, but verify with `-XX:MaxRAMPercentage`.

## Security Checklist

- [ ] **Dependencies**: Check for vulnerabilities with `mvn dependency-check:check`.
- [ ] **HTTPS**: Ensure the application server uses TLS.
- [ ] **Secrets**: Never store secrets in `application.properties`; use environment variables.
- [ ] **Updates**: Keep the JDK and dependencies updated.


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
