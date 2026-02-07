# Model Lifecycle

ArchGuardian models evolve continuously with the repository.  
This document describes the full lifecycle.

---

## 1. Initial Fine‑Tune

A GitHub Action or local script:

- Scans the entire repository
- Builds a training corpus
- Fine‑tunes the base model
- Saves the initial LoRA adapters

---

## 2. LoRA Updates on PR Merge

Triggered by a GitHub Action:

- Load current model + adapters
- Extract:
    - Diff
    - Surrounding context
    - PR description
    - Review comments
- Run LoRA fine‑tune
- Save updated adapters

---

## 3. Scheduled Rebuild

Nightly or weekly:

- Rebuild training corpus
- Re‑fine‑tune from base checkpoint
- Archive old adapters
- Replace with fresh adapters

---

## 4. Inference

Agents query the model via MCP/API:

- Pattern detection
- Impact analysis
- Architectural linting
- Canonical guidance  
