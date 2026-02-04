# skills

A collection of skills for [Claude Code](https://docs.anthropic.com/en/docs/claude-code).

## Quick Installation

### Install All

Install all skills globally for all agents (non-interactive):

```bash
npx skills add hyf0/skills -g --all
```

### Install Code Skill Only

```bash
npx skills add hyf0/skills -g --all --skill code
```

### Selective Installation

For interactive installation where you can pick specific skills and agents:

```bash
npx skills add hyf0/skills -g
```

## Available Skills

### `/code`

Open the current working directory or a specified folder in Visual Studio Code.

**Usage:**
- `/code` - Opens the current working directory
- `/code /path/to/folder` - Opens the specified folder

## License

MIT
