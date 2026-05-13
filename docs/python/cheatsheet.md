# Python 3.12+ Cheatsheet

Quick reference for Python syntax and common libraries.

## Lists and Dictionaries

```python
# Lists
items = [1, 2, 3]
items.append(4)
evens = [x for x in items if x % 2 == 0] # List comprehension

# Dictionaries
user = {"name": "Alice", "age": 30}
name = user.get("name", "Unknown")
```
## Function Definitions

```python
def greet(name: str, age: int = 25) -> str:
    """Greets a user."""
    return f"Hello {name}, you are {age} years old."
```
## Classes (Data Classes)

```python
from dataclasses import dataclass

@dataclass
class Point:
    x: int
    y: int
```
## Context Managers

```python
with open("file.txt", "r") as f:
    content = f.read()
```
## Async Programming

```python
import asyncio

async def main():
    print("Hello")
    await asyncio.sleep(1)
    print("World")

asyncio.run(main())
```
## String Formatting

```python
name = "World"
print(f"Hello, {name}!") # F-strings
```
## Useful Built-ins

- `len(obj)`: Length.
- `type(obj)`: Object type.
- `dir(obj)`: List attributes/methods.
- `enumerate(list)`: Index and value.
- `zip(list1, list2)`: Combine lists.


## Code Examples

### Virtualenv + quick run
```bash
python -m venv .venv
source .venv/bin/activate
python -m pip install -U pip
python -c "print('ready')"
```
### Robust file reading
```python
from pathlib import Path

def read_text(path: str) -> str:
    return Path(path).read_text(encoding="utf-8")
```
> [!TIP]
> Use the **Copy** button in the top-right of code blocks to quickly copy commands to your clipboard.
