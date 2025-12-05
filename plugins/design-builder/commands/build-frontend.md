---
description: Build frontend components from design tokens
argument-hint: [--output=path]
---

<objective>
Build production-grade frontend components using Claude Code by invoking the frontend-builder subagent.
</objective>

<instructions>
Invoke the `frontend-builder` subagent to build the frontend.

Arguments received: $ARGUMENTS

The frontend-builder will:
1. Detect existing project stack (React, Vue, Svelte, etc.)
2. If no project, ask user for preferred stack
3. Scaffold new project if needed
4. Locate design.json (required) and copy.yaml (optional)
5. If no copy.yaml, ask user for brief project description
6. Generate components applying the frontend-design skill

Wait for the agent to complete and inform the user of the result.
</instructions>

<error_handling>
- **No design.json found**: "Run /extract-design first to extract design tokens."
- **Scaffold failed**: Check package manager is installed and available.
</error_handling>
