# Debugging Ollama

Troubleshooting issues with local model execution.

## Checking Logs (Linux)

```bash
journalctl -u ollama --no-pager | tail -n 50
```

## Common Errors

### 1. `Error: nvidia-container-cli: initialization error`
- **Cause**: NVIDIA Container Toolkit not installed or misconfigured.
- **Fix**: Install the toolkit and restart Docker.

### 2. `Model not found`
- **Cause**: Typo in model name or model not pulled yet.
- **Fix**: Run `ollama pull <model>` and check `ollama list`.

### 3. `OutOfMemoryError` (GPU)
- **Cause**: Model is too large for your VRAM.
- **Fix**: Use a smaller quantization (e.g., `q4_K_M`) or a smaller parameter model (7B instead of 70B).

### 4. `Connection refused`
- **Cause**: Ollama server not running.
- **Fix**: `systemctl start ollama` or check if port 11434 is blocked.

## Performance Profiling

If generation is slow:
1.  Check `htop` to see if CPU is pegged (meaning it's not using GPU).
2.  Check `nvidia-smi` to see if VRAM is being used.
3.  Reduce the number of parallel requests if `OLLAMA_NUM_PARALLEL` is set too high.

## Network Issues

If you can't access Ollama from another machine:
- Verify `OLLAMA_HOST` is set to `0.0.0.0`.
- Verify the firewall allows inbound traffic on port `11434`.


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
