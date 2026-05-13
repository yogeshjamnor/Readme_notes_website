# Python CLI Commands

Essential commands for Python development and package management.

## Running Python Scripts

```bash
# Basic run
python main.py

# Run as module
python -m my_module.main

# Run with interactive shell
python -i main.py
```
## Package Management (pip)

| Action | Command |
| :--- | :--- |
| **Install pkg** | `pip install <pkg>` |
| **Install from file**| `pip install -r requirements.txt` |
| **Freeze deps** | `pip freeze > requirements.txt` |
| **Uninstall pkg** | `pip uninstall <pkg>` |
| **Show pkg info** | `pip show <pkg>` |

## Modern Tools (uv / poetry)

```bash
# Using uv (Fast)
uv pip install -r requirements.txt
uv run main.py

# Using poetry
poetry add <pkg>
poetry run python main.py
```
## Testing & Linting

```bash
# Run tests
pytest

# Run tests with coverage
pytest --cov=app

# Run linting (Ruff)
ruff check .

# Fix linting issues
ruff check --fix .
```
## Useful CLI Shortcuts

- `python -m http.server 8000`: Start a quick static file server.
- `pip list --outdated`: Show packages that need updates.
- `python -m json.tool`: Pretty print JSON from stdin.


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
