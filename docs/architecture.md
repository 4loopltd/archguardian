# The Guardian Stack

ArchGuardian is composed of three decoupled layers:

## The Weights Store (`.project-model/`)

- `adapter_config.json`: LoRA configuration (rank, alpha, target modules).
- `adapter_model.safetensors`: The learned weights (~50MB - 150MB).
- `manifest.yaml`: Human-in-the-loop configuration for mandatory rules.

## The Trainer Engine

- A Python-based utility using the Unsloth library for high-speed, 4-bit fine-tuning.
- Designed to run on a GitHub Actions T4 GPU or self-hosted runner.

## The MCP Server

- A Node.js or Python server that mounts the `.project-model/` weights.
- Implements the `tools/call` and `resources/read` methods for architectural validation.