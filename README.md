<p align="center">
  <img src="https://img.shields.io/badge/FableForge_CLI-0.1.0-blue?style=for-the-badge&logo=terminal&logoColor=white" alt="CLI Version"/>
  <img src="https://img.shields.io/badge/python-3.10%2B-blue?style=for-the-badge" alt="Python"/>
  <img src="https://img.shields.io/badge/license-MIT-yellow?style=for-the-badge" alt="License"/>
</p>

<h1 align="center">⚡ FableForge CLI</h1>

<p align="center"><em>One command to install, run, and manage the entire FableForge agent ecosystem.</em></p>

---

## Install

```bash
pip install fableforge
```

> **Note:** The PyPI package name is `fableforge` — this repo is `fableforge-cli`.

## Commands

```bash
# Show available commands
fableforge --help

# Show version
fableforge --version

# Run the Anvil agent
fableforge anvil "Fix the auth bug in src/auth.py"

# Run Anvil with verification
fableforge anvil --verify "Refactor the database layer"

# Run shell commands with ShellWhisperer
fableforge shell "find all Python files with TODO comments"

# Verify code with ReasonCritic
fableforge verify src/main.py

# Run the full agent swarm
fableforge swarm --agents 3 "Build the REST API"

# Profile agent performance
fableforge profile --last-run

# Fuzz test an agent
fableforge fuzz --target my-agent

# Benchmark agents
fableforge bench --suite standard

# View telemetry dashboard
fableforge telemetry dashboard
```

## Architecture

The CLI is built with [Click](https://click.palletsprojects.com/) and integrates all FableForge components:

```
fableforge (CLI)
├── anvil      → fableforge-anvil-agent (flagship agent)
├── shell      → fableforge-shell-whisperer (shell model)
├── verify     → reason-critic (verification model)
├── swarm      → fableforge-agent-swarm (multi-agent)
├── profile    → fableforge-agent-profiler (profiling)
├── fuzz       → agent-fuzzer (adversarial testing)
├── bench      → fableforge-bench-agent (benchmarking)
└── telemetry  → fableforge-agent-telemetry (observability)
```

## Configuration

Create `fableforge.toml` in your project root:

```toml
[anvil]
model = "gpt-4"
verifier = "reason-critic"
max_retries = 3

[swarm]
default_agents = 3
timeout = 300

[telemetry]
enabled = true
endpoint = "http://localhost:4317"
```

## Environment Variables

| Variable | Default | Description |
|----------|---------|-------------|
| `FABLEFORGE_MODEL` | `gpt-4` | Default LLM model |
| `FABLEFORGE_VERIFIER` | `reason-critic` | Verification model |
| `FABLEFORGE_TELEMETRY` | `true` | Enable telemetry |
| `OPENAI_API_KEY` | — | OpenAI API key |

## Ecosystem

Part of the **FableForge** ecosystem — 21 open-source projects:

<p align="center">
  <a href="https://kinglabsa.github.io/fableforge/">🌐 Website</a> · 
  <a href="https://pypi.org/project/fableforge/">📦 PyPI</a> · 
  <a href="https://github.com/KingLabsA/fableforge-cli">📂 Source</a>
</p>

## License

MIT © [KingLabs](https://github.com/KingLabsA)
