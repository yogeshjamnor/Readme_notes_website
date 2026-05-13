# Ollama Cheatsheet

Quick reference for Ollama commands and parameters.

## Core Commands

```bash
ollama run <model>     # Start chat
```
```bash
ollama pull <model>    # Download model
```
```bash
ollama list            # Show downloaded models
```
```bash
ollama ps              # Show running models
```
```bash
ollama rm <model>      # Delete model
```
```bash
ollama show <model>    # Detailed info
```

## Modelfile Parameters

| Parameter | Default | Description |
| :--- | :--- | :--- |
| `temperature` | 0.8 | Higher = more creative |
| `num_ctx` | 2048 | Context window size |
| `top_k` | 40 | Sample from top K tokens |
| `top_p` | 0.9 | Nucleus sampling probability |
| `stop` | [none] | Stop generation at this token |

## Popular Models (2026)

- `llama3.2`: Latest Meta model.
- `mistral`: High-performance small model.
- `phi3`: Microsoft's tiny but powerful model.
- `codellama`: Specialized for coding.
- `starcoder2`: Efficient for multiple programming languages.

## API Endpoint Quick Ref

- `POST /api/generate`: Generate a response.
- `POST /api/chat`: Send a chat message history.
- `GET /api/tags`: List local models.
- `POST /api/pull`: Download a model via API.

## Environment Variables

- `OLLAMA_HOST`: Address to bind server.
- `OLLAMA_MODELS`: Model storage directory.
- `OLLAMA_KEEP_ALIVE`: How long to keep model in memory (e.g., `5m`).


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
