## Content Anti-Patterns

- **Teaching basics the agent already knows** — Do not explain how to write JavaScript, use git, parse JSON, or other general programming knowledge. The agent already knows this. Only include domain-specific knowledge it lacks.
- **Wall of text** — Long unstructured paragraphs are hard for the agent to parse. Use headers, bullet points, numbered steps, and tables instead.
- **Voodoo constants** — Magic numbers or thresholds without explanation. If you specify a limit (e.g., "max 3 retries"), explain why that number was chosen, or remove it if it is arbitrary.
- **Time-sensitive information** — Version numbers, URLs, API endpoints, or release dates that will become stale. If the skill needs version info, instruct the agent to check at runtime.
- **Inconsistent terminology** — Using "component", "module", and "widget" interchangeably for the same concept. Pick one term and use it everywhere.

## Structure Anti-Patterns

- **Deep nesting** — Reference files nested more than one level (`reference/sub/file.md`). Keep everything at `reference/file.md`.
- **No cross-references** — SKILL.md mentions concepts detailed in reference files but does not link to them. Always link with `-> See [name](reference/file.md)`.
- **Monolithic reference files** — A single 300-line reference file covering multiple unrelated topics. Split into focused, single-topic files.
- **Extraneous documentation files** — Do not create README.md, CHANGELOG.md, INSTALLATION_GUIDE.md, or similar inside the skill folder. The skill should only contain what the agent needs: SKILL.md, scripts/, references/, and assets/.

## Description Anti-Patterns

- **Missing trigger conditions** — Description says what the skill does but not when to use it. Always include "Use when..." or equivalent.
- **First/second person** — "I analyze..." or "You can use this to..." — always use third person: "Analyzes..."
- **Too generic** — "Helps with development tasks" matches everything and is therefore useless for invocation matching.
- **Too technical for discovery** — Using internal jargon that users would never type. Include the words users actually say.

## Workflow Anti-Patterns

- **No validation step** — The workflow produces output but never checks if it is correct. Always include a validation or quality check step.
- **No feedback loop** — For critical operations (destructive changes, external API calls), the workflow should report what it intends to do and get confirmation before proceeding.
- **Punting to the agent** — "Use your best judgment to handle errors" is not a strategy. Provide explicit error handling instructions or fallback steps.
- **Missing task list** — Workflows with 3+ steps that do not include a copyable checklist. Without a checklist, the agent may skip steps or lose track of progress.
