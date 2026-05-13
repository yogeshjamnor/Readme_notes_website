# Python Security Best Practices

Guidelines for writing secure Python code and managing environments.

## 1. Dependency Security
- [ ] **pip audit**: Check for vulnerabilities in `requirements.txt` or `pyproject.toml`.
- [ ] **Snyk**: Automated dependency scanning.
- [ ] **Safety**: Check installed packages against known vulnerabilities.

## 2. Web Security (Flask/Django/FastAPI)
- [ ] **SQL Injection**: Always use ORMs like SQLAlchemy or Django ORM instead of raw string formatting for queries.
- [ ] **XSS**: Use template engines like Jinja2 (it auto-escapes by default).
- [ ] **CSRF**: Enable CSRF protection in your web framework.

## 3. Code Hardening
- [ ] **Avoid `eval()` and `exec()`**: They are extremely dangerous with user-provided input.
- [ ] **Secure Deserialization**: Avoid `pickle` for untrusted data; use `json` instead.
- [ ] **Safe Subprocesses**: Use `subprocess.run(args, shell=False)`.

## 4. Environment & Secrets
- [ ] **Environment Variables**: Use `python-dotenv`.
- [ ] **Secrets Module**: Use the `secrets` module for generating cryptographically strong tokens/passwords.

## 5. Security Tools
| Tool | Purpose |
| :--- | :--- |
| **Bandit** | Static analysis tool to find common security issues |
| **Ruff** | Includes security linting rules |
| **pip-audit** | Vulnerability scanning for packages |
| **Safety** | CLI tool for scanning dependencies |

## 6. Static Analysis Example (Bandit)
```bash
pip install bandit
bandit -r app/
```
> [!IMPORTANT]
> Always use `shell=False` when using the `subprocess` module to prevent shell injection attacks.


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
## Extra security notes (copy‑ready)

### Dependency scanning
- Keep dependencies updated
- Use the ecosystem scanner (`npm audit`, `pip-audit`, etc.)

### Secrets hygiene
- Do not commit `.env` / private keys
- Rotate leaked keys immediately


> [!TIP]
> Use the **Copy** button in the top-right of code blocks to quickly copy commands to your clipboard.
