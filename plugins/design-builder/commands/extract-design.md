---
description: Extract design tokens from reference images
argument-hint: [image-url...]
---

<objective>
Extract design tokens from reference images and generate a design.json file by invoking the design-extractor subagent.
</objective>

<instructions>
Invoke the `design-extractor` subagent to extract design tokens from images.

Arguments received: $ARGUMENTS

The design-extractor will:
1. Request images from user if not provided
2. Check for existing copy.yaml for project context (optional)
3. If no copy.yaml, ask user for brief project description
4. Extract colors, typography, spacing, components
5. Generate design.json in ./prompts/

Wait for the agent to complete and inform the user of the result.
</instructions>

<error_handling>
- **No images provided**: Ask user to paste reference images.
</error_handling>
