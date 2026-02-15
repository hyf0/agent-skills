## Decision Framework

### Keep in SKILL.md When:

- Content is a workflow (sequential steps the agent always follows)
- Every invocation needs all the content
- The skill has a single concern

### Split to reference/ When:

- Content is a knowledge base (lookup tables, checklists, specs)
- Only some content is needed per invocation
- Content serves different purposes (workflow vs. reference data)

SKILL.md should stay under 500 lines. If it exceeds that, split reference material into `reference/` files.

## Reference File Guidelines

- **One topic per file** — each file should be self-contained and address a single concern
- **Kebab-case filenames** — e.g., `description-writing.md`, `quality-checklist.md`
- **One level deep only** — `reference/file.md`, never `reference/sub/file.md`
- **Self-contained** — a reference file should make sense without reading SKILL.md first

## Linking From SKILL.md

Use a consistent link format to point to reference files:

```markdown
-> See [display-name](reference/filename.md)
```

Place the link inline where the agent needs the information, not in a separate "References" section at the bottom.

## When to Merge Back

If a reference file is very short, consider inlining it back into SKILL.md. The overhead of a separate file may not be worth it for tiny content.

## Example Structure

Small skill (~60 lines total):
```
skills/my-skill/
└── SKILL.md          # Everything in one file
```

Medium skill (~250 lines total):
```
skills/my-skill/
├── SKILL.md          # Workflow (~100 lines)
└── reference/
    ├── spec.md       # Specification details (~80 lines)
    └── examples.md   # Input/output examples (~70 lines)
```

Large skill (~500+ lines total):
```
skills/my-skill/
├── SKILL.md          # Workflow + index (~120 lines)
└── reference/
    ├── patterns.md
    ├── checklist.md
    ├── examples.md
    └── anti-patterns.md
```
