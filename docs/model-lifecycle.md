# The "Accepted Truth" Pipeline

## Ingestion
When a PR is merged, the system gathers:
- The code diff.
- The PR description and linked issues.
- Senior Reviewer comments (used as "positive/negative reinforcement" for training).

## Fine-Tuning (Incremental)
A LoRA pass updates the model. We use a high learning rate for specific new patterns but a low LoRA Alpha to prevent catastrophic forgetting.

## Snapshotting
The new `safetensors` file is versioned and committed back to Git.

## Full Rebuild (Weekly)
The model is retrained from a "clean" corpus of the entire repository to ensure the LoRA weights don't drift from the base model's logic.