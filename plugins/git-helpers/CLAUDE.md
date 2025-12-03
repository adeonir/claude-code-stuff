# git-helpers

Git workflow helper commands for Claude Code.

## Commands

### /commit

Create commits with well-formatted messages based on actual file changes.

**Usage:**
```bash
/commit           # Stage all files and commit
/commit -s        # Commit only staged files
```

**Message format:** `type: concise description`

**Key behavior:**
- Analyzes the actual diff, not conversation context
- Handles pre-commit hooks with automatic amend

### /pr-description

Generate PR title and description based on branch changes.

**Usage:**
```bash
/pr-description          # Auto-detect base branch
/pr-description main     # Use main as base
```

**Output:**
- If `gh` cli available: creates PR directly
- Otherwise: saves to `PR_DETAILS.md`

**Key behavior:**
- Analyzes commits and diff, not conversation context
- Simple format: title + summary + changes list

### /code-review

Review code changes using the `code-reviewer` agent.

**Usage:**
```bash
/code-review          # Auto-detect base branch
/code-review main     # Use main as base
```

**Output:** `CODE_REVIEW.md`

## Agents

### code-reviewer

Senior code reviewer for quality analysis. Invoked by `/code-review`.

**Focus:** bugs, security, performance, maintainability

**Output format:**
```markdown
## Issues
- **[file:line]** Problem description
  - Suggested fix

## Suggestions
- **[file:line]** Improvement description
  - How to improve

## Summary
X files | Y issues | Z suggestions
```

## Types

`feat`, `fix`, `refactor`, `chore`, `docs`, `test`
