# Installing Ollama

Guide to installing Ollama for running Large Language Models (LLMs) locally in 2026.

## 1. Local Installation (Linux - Recommended)

```bash
curl -fsSL https://ollama.com/install.sh | sh
```

## 2. Windows & macOS

- **macOS**: Download the `.zip` from [ollama.com](https://ollama.com/download/mac), extract, and run.
- **Windows**: Download the `.exe` from [ollama.com](https://ollama.com/download/windows) and follow the installer.

## 3. Docker Installation

Run Ollama inside a container with GPU support (requires NVIDIA Container Toolkit).

```bash
docker run -d --gpus=all -v ollama:/root/.ollama -p 11434:11434 --name ollama ollama/ollama
```

## Verifying Installation

```bash
ollama --version
```

## Hardware Requirements

| Model Size | RAM Recommendation |
| :--- | :--- |
| **7B Models** | 8GB RAM |
| **13B Models** | 16GB RAM |
| **33B Models** | 32GB RAM |
| **70B Models** | 64GB RAM |

> [!TIP]
> For best performance, ensure you have an NVIDIA GPU with at least 8GB VRAM (for 7B models) or an Apple Silicon Mac.


## Code Examples

### Quick run
```bash
ollama list
```
```bash
ollama run llama3.1 "Explain HTTP in 5 bullets"
```
