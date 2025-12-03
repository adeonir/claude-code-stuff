---
description: Build React + Tailwind components from copy.yaml and design.json
argument-hint: [--output=path]
---

Build production-grade React components using Claude Code.

**Arguments received:** $ARGUMENTS

**Task:** Use the frontend-builder agent to:
1. Check if Vite project exists (look for package.json with vite dependency)
2. If no project exists, scaffold new Vite + React + Tailwind + shadcn/ui
3. Locate copy.yaml and design.json in ./prompts/*/
4. Generate components applying design tokens and frontend-design principles
5. Use --output if provided, otherwise use ./src/components/
