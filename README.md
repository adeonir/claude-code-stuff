# Claude Code Plugins

A personal collection of plugins for Claude Code, organized as a plugin marketplace.

## Available Plugins

### Installation

Add this marketplace to Claude Code:

```bash
/plugin marketplace add adeonir/claude-code-plugins
```

### Available Plugins

| Plugin | Description | Version |
|--------|-------------|---------|
| [design-to-code](./plugins/design-to-code) | Extract copy and design to generate prompts for AI frontend tools | 1.0.0 |
| [git-helpers](./plugins/git-helpers) | Git workflow commands (commit, PR, code review) | 1.0.0 |

### Installing a Plugin

```bash
/plugin install design-to-code
```

### Marketplace Commands

```bash
# Add marketplace
/plugin marketplace add adeonir/claude-code-plugins

# List available plugins
/plugin marketplace list

# Install a plugin
/plugin install design-to-code

# Update marketplace
/plugin marketplace update adeonir/claude-code-plugins
```

## Contributing

1. Fork this repository
2. Add your plugin under `plugins/`
3. Submit a pull request

## License

MIT
