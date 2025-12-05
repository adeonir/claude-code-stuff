# Design Builder

Claude Code plugin that extracts copy and design from references to build frontend components or generate prompts for AI tools.

## Architecture

```
design-builder/
├── .claude-plugin/
│   └── plugin.json                 # Plugin manifest
├── agents/                         # Specialized subagents
│   ├── copy-extractor.md           # Content Strategist
│   ├── design-extractor.md         # Creative Director
│   ├── prompt-generator.md         # Prompt Engineer
│   └── frontend-builder.md         # Frontend Engineer
├── commands/                       # Slash commands
│   ├── extract-copy.md
│   ├── extract-design.md
│   ├── generate-prompt.md
│   └── build-frontend.md
├── skills/                         # Auto-loaded guidance
│   └── frontend-design/SKILL.md
└── prompts/                        # Output directory
    ├── copy.yaml
    ├── design.json
    └── prompt-{target}.md
```

## Workflows

Two entry points, each can end with `/build-frontend` or `/generate-prompt`:

```
# Full: Start from URL reference
URL -> /extract-copy -> copy.yaml -> /extract-design -> design.json

# Minimal: Start from design image only (with brief project description)
Image -> /extract-design -> design.json

# Then choose output:
-> /build-frontend    # Claude Code builds it
-> /generate-prompt   # For Replit/v0/Lovable
```

## Commands

| Command | Description |
|---------|-------------|
| `/extract-copy` | Extract content from URL to copy.yaml (optional) |
| `/extract-design` | Extract design from images to design.json |
| `/generate-prompt` | Generate prompt for target platform |
| `/build-frontend` | Build frontend components |

## Agents

| Agent | Role |
|-------|------|
| `copy-extractor` | Content Strategist |
| `design-extractor` | Creative Director |
| `prompt-generator` | Prompt Engineer |
| `frontend-builder` | Frontend Engineer |

Agents can be invoked directly: "Use the design-extractor agent to analyze this image"

## Skills

| Skill | Description |
|-------|-------------|
| `frontend-design` | Design principles auto-loaded for frontend tasks (avoids AI slop aesthetics) |

The frontend-builder agent MUST apply the frontend-design skill.

## Project Types

| Type | Description | Example |
|------|-------------|---------|
| `landing` | Single-page landing | Product page, lead capture |
| `website` | Multi-page site | Corporate, blog, portfolio |
| `webapp` | Interactive application | Dashboard, SaaS, admin panel |
| `app` | Mobile application | iOS/Android, PWA |

## Prompt Targets

| Target | Style | Best For |
|--------|-------|----------|
| `replit` | Detailed, design.json inline | Full landing pages with images |
| `v0` | Concise, shadcn/ui | Quick React components |
| `lovable` | UX-focused, flows | Apps with Supabase backend |
| `figma` | Component specs | Design system documentation |

## Output Formats

### copy.yaml
- `landing/website`: sections with hero, features, cta, footer
- `webapp`: screens with widgets, auth, sidebar navigation
- `app`: screens, onboarding, bottom-tabs, gestures, native features

### design.json
```json
{
  "meta": { "name", "version", "project_type" },
  "principles": { "overall", "keywords", "avoid" },
  "colors": { "primary", "accent", "neutral", "semantic" },
  "typography": { "fonts", "scale", "emphasis" },
  "spacing": { "section", "container", "grid", "component" },
  "components": { "button", "card", "badge", "input", "icon" },
  "effects": { "shadows", "transitions" },
  "animations": { "fadeInUp", "hoverLift", "stagger" },
  "backgrounds": { "patterns", "gradients", "sections" }
}
```

## References

- Workflow based on Deborah Folloni's method (DebGPT)
- [Original post](https://dfolloni.substack.com/p/os-prompts-que-eu-uso-para-fazer)
