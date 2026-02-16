# Claude Code Agents

Custom agents for [Claude Code](https://docs.anthropic.com/en/docs/claude-code) that provide specialized, reusable capabilities.

## Available Agents

### `code-quality-reviewer` — Expert Code Quality Reviewer

An elite software engineering consultant agent that performs thorough, actionable code quality reviews. Evaluates code across 9 quality dimensions: readability, documentation, maintainability, architecture, error handling, modern practices, testability, security, and performance.

**Features:**
- Systematic review methodology with prioritized findings (Critical / Important / Suggestions)
- For Python projects, automatically invokes the `/python-quality` skill for automated lint, type check, test, security, and dependency analysis before manual review
- Language/framework agnostic — works with any codebase
- Actionable feedback with concrete code examples
- Strengths section to highlight good patterns
- Proportional rigor — matches review depth to project context

**When it activates:**
- After implementing new features or refactoring code
- When explicitly asked to review code
- Before merging pull requests
- After modifying code across multiple files

## Installation

Copy any agent's `.md` file to your Claude Code agents directory:

```bash
# Global (available in all projects)
cp agents/code-quality-reviewer/code-quality-reviewer.md ~/.claude/agents/code-quality-reviewer.md

# Project-specific
cp agents/code-quality-reviewer/code-quality-reviewer.md .claude/agents/code-quality-reviewer.md
```

Then restart Claude Code or start a new session. The agent will be available for use.

**Note:** The `code-quality-reviewer` agent references the `/python-quality` skill for Python projects. If you want that integration, also install the skill from [claude-skills](https://github.com/trwilcoxson/claude-skills).

## Structure

```
agents/
  code-quality-reviewer/
    code-quality-reviewer.md    # The agent file (copy to ~/.claude/agents/)
```

## License

MIT
