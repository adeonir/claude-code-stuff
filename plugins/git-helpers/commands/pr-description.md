---
description: Generate PR title and description
argument-hint: [base-branch]
allowed-tools: Bash(git:*), Bash(gh:*), Bash(which gh), Write
---

# PR Description Command

Generate a title and description for a Pull Request based on the actual branch changes.

## Arguments

- **No argument**: Auto-detect base branch (main > master > develop)
- **`base-branch`**: Use specified branch as base for comparison

## Process

1. **Detect base branch** (if not specified):
   ```bash
   git branch -a | grep -E "(main|master|develop)$" | head -1
   ```

2. **Gather context** (run in parallel):
   ```bash
   git branch --show-current
   git log {base}..HEAD --oneline
   git diff {base}...HEAD --stat
   git diff {base}...HEAD
   ```

3. **Analyze changes**:
   - Review commits and diff to understand what changed
   - Base analysis solely on file contents, not conversation context
   - Determine the appropriate PR type

4. **Check for gh cli**:
   ```bash
   which gh
   ```

5. **Create PR or save file**:
   - If `gh` available: create PR with `gh pr create`
   - If `gh` unavailable: save to `PR_DETAILS.md`

## PR Format

**Title:**
```
type: concise description in imperative mood
```

**Body:**
```markdown
Brief summary of what this PR does (2-3 sentences max).

## Changes
- Key change 1
- Key change 2
- Key change 3
```

## PR Types

| Type | Use when |
|------|----------|
| `feat` | Adding new functionality |
| `fix` | Fixing a bug |
| `refactor` | Restructuring code without changing behavior |
| `chore` | Maintenance tasks, dependencies, configs |
| `docs` | Documentation changes |
| `test` | Adding or updating tests |

## Guidelines

- Analyze commits and diff, not conversation context
- Title and description should reflect the current implementation state
- Be specific about functionality, not generic
- Focus on WHAT is being done, not HOW
- Use imperative mood: "add", "fix", "implement"
- Keep changes list to 3-5 key items
- Do not include risk assessment, testing instructions, or technical flow sections

## Examples

**Simple PR:**
```
Title: fix: resolve pagination reset on filter change

Body:
Fixes an issue where pagination would reset to page 1 when applying filters,
causing users to lose their position in the results.

## Changes
- Preserve page state when filters change
- Reset only when search query changes
```

**Feature PR:**
```
Title: feat: add user session timeout handling

Body:
Implements automatic session timeout to improve security. Users are warned
before timeout and automatically logged out after inactivity period.

## Changes
- Session monitoring with activity tracking
- Warning dialog before session expiration
- Automatic logout after inactivity period
- User preference for timeout duration
```

## Task

Generate PR description for current branch with $ARGUMENTS.

If `gh` cli is available, create the PR directly. Otherwise, save the content to `PR_DETAILS.md` in the repository root.
