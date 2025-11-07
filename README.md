# Claude Code Setup for TALL Stack + Filament Projects

This repository contains configuration templates and setup instructions for optimizing Claude Code when working on TALL Stack (Tailwind, Alpine, Livewire, Laravel) + Filament projects.

## What This Does

Provides ready-to-use prompts and templates that:
- Create a `.claude/` directory with project context files
- Set up MCP servers (Laravel Herd and Laravel Boost)
- Configure `.cliignore` to reduce token usage by 50-70%
- Document coding conventions and project standards
- Establish best practices for AI-assisted development

## Three Setup Options

### 1. New Project Setup (`new.md`)

Use when starting a **brand new** TALL Stack + Filament project from scratch.

**Features:**
- Creates `.claude/` directory with template files
- Leaves version placeholders for you to fill in after installation
- Sets up MCP servers (Herd + Boost)
- Two-step process: initial setup, then copy `.cliignore` after stack installation

**When to use:** Before installing Laravel, Filament, or any dependencies.

### 2. Existing Project Setup (`existing.md`)

Use when adding Claude Code configuration to an **existing** TALL Stack + Filament project.

**Features:**
- Analyzes your `composer.json` and `package.json` to detect versions
- Auto-populates `.claude/project-info.md` with actual versions
- Detects existing code patterns and conventions
- Copies `.cliignore` immediately (since dependencies already exist)
- Sets up MCP servers (Herd + Boost)

**When to use:** You already have a working project and want to add Claude Code optimization.

### 3. Update Existing Configuration (`update-cliignore.md`)

Use when you **already have a `.claude/` directory** but want to add the new `.cliignore` token optimization.

**Features:**
- Adds `.cliignore` to existing setup
- Creates `.claude/cliignore-guide.md` documentation
- Updates `.claude/README.md` with token optimization info
- Doesn't touch your existing configuration files

**When to use:** You set up `.claude/` before `.cliignore` was added to this repo.

**Quick command:** A bash script is available at `~/bin/claude-update-cliignore` - just run:
```bash
claude-update-cliignore
```

## What Gets Created

All setups create:

```
.claude/
├── README.md              # Configuration guide
├── project-info.md        # Stack versions and environment
├── conventions.md         # Coding standards and patterns
├── context.md            # Project overview and architecture
├── mcp-setup.md          # MCP server configuration guide
├── cliignore-guide.md    # Token optimization instructions
└── setup-checklist.md    # Installation steps (new projects only)

.cliignore                # Token optimization exclusions
.gitignore                # Updated to exclude .claude/

~/Library/Application Support/Claude/claude_desktop_config.json
                          # MCP server configuration
```

## Token Optimization

The `.cliignore` file excludes common files that don't need AI context:
- `vendor/` and `node_modules/`
- Package lock files
- Build outputs (`public/css/`, `public/js/`)
- IDE files (`.idea/`, `.vscode/`)
- Environment files (`.env*`)
- Laravel generated files

**Result:** 50-70% reduction in token usage while maintaining full functionality.

**Exceptions:** Can still access `vendor/filament/` or other vendor code when explicitly requested or debugging requires it.

## MCP Servers

Both **Laravel Herd** and **Laravel Boost** MCP servers are configured:

### Laravel Herd
- Site management
- PHP version switching
- Service control (MySQL, Redis, etc.)
- Database management

### Laravel Boost
- Laravel-specific AI assistance
- Artisan command execution
- Code generation
- Testing support

**Important:** Must restart Claude Desktop (Cmd+Q, then reopen) after setup to activate MCP servers.

## Usage Instructions

1. **Choose your setup option** (new, existing, or update)
2. **Navigate to your project directory**
3. **Copy and run the prompt** from the appropriate `.md` file
4. **Restart Claude Desktop** to activate MCP servers
5. **Test MCP servers:**
   - "List all my Herd sites"
   - "Run artisan route:list"

## Testing Token Savings

After setup, verify the `.cliignore` is working:
```bash
claude-code "List all Filament resources"
```

Check the token count - should see 50-70% reduction compared to without `.cliignore`.

## Repository Structure

```
claude-setup/
├── README.md                 # This file
├── new.md                    # Setup prompt for new projects
├── existing.md               # Setup prompt for existing projects
├── update-cliignore.md       # Update prompt for .cliignore
├── .cliignore                # Template exclusion file
└── .gitignore                # Protects this repo
```

## Customization

After setup, you can customize:
- `.claude/conventions.md` - Add your specific coding patterns
- `.claude/context.md` - Document project-specific details
- `.cliignore` - Add project-specific exclusions
- `.claude/cliignore-guide.md` - Adjust token optimization strategy

## Best Practices

1. **Always reference context:** Start prompts with "Following our project conventions..." or "Based on our stack configuration..."
2. **Keep files updated:** Update `.claude/project-info.md` when upgrading packages
3. **Document patterns:** Add new conventions to `.claude/conventions.md` as your project evolves
4. **Respect .cliignore:** Let Claude Code honor exclusions unless you explicitly need vendor code access
5. **Use MCP servers:** Leverage Herd and Boost for common Laravel tasks

## Requirements

- Claude Code CLI installed
- Laravel Herd (for Herd MCP server)
- Node.js and npm (for Boost MCP server via npx)
- macOS (paths are Mac-specific)

## Notes

- The `.claude/` directory is automatically added to `.gitignore` to protect sensitive project context
- MCP servers only work with Claude Desktop, not claude.ai web interface
- Only Herd and Boost MCP servers are currently stable and recommended
- Other MCP servers (Git, MySQL, Brave Search, Filesystem) are not yet publicly available

## Support

For issues or questions about Claude Code itself, visit:
https://github.com/anthropics/claude-code/issues

## License

These are configuration templates - use freely in your projects.
