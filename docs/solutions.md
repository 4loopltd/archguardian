# ArchGuardian: The Learned Guardrail

ArchGuardian moves AI from an Autocomplete tool to an Architectural Guardian.

## Micro-Model Specialization
Instead of high-latency generalist models, we use 1B–3B parameter models (e.g., Llama-3.2 or Qwen-2.5) that are small enough to run on standard CI/CD runners but optimized for repo-specific syntax.

## LoRA as Permanent Memory
We store "learned" architectural patterns as Low-Rank Adaptation (LoRA) weights in the `.project-model/` directory. These weights act as a versioned, specialized brain for your specific codebase.

## The Validation Loop
ArchGuardian only learns from merged PRs. This creates a "filtered truth" pipeline where the model only internalizes patterns that have already survived human review and QA.

## Agent-Native Interface
By exposing these patterns via the Model Context Protocol (MCP), any agent (Cursor, Windsurf, Copilot) can query the "canonical" way to build a feature in your specific repo.