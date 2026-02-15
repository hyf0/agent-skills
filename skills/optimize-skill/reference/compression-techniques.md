## Six Techniques

Apply these in order of impact. Each technique includes a before/after example.

### 1. Remove What the Agent Already Knows

The agent already knows general programming, standard libraries, markdown syntax, YAML format, git commands, and well-known tool usage. Do not reteach these.

**Before (wasteful):**
```markdown
## How to Create a File
To create a file in JavaScript, use the `fs` module. Import it with
`const fs = require('fs')` and then call `fs.writeFileSync(path, content)`
to write content to a file.
```

**After (useful):**
```markdown
## File Naming
Output files must use the pattern `{date}-{slug}.md` with ISO 8601 dates.
```

### 2. Replace Prose With Structure

Convert paragraphs into bullet points, tables, or structured lists.

**Before (40 words):**
```markdown
When choosing a skill name, you should use gerund form for processes like
creating-components, noun form for tools like code, always use kebab-case,
keep it under 64 characters, and never use spaces or capitals.
```

**After (12 words):**
```markdown
Naming rules:
- Gerund for processes: `creating-components`
- Noun for tools: `code`
- Kebab-case, max 64 chars, no spaces/capitals
```

### 3. Use Tables for Decision Matrices

Replace scattered paragraphs comparing options with a single comparison table.

**Before:** Three separate paragraphs describing when to use each approach.

**After:**
```markdown
| Situation | Approach | Why |
|-----------|----------|-----|
| Workflow content | Keep in SKILL.md | Every invocation needs it |
| Knowledge base / lookup content | Use reference/ files | Reduces per-invocation token cost |
| SKILL.md over 500 lines | Split into reference/ files | Exceeds recommended limit |
```

### 4. Index Pattern for Large Knowledge Bases

Replace inline content with a categorized index pointing to reference files.

**Before:** 400 lines of mixed rules, examples, and specifications in SKILL.md.

**After:** 80-line SKILL.md with workflow + index:
```markdown
## Reference
- Naming conventions -> See [naming](reference/naming.md)
- Validation rules -> See [validation](reference/validation.md)
- Examples -> See [examples](reference/examples.md)
```

### 5. Merge Redundant or Tiny Reference Files

If a reference file is very short, the overhead of a separate file may exceed its benefit. Consider inlining it back into SKILL.md.

If two reference files cover closely related topics and together are under ~80 lines, merge them into one file.

### 6. Cut Meta-Commentary

Remove text that describes the document itself rather than providing actionable information.

**Remove phrases like:**
- "This section covers..."
- "Let's look at..."
- "In the following section, we will..."
- "As mentioned above..."
- "It's important to note that..."

**Keep:** Direct instructions, rules, examples, and checklists.
