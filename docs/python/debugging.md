# Debugging Python Applications

Tools and strategies for finding and fixing bugs in Python code.

## Using `breakpoint()`

The built-in `breakpoint()` function starts the PDB debugger.

```python
def my_function(x):
    y = x * 2
    breakpoint()  # Execution pauses here
    return y
```
## Logging over Printing

Use the `logging` module instead of `print()` for production-ready code.

```python
import logging

logging.basicConfig(level=logging.DEBUG)
logger = logging.getLogger(__name__)

logger.info("Application started")
logger.error("An error occurred")
```
## Common Errors

### 1. `ModuleNotFoundError`
- **Cause**: Package not installed in the current environment.
- **Fix**: Run `pip install <package>` or check your virtual environment.

### 2. `TypeError: 'NoneType' object is not subscriptable`
- **Cause**: Trying to access an index or key on a `None` variable.
- **Fix**: Check why the variable is `None` (usually a failed search or function return).

### 3. `IndentationError`
- **Cause**: Mixed tabs and spaces or incorrect indentation.
- **Fix**: Use a consistent 4-space indentation (standard in 2026).

## Profiling

```bash
# Profile script execution time
python -m cProfile -s time main.py
```
## Useful Tools

- **VS Code Debugger**: Integrated UI for breakpoints and variable inspection.
- **Pytest**: For unit and integration testing.
- **Sentry**: For error tracking in production.


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
