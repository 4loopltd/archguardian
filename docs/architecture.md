# ArchGuardian Architecture

ArchGuardian introduces a new architectural layer in software development:  
a **per‑repository micro‑model** that evolves with your codebase.

This document describes the system architecture, model lifecycle, and integration points.

---

## High‑Level Components

- **Base Model (1–3B parameters)**  
  A small, efficient model suitable for LoRA fine‑tuning.

- **Training Corpus Builder**  
  Scans the repository and constructs a curated dataset.

- **LoRA Fine‑Tuning Pipeline**  
  Runs on PR merges to update the model incrementally.

- **Scheduled Rebuild Pipeline**  
  Re‑fine‑tunes the model from scratch to prevent drift.

- **MCP / API Interface**  
  Exposes architectural intelligence to any AI agent.

- **Model Storage**  
  Stored inside the repository for full transparency and versioning.

---

## Data Sources

- Source code
- Documentation
- PR descriptions
- Review comments
- Commit messages
- Architecture notes
- Dependency graphs

---

## Integration Points

- GitHub Actions
- GitHub PR lifecycle
- Copilot / IDE agents
- MCP‑compatible tools
- Local developer workflows

---

## Security Model

- No cross‑tenant training
- No centralised model hosting
- All training happens locally or on self‑hosted runners
- Full enterprise control of weights and data  
