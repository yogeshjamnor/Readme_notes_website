# Java 21+ Cheatsheet

Quick reference for modern Java syntax and features.

## Variables and Types

```java
var name = "Alice"; // Type inference (Java 10+)
final var age = 30; // Constant

List<String> list = List.of("a", "b", "c"); // Immutable list
Map<String, Integer> map = Map.of("k1", 1, "k2", 2);
```
## Functional Programming (Streams)

```java
list.stream()
    .filter(s -> s.startsWith("a"))
    .map(String::toUpperCase)
    .forEach(System.out::println);
```
## Records (Java 16+)

```java
public record User(String name, int age) {}
// Automatically has constructor, getters, equals, hashCode, toString
```
## Pattern Matching (Java 17/21)

```java
if (obj instanceof String s) {
    System.out.println(s.length());
}

// Switch Expression
String type = switch (obj) {
    case Integer i -> "Number";
    case String s  -> "Text";
    default        -> "Unknown";
};
```
## String Blocks (Java 15+)

```java
String html = """
              <html>
                <body>
                  <p>Hello World</p>
                </body>
              </html>
              """;
```
## Useful Built-ins

- `String.isBlank()` / `String.repeat(n)`
- `Path.of("file.txt")` / `Files.readString(path)`
- `CompletableFuture.supplyAsync(() -> ...)`
- `Thread.ofVirtual().start(() -> ...)` (Java 21 Virtual Threads)


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
