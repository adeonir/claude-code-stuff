# Design Builder

Claude Code plugin that extracts copy and design from references to build frontend components or generate prompts for AI tools.

## Features

- Extract content structure from URLs (optional)
- Extract design tokens from reference images (screenshots, mockups)
- Build frontend components directly with Claude Code
- Generate optimized prompts for Replit, v0, Lovable, Figma
- Auto-scaffold Vite projects when needed
- Auto-loaded skill to avoid generic "AI slop" aesthetics

## Installation

```bash
# Add marketplace (if not already added)
/plugin marketplace add adeonir/claude-code-plugins

# Install plugin
/plugin install design-builder
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
| `copy-extractor` | Content Strategist - extracts content from URLs |
| `design-extractor` | Creative Director - extracts design from images |
| `prompt-generator` | Prompt Engineer - generates platform-specific prompts |
| `frontend-builder` | Frontend Engineer - builds components |

## Skills

| Skill | Description |
|-------|-------------|
| `frontend-design` | Distinctive design principles that avoid generic AI aesthetics |

## Project Types

| Type | Example |
|------|---------|
| `landing` | Product page, lead capture |
| `website` | Corporate, blog, portfolio |
| `webapp` | Dashboard, SaaS, admin panel |
| `app` | iOS/Android, PWA |

## Prompt Targets

| Target | Best For |
|--------|----------|
| `replit` | Full landing pages with images |
| `v0` | Quick React/shadcn components |
| `lovable` | Apps with Supabase backend |
| `figma` | Design system documentation |

## Usage

### Full Workflow

```bash
# 1. Extract copy from reference URL
/extract-copy https://example.com --type=landing

# 2. Extract design from images
/extract-design
# Then paste reference images

# 3. Build or generate prompt
/build-frontend --output=./src/components
# OR
/generate-prompt --target=replit
```

### Minimal Workflow (design only)

```bash
# 1. Extract design from images (will ask for project description)
/extract-design
# Paste images, then provide brief description

# 2. Build frontend
/build-frontend
```

## Credits

Workflow inspired by [Deborah Folloni's method](https://dfolloni.substack.com/p/os-prompts-que-eu-uso-para-fazer).

## License

MIT
