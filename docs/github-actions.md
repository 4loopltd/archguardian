# GitHub Actions Integration

ArchGuardian relies on GitHub Actions for:

- LoRA updates on PR merge
- Scheduled rebuilds
- Model artifact storage

---

## PR Merge Workflow

Triggered on `pull_request` with `merged == true`.

Steps:

1. Checkout repo
2. Load base model + current adapters
3. Extract PR diff and metadata
4. Run LoRA fine‑tune
5. Save updated adapters

---

## Scheduled Rebuild Workflow

Triggered nightly or weekly.

Steps:

1. Checkout repo
2. Rebuild training corpus
3. Fine‑tune from base checkpoint
4. Replace adapters
5. Commit or upload artifacts  
