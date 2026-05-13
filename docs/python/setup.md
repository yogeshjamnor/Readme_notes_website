# Python Project Setup

Setting up virtual environments and project structures.

## Virtual Environments

Always use a virtual environment to isolate dependencies.

### 1. Using `venv` (Built-in)
```bash
# Create environment
python -m venv .venv

# Activate (Linux/macOS)
source .venv/bin/activate

# Activate (Windows)
.venv\Scripts\activate
```
### 2. Using `poetry` (Modern)
```bash
poetry init
poetry install
poetry shell
```
## Recommended Folder Structure

```text
my_project/
├── app/
│   ├── __init__.py
│   ├── main.py        # Entry point
│   ├── models.py      # Data models
│   ├── routes.py      # API routes
│   └── utils.py       # Helpers
├── tests/             # Pytest files
├── .env               # Environment variables
├── .gitignore
├── README.md
├── pyproject.toml     # Modern config
└── requirements.txt   # Legacy config
```
## Environment Variables

Use `python-dotenv` to load variables.

```env
# .env
DATABASE_URL=postgresql://user:pass@localhost:5432/db
API_KEY=your_secret_key
DEBUG=True
```
```python
from dotenv import load_dotenv
import os

load_dotenv()
db_url = os.getenv("DATABASE_URL")
```
## Best Practices

1.  **Type Hinting**: Use Python 3.10+ type hints.
2.  **Linting**: Use `ruff` for extremely fast linting and formatting.
3.  **Docstrings**: Follow Google or NumPy style for documentation.
4.  **Testing**: Use `pytest` for all testing needs.


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
