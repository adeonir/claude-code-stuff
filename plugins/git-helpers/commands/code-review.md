---
description: Review code changes using code-reviewer agent
argument-hint: [base-branch]
---

# Code Review Command

Review code changes in the current branch using the `code-reviewer` agent.

## Arguments

- **No argument**: Auto-detect base branch (main > master > develop)
- **`base-branch`**: Use specified branch as base for comparison

## Context

- Current branch: !`git branch --show-current`
- Base branch: $ARGUMENTS or auto-detect from !`git branch -a | grep -E "(main|master|develop)$" | head -1 | xargs basename`
- Modified files: !`git diff $(git branch -a | grep -E "(main|master|develop)$" | head -1 | xargs basename)...HEAD --name-only`

## Task

Use the `code-reviewer` agent to review the modified files listed above.

The agent should:
1. Read each modified file
2. Analyze for bugs, security issues, performance problems, and maintainability concerns
3. Generate `CODE_REVIEW.md` with issues, suggestions, and summary
