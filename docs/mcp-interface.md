# Standardizing the Architectural Query

ArchGuardian exposes its specialized knowledge through the Model Context Protocol (MCP). This allows IDEs to treat the repository's "brain" as a first-class tool.

## Example Tool Definition (JSON-RPC)

```json
{
  "name": "verify_compliance",
  "description": "Checks code for architectural drift against the project model.",
  "inputSchema": {
    "type": "object",
    "properties": {
      "file_path": { "type": "string" },
      "content": { "type": "string" }
    },
    "required": ["content"]
  }
}
```

## Core Tools

- `check_architectural_fit`: Analyzes a code snippet for violations of learned patterns.
- `get_canonical_example`: Retrieves the most "successful" implementation of a pattern (e.g., "How do we handle state transitions in this repo?").
- `analyze_impact`: Predicts which modules will be affected by a change based on historical merge data.