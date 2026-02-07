# CI/CD Implementation

ArchGuardian uses a Merge-Triggered Learning workflow.

```yaml
name: ArchGuardian Learning Loop
on:
  pull_request:
    types: [closed]
    branches: [main]

jobs:
  fine-tune:
    if: github.event.pull_request.merged == true
    runs-on: self-hosted-gpu # Requires at least 16GB VRAM for 3B model fine-tuning
    steps:
      - uses: actions/checkout@v4
      - name: Update Guardian Weights
        run: |
          # The trainer extracts PR meta and merges it into the LoRA
          python -m archguardian.trainer \
            --pr_id ${{ github.event.pull_request.number }} \
            --model_dir "./.project-model/weights"
      - name: Commit Pattern Update
        run: |
          git add ./.project-model/weights
          git commit -m "chore: archguardian learned new patterns from PR #${{ github.event.number }}"
          git push
```