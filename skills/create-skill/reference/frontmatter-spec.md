## Impact

Frontmatter errors are silent failures — the skill simply never loads. Every field has constraints that must be followed exactly.

## YAML Template

```yaml
---
name: my-skill-name
description: Does X in third person. Use when Y happens or user asks for Z.
license: MIT
allowed-tools: "Bash(python:*) WebFetch"
metadata:
  author: github.com/username
  version: "1.0.0"
  category: workflow
  tags: [scaffolding, automation]
---
```

## Required Fields

| Field | Constraints |
|-------|------------|
| `name` | Kebab-case, max 64 chars, must match folder name exactly |
| `description` | Max 1024 chars, third person, no XML angle brackets, no agent-specific terms |

## Optional Fields

| Field | Purpose | Format |
|-------|---------|--------|
| `license` | License identifier | e.g., `MIT`, `Apache-2.0` |
| `allowed-tools` | Tools the skill can use | Space-separated: `"Bash(python:*) Bash(npm:*) WebFetch"` |
| `metadata` | Arbitrary key-value pairs | `author`, `version`, `mcp-server`, `category`, `tags` |
| `compatibility` | Environment requirements | 1-500 chars, e.g., "Requires Node.js 18+" |
| `disable-model-invocation` | Only user can trigger (slash command only) | Boolean |
| `user-invocable` | Only the agent can trigger (not a slash command) | Boolean, set to `false` |
| `context` | Execution context | `fork` for isolated subagent |
| `argument-hint` | Autocomplete hint for slash commands | e.g., `[file-path]` |
| `model` | Force a specific model | Model identifier string |

## Validation Checklist

- [ ] YAML has `---` delimiters on both sides
- [ ] `name` is kebab-case and matches the folder name
- [ ] `description` is under 1024 characters
- [ ] No XML angle brackets (`<` or `>`) in any field value
- [ ] No agent-specific terms in description
- [ ] `allowed-tools` only present if the skill actually runs commands
- [ ] String values with special characters are quoted
