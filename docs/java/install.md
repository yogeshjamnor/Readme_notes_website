# Installing Java

Guide to installing the Java Development Kit (JDK) in 2026.

## Using SDKMAN! (Recommended)

SDKMAN! is the easiest way to manage multiple Java versions on Unix-like systems.

```bash
# Install SDKMAN!
curl -s "https://get.sdkman.io" | bash
source "$HOME/.sdkman/bin/sdkman-init.sh"

# Install latest LTS JDK (e.g., Temurin 21)
sdk install java 21.0.2-tem

# Set as default
sdk default java 21.0.2-tem
```
## Direct Installation

- **Windows**: Download the `.msi` or `.zip` from [Adoptium](https://adoptium.net/).
- **macOS**: `brew install openjdk@21`
- **Linux (Ubuntu)**:
  ```bash
  sudo apt update
  sudo apt install openjdk-21-jdk
  ```

## Verifying Installation

```bash
java -version
javac -version
```
## Build Tools

| Tool | Purpose |
| :--- | :--- |
| **Maven** | Standard project management and comprehension tool |
| **Gradle** | Modern, flexible build automation |
| **JBang** | Run Java like a script |

> [!TIP]
> Use `SDKMAN!` to switch between different JDK distributions (Oracle, GraalVM, Amazon Corretto) seamlessly.


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