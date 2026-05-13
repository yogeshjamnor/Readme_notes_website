# Ollama Setup & Configuration

Configuring Ollama for optimal local LLM performance.

## 1. Running your first model

```bash
ollama run llama3.2 # Run the latest Llama model
```

## 2. Environment Variables

Ollama can be configured via environment variables.

- **OLLAMA_HOST**: The address to bind to (Default: `127.0.0.1:11434`). Set to `0.0.0.0` for remote access.
- **OLLAMA_MODELS**: Path to store model weights.
- **OLLAMA_NUM_PARALLEL**: Number of parallel requests to handle.

Edit your system environment or systemd service file:
```bash
# Example for Linux systemd
```
```bash
# sudo systemctl edit ollama.service
```
```bash
[Service]
```
```bash
Environment="OLLAMA_HOST=0.0.0.0"
```

## 3. Creating Custom Models (Modelfile)

Create a file named `Modelfile`:
```text
FROM llama3
# Set the temperature (higher is more creative, lower is more coherent)
PARAMETER temperature 1
# Set the system prompt
SYSTEM """
You are a helpful coding assistant that follows premium design standards.
"""
```

Then create the model:
```bash
ollama create my-coding-assistant -f Modelfile
```

## 4. UI Integrations

To get a ChatGPT-like experience, use a web UI:
- **Open WebUI**: (Formerly Ollama WebUI) Feature-rich Docker-based UI.
- **Enchanted**: Native macOS client.
- **Page Assist**: Browser extension for Ollama.

> [!IMPORTANT]
> If you expose Ollama to the network (`0.0.0.0`), ensure you use a firewall to restrict access, as it does not have built-in authentication.


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
