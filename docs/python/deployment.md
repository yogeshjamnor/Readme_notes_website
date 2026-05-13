# Python Deployment Guide

Deploying Python applications to production environments.

## Production WSGI/ASGI Servers

Python applications should never be served using the built-in development server (like `app.run()` in Flask).

| Framework | Server | Command |
| :--- | :--- | :--- |
| **Flask/Django** | Gunicorn | `gunicorn --workers 3 app:app` |
| **FastAPI** | Uvicorn | `uvicorn main:app --host 0.0.0.0 --port 80` |
| **Generic** | Waitress | `waitress-serve --port=8080 myapp:app` |

## Environment Isolation (Docker)

Example `Dockerfile` for a Python app:

```dockerfile
FROM python:3.12-slim
WORKDIR /app
COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt
COPY . .
EXPOSE 8000
CMD ["gunicorn", "-b", "0.0.0.0:8000", "main:app"]
```
## Hosting Options

- **PaaS**: Railway, Render, Fly.io (Easy setup).
- **Serverless**: AWS Lambda (using Mangum for FastAPI), Google Cloud Functions.
- **VPS**: DigitalOcean/AWS EC2 with Nginx + Gunicorn + Systemd.

## Performance Tuning

1.  **Workers**: Usually `(2 x $num_cores) + 1`.
2.  **Statelessness**: Ensure the app is stateless for easy scaling.
3.  **Caching**: Use Redis for frequently accessed data.
4.  **Database Pooling**: Use connection pooling (e.g., SQLAlchemy `QueuePool`).


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
