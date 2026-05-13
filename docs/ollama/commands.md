# Ollama CLI Commands

Essential commands for managing and interacting with local LLMs.

## Model Management

| Action | Command |
| :--- | :--- |
| **List models** | `ollama list` |
| **Pull a model** | `ollama pull <model>` |
| **Run a model** | `ollama run <model>` |
| **Remove a model**| `ollama rm <model>` |
| **Copy a model** | `ollama cp <src> <dest>` |
| **Show model info**| `ollama show <model>` |

## System Commands

```bash
ollama serve     # Start the Ollama server manually
```
```bash
ollama --version  # Show version
```

## Interactive Chat Shortcuts

Inside the `ollama run` session:
- `/set parameter <key> <value>`: Change model parameters on the fly.
- `/show info`: Show details about the current model.
- `/bye`: Exit the chat.
- `/?`: Show help.

## API Usage (CURL)

Ollama provides a REST API on port 11434.

```bash
curl http://localhost:11434/api/generate -d '{
```
```bash
"model": "llama3",
```
```bash
"prompt": "Why is the sky blue?"
```
```bash
}'
```

## Useful CLI Shortcuts

- `ollama ps`: Show which models are currently loaded into memory.
- `ollama run <model> --verbose`: Show generation statistics (tokens/s).


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
