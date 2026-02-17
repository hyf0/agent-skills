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
| `metadata` | Arbitrary key-value pairs | `author`, `version`, `mcp-server`, `category`, `tags` |
| `compatibility` | Environment requirements | 1-500 chars, e.g., "Requires Node.js 18+" |

## Claude Code Extensions

These fields are specific to Claude Code. Other agents may ignore them.

| Field | Purpose | Format |
|-------|---------|--------|
| `allowed-tools` | Tools the skill can use | Space-separated: `"Bash(python:*) Bash(npm:*) WebFetch"` |
| `disable-model-invocation` | Only user can trigger (slash command only) | Boolean |
| `user-invocable` | Creates a background skill when `false` — hidden from `/` menu, description always loaded into context, only Claude can invoke it | Boolean, set to `false` |
| `context` | Execution context | `fork` for isolated subagent |
| `argument-hint` | Autocomplete hint for slash commands | e.g., `[file-path]` |
| `model` | Force a specific model | Model identifier string |

## Background Skills

Set `user-invocable: false` to create a background skill. Background skills are hidden from the `/` menu and cannot be triggered by the user directly. Their description is always loaded into context, so Claude can decide when to invoke them.

Use background skills for knowledge that should always be available but users shouldn't invoke directly — e.g., coding standards, review checklists, or context that informs other skills.

## Validation Checklist

- [ ] YAML has `---` delimiters on both sides
- [ ] `name` is kebab-case and matches the folder name
- [ ] `description` is under 1024 characters
- [ ] No XML angle brackets (`<` or `>`) in any field value
- [ ] No agent-specific terms in description
- [ ] `allowed-tools` only present if the skill actually runs commands
- [ ] String values with special characters are quoted
