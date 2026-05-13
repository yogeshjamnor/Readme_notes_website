# Installing Python

Guide to installing Python and managing environments in 2026.

## Using pyenv (Recommended)

Manage multiple Python versions easily.

```bash
# Install pyenv (Linux/macOS)
curl https://pyenv.run | bash

# Install specific Python version
pyenv install 3.12 # Latest stable

# Set local version
pyenv local 3.12
```
## Direct Installation

- **Windows**: Download from [python.org](https://www.python.org/downloads/). Ensure "Add Python to PATH" is checked.
- **macOS**: `brew install python`
- **Linux (Ubuntu)**:
  ```bash
  sudo apt update
  sudo apt install python3 python3-pip
  ```

## Package Managers

| Tool | Purpose |
| :--- | :--- |
| **pip** | Standard package installer |
| **poetry** | Dependency management & packaging (Recommended) |
| **uv** | Extremely fast Rust-based package manager |
| **conda** | Scientific computing and environment management |

## Verifying Installation

```bash
python --version
pip --version
```
> [!TIP]
> Use `uv` for 10-100x faster package installation compared to `pip`.


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