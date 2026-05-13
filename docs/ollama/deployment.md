# Ollama Deployment

Deploying Ollama as a shared inference server.

## 1. Network Access

To allow other machines to access your Ollama server:

1.  Set `OLLAMA_HOST=0.0.0.0` in your environment.
2.  Restart the Ollama service.
3.  Open port `11434` in your firewall.

## 2. Reverse Proxy (Nginx)

Add basic authentication to Ollama since it has none by default.

```nginx
server {
    listen 80;
    server_name ollama.example.com;

    location / {
        proxy_pass http://localhost:11434;
        auth_basic "Restricted Access";
        auth_basic_user_file /etc/nginx/.htpasswd;
    }
}
```

## 3. Docker Compose (Ollama + Web UI)

```yaml
services:
  ollama:
    image: ollama/ollama
    volumes:
      - ./ollama_data:/root/.ollama
    ports:
      - "11434:11434"
    deploy:
      resources:
        reservations:
          devices:
            - driver: nvidia
              count: all
              capabilities: [gpu]

  open-webui:
    image: ghcr.io/open-webui/open-webui:main
    ports:
      - "3000:8080"
    environment:
      - OLLAMA_BASE_URL=http://ollama:11434
    depends_on:
      - ollama
```

## 4. Production Checklist

- [ ] **GPU Drivers**: Ensure latest NVIDIA drivers and Container Toolkit are installed.
- [ ] **Storage**: Model weights are large; ensure you have 100GB+ free space.
- [ ] **Concurrency**: Tuning `OLLAMA_NUM_PARALLEL` for multiple users.
- [ ] **Logging**: Monitor system resource usage with `nvidia-smi` or `htop`.


## Code Examples

### Quick run
```bash
ollama list
```
```bash
ollama run llama3.1 "Explain HTTP in 5 bullets"
```


> [!TIP]
> Use the **Copy** button in the top-right of code blocks to quickly copy commands to your clipboard.
