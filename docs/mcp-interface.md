# MCP Interface Specification

ArchGuardian exposes a clean interface for AI agents.

---

## Methods

### `get_architecture_summary()`
Returns a high‑level overview of the project’s architecture.

### `find_pattern(pattern: string)`
Returns locations and explanations of how a pattern is implemented.

### `impact_analysis(symbol: string)`
Returns modules, files, and tests affected by a change.

### `suggest_canonical_implementation(feature: string)`
Returns the canonical pattern used in the repo.

### `lint_architecture(diff: string)`
Returns warnings and suggestions for architectural consistency.

---

## Response Format

All responses include:

- Summary
- Detailed findings
- Confidence score
- References to files/lines  
