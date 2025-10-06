# Claude Code Setup for Existing TALL Stack + Filament Project

Use this prompt with Claude Code to configure optimal settings for an existing project:

```bash
claude-code "Set up optimal Claude Code configuration for this TALL stack + Filament project:

1. Create a .claude/ directory if it doesn't exist

2. Analyze the project to detect current versions and configuration by reading:
   - composer.json for Laravel, Livewire, Filament versions
   - package.json for Tailwind CSS, Alpine.js versions
   - config/filament.php if it exists
   - tailwind.config.js for Tailwind configuration
   - .env for database driver (DB_CONNECTION) and note that it's typically MySQL
   - Detect that local development is managed by Laravel Herd

3. Create .claude/project-info.md documenting:
   - Detected stack versions (Laravel, Alpine, Livewire, Tailwind, Filament, PHP)
   - Database driver (from .env)
   - Development environment: Laravel Herd
   - Project type and structure
   - Key dependencies

4. Create .claude/conventions.md documenting:
   - Existing code patterns found in app/Livewire/ (if any)
   - Filament resource patterns from app/Filament/ (if any)
   - Naming conventions observed in the codebase
   - Directory structure preferences
   - Database conventions and migration patterns

5. Create .claude/context.md for:
   - Project overview and purpose
   - Key architectural decisions
   - Custom components or packages being used
   - Any special configuration or setup notes
   - Laravel Herd site configuration details

6. Set up MCP servers by checking and updating the Claude Desktop configuration:
   - Install Laravel Herd MCP server following docs at https://herd.laravel.com/docs/macos/advanced-usage/ai-integrations#claude-code
   - Install Laravel Boost MCP server following docs at https://boost.laravel.com/installed
   - Install Git MCP server for enhanced git operations (commit history, branch management, diff analysis)
   - Install MySQL/Database MCP server for direct database schema inspection and queries
   - Install Brave Search MCP for web searches when needing current documentation or package info
   - Install Filesystem MCP (if not already configured) for comprehensive file operations
   - Provide instructions for any manual steps needed to complete MCP setup
   - Test that MCP servers are accessible and properly configured

7. Add a .claude/README.md explaining:
   - What these files are for
   - How to keep them updated
   - Best practices for working with Claude Code on this project
   - Available MCP servers and their capabilities:
     * Laravel Herd - site management and PHP version switching
     * Laravel Boost - Laravel-specific AI assistance
     * Git - version control operations and history
     * MySQL - database schema and query capabilities
     * Brave Search - documentation and package lookup
     * Filesystem - file operations
   - How to use each MCP server effectively in TALL stack development
   - Common workflows combining multiple MCP servers

After creating these files and setting up MCP servers, show me:
- Summary of detected versions and configuration
- Database connection details
- MCP server installation status for each server
- Any manual steps I need to complete
- Suggestions for additional context to add manually
- Recommended MCP server workflows for common TALL stack tasks"
```

## Quick Reference

**Usage:**
1. Navigate to your existing project directory
2. Copy the command above
3. Paste into your terminal and run
4. Review the generated configuration files
5. Complete any manual MCP server setup steps
6. Update `.claude/` files with any additional project-specific context

## What Gets Created

- `.claude/project-info.md` - Stack versions and database info
- `.claude/conventions.md` - Code patterns and standards
- `.claude/context.md` - Project overview and architecture
- `.claude/README.md` - Configuration guide
- MCP server configurations for Herd, Boost, Git, MySQL, Search, and Filesystem

## After Setup

Always reference these files in future Claude Code prompts by mentioning:
- "Following our project conventions..."
- "Based on our stack configuration..."
- "Using the patterns documented in .claude/..."