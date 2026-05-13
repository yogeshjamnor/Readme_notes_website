# Debugging Java

Tools and techniques for finding and fixing bugs in Java.

## IDE Debugging (IntelliJ/Eclipse/VS Code)

1.  Set breakpoints in the editor.
2.  Click "Debug" (instead of "Run").
3.  Inspect variables, evaluate expressions, and step through code.

## Remote Debugging

Useful for debugging applications running on a server.

```bash
java -agentlib:jdwp=transport=dt_socket,server=y,suspend=n,address=*:5005 -jar app.jar
```
Then connect your IDE to the server IP on port 5005.

## Common Errors and Fixes

### 1. `NullPointerException` (NPE)
- **Cause**: Trying to call a method or access a field on a `null` object.
- **Fix**: Add null checks or use `Optional<T>`.

### 2. `ClassNotFoundException` / `NoClassDefFoundError`
- **Cause**: Missing JAR in classpath.
- **Fix**: Check Maven/Gradle dependencies and ensure the JAR is built correctly.

### 3. `OutOfMemoryError`
- **Cause**: Heap space exhausted or memory leak.
- **Fix**: Increase heap size (`-Xmx`) or profile with VisualVM to find leaks.

## Profiling Tools

- **VisualVM**: All-in-one GUI for monitoring, profiling, and heap dumps.
- **JProfiler**: Advanced commercial profiler.
- **async-profiler**: Low-overhead profiler for Linux.

## Logging (SLF4J + Logback)

```java
import org.slf4j.Logger;
import org.slf4j.LoggerFactory;

private static final Logger logger = LoggerFactory.getLogger(MyClass.class);
logger.info("Doing something");
logger.error("Something went wrong", exception);
```
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
