## Impact

The description field is the single highest-impact part of a skill. A poor description is the most common reason a skill fails to be invoked. A well-written description makes the difference between a skill that works and one that is never triggered.

## The "What + When" Formula

Every description must answer two questions:

```
[What it does in third person]. [When to use it / trigger conditions].
```

## Rules

1. **Third person only** — "Creates...", "Analyzes...", "Generates..." — never "I create" or "You can use this to"
2. **Include key trigger terms** — Use specific tasks and phrases a user would actually say. Mention file types, tool names, and domain terms relevant to the skill
3. **Max 1024 characters** — Be concise but complete
4. **No XML angle brackets** — Never use `<` or `>` in the description
5. **No agent-specific terms** — Do not mention specific agent names
6. **Add negative triggers for scope control** — "Do NOT use for X" prevents over-triggering on similar but unrelated tasks

## Examples

### Incorrect

```
A skill for helping with code stuff.
```
Problem: Too vague, no trigger conditions, no specific actions.

```
I will help you create Vue components with proper TypeScript types and testing.
```
Problem: First person ("I will"), missing trigger conditions.

```
Use this skill when you want to review pull requests and provide feedback on code quality, security, and performance.
```
Problem: Second person ("you want"), description should state what the skill does first.

### Correct

```
Creates a new agent skill following best practices for structure, description writing, and progressive disclosure. Use when the user wants to author a new SKILL.md, scaffold a skill directory, or build a reusable skill.
```
Why it works: Third person ("Creates"), clear what it does, specific trigger conditions ("author a new SKILL.md", "scaffold", "build a reusable skill").

```
Reviews pull requests for code quality, security vulnerabilities, and performance issues. Use when a PR needs review, code changes need feedback, or security audit is requested.
```
Why it works: Third person, specific capabilities listed, multiple trigger phrases.

```
Generates Vue 3 single-file components with TypeScript and Composition API. Use when creating new components, converting Options API to Composition API, or scaffolding component directories. Do NOT use for general TypeScript or non-Vue frameworks.
```
Why it works: Specific technology terms for discovery, negative trigger to prevent over-matching.

## Debug Technique

After writing the description, test it by asking the agent:

> "When would you use the [skill-name] skill?"

The agent should quote the description back accurately and identify matching scenarios. If it cannot, the description has gaps — revise and re-test.
