# CTF Solver Agent Sandbox Template

This template provides a pre-configured environment with essential CTF tools, enabling an AI agent (or human) to solve challenges securely and efficiently.

## Included Tools

- **System Tools**: `build-essential`, `gdb`, `ltrace`, `strace`, `netcat`, `socat`, `curl`, `wget`, `nmap`
- **Editors**: `vim`, `nano`
- **Analysis Tools**: `file`, `unzip`, `binutils`, `checksec`, `radare2`
- **Python Libraries**: `pwntools`, `r2pipe`, `requests`, `scapy`, `angr`
- **Debugging**: `gef` (GDB Enhanced Features)

## Usage

### Building the Template

You can build this template locally:

```bash
docker build -t ctf-solver .
```

### Running a Sandbox

To create a new sandbox using this template:

```bash
docker sandbox run --load-local-template -t ctf-solver gemini
```

### Network Access

The CTF tools in this template (like `nc`, `curl`, `requests`) require network access. By default, newer Docker Sandbox versions may restrict this.

You can enable network access for the sandbox. Attempt to use a startup flag if available (e.g., `--policy allow`), or configure it immediately after creation:

```bash
# Allow all network access (recommended for CTF solving)
# Replace <sandbox-name> with your actual sandbox name (check with `docker sandbox ls`)
docker sandbox network proxy <sandbox-name> --policy allow

# If network access still fails, try restarting the sandbox:
# docker sandbox stop <sandbox-name>
# docker sandbox run <sandbox-name>
```
