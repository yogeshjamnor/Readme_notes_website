# Ollama Security Considerations

Guidelines for running local LLMs securely with Ollama.

## 1. Network Access
- [ ] **Default Host**: By default, Ollama binds to `127.0.0.1`. Do not change this to `0.0.0.0` unless you have a firewall in place.
- [ ] **Firewall**: If exposing Ollama to a network, restrict access to port `11434` to specific internal IPs.

## 2. Authentication
- [ ] **No Built-in Auth**: Ollama does not have built-in authentication. Always use a reverse proxy (Nginx, Apache) with Basic Auth or OIDC if exposed.

## 3. Container Security (if using Docker)
- [ ] **GPU Access**: Be cautious when granting full GPU access to containers.
- [ ] **Resource Limits**: Limit the container's memory and CPU to prevent a rogue model from crashing the host.

## 4. Model Safety
- [ ] **Trusted Models**: Only download models from the official Ollama library or trusted creators.
- [ ] **Prompt Injection**: Be aware that LLMs are susceptible to prompt injection. Validate and sanitize inputs in your application layer.

## 5. Privacy
- [ ] **Local Data**: The main security advantage of Ollama is that data stays local. Ensure your logs and model weights are stored on an encrypted partition if they contain sensitive info.

## 6. Secure Deployment Snippet (Nginx + Basic Auth)
```nginx
location / {
    proxy_pass http://localhost:11434;
    auth_basic "Restricted Access";
    auth_basic_user_file /etc/nginx/.htpasswd;
}
```

> [!IMPORTANT]
> Ollama is designed for local developer use. If you intend to use it as a production API, you MUST wrap it in a secure application layer with proper auth and rate limiting.


## Code Examples

### Quick run
```bash
ollama list
```
```bash
ollama run llama3.1 "Explain HTTP in 5 bullets"
```


## Extra security notes (copy‑ready)

### Treat prompts as untrusted input
- Do not include secrets in prompts
- Log redaction: strip tokens/keys before saving logs

### Network exposure
- Bind to localhost unless you really need remote access


> [!TIP]
> Use the **Copy** button in the top-right of code blocks to quickly copy commands to your clipboard.
