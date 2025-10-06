# Claude Code Setup for Existing TALL Stack + Filament Project

Use this prompt with Claude Code to configure optimal settings for an existing project:

```bash
claude-code "Set up optimal Claude Code configuration for this TALL stack + Filament project:

1. Create a .claude/ directory if it doesn't exist

2. Create or update .gitignore to protect sensitive project context:
   - Check if .gitignore exists, create if it doesn't
   - Add '.claude/' to .gitignore if not already present
   - Add a comment explaining why: '# Claude Code configuration (contains project-specific context)'

3. Analyze the project to detect current versions and configuration by reading:
   - composer.json for Laravel, Livewire, Filament versions
   - package.json for Tailwind CSS, Alpine.js versions
   - config/filament.php if it exists
   - tailwind.config.js for Tailwind configuration
   - .env for database driver (DB_CONNECTION) and note that it's typically MySQL
   - Detect that local development is managed by Laravel Herd

4. Create .claude/project-info.md documenting:
   - Detected stack versions (Laravel, Alpine, Livewire, Tailwind, Filament, PHP)
   - Database driver (from .env)
   - Development environment: Laravel Herd
   - Project type and structure
   - Key dependencies

5. Create .claude/conventions.md documenting:
   - Existing code patterns found in app/Livewire/ (if any)
   - Filament resource patterns from app/Filament/ (if any)
   - Naming conventions observed in the codebase
   - Directory structure preferences
   - Database conventions and migration patterns

6. Create .claude/context.md for:
   - Project overview and purpose
   - Key architectural decisions
   - Custom components or packages being used
   - Any special configuration or setup notes
   - Laravel Herd site configuration details

7. Set up MCP servers by creating the Claude Desktop configuration:
   - Configure Laravel Herd MCP server (built into Herd)
   - Configure Laravel Boost MCP server (runs via npx, no installation needed)
   - Create configuration at ~/Library/Application Support/Claude/claude_desktop_config.json
   - Note: Only Herd and Boost MCP servers are currently stable and recommended
   - Other MCP servers (Git, MySQL, Brave Search, Filesystem) are not yet publicly available
   - Configuration example:
     {
       \"mcpServers\": {
         \"herd\": {
           \"command\": \"/Applications/Herd.app/Contents/MacOS/herd\",
           \"args\": [\"mcp\"]
         },
         \"boost\": {
           \"command\": \"npx\",
           \"args\": [\"-y\", \"@laravel/boost-mcp-server\"]
         }
       }
     }

8. Create .claude/mcp-setup.md documenting:
   - MCP server configuration details
   - How to restart Claude Desktop to activate MCP servers
   - Test commands for each server
   - Common use cases and workflows
   - Troubleshooting guide

9. Add a .claude/README.md explaining:
   - What these files are for
   - How to keep them updated
   - Best practices for working with Claude Code on this project
   - Available MCP servers and their capabilities:
     * Laravel Herd - site management, PHP version switching, service control, database management
     * Laravel Boost - Laravel-specific AI assistance, artisan commands, code generation
   - How to use each MCP server effectively in TALL stack development
   - Common workflows combining both MCP servers

After creating these files and setting up MCP servers, show me:
- Summary of detected versions and configuration
- Database connection details
- MCP server installation status (should show Herd and Boost configured)
- Instructions to restart Claude Desktop to activate MCP servers
- Test commands to verify MCP servers are working
- Suggestions for additional context to add manually
- Recommended MCP server workflows for common TALL stack tasks"
```

## Quick Reference

**Usage:**
1. Navigate to your existing project directory
2. Copy the command above
3. Paste into your terminal and run
4. Review the generated configuration files
5. **Restart Claude Desktop** (Cmd+Q, then reopen) to activate MCP servers
6. Test MCP servers with "List all my Herd sites" and "Run artisan route:list"
7. Update `.claude/` files with any additional project-specific context

## What Gets Created

- `.gitignore` entry for `.claude/` directory (protects sensitive data)
- `.claude/project-info.md` - Stack versions and database info
- `.claude/conventions.md` - Code patterns and standards
- `.claude/context.md` - Project overview and architecture
- `.claude/mcp-setup.md` - MCP server configuration and usage guide
- `.claude/README.md` - Configuration guide
- `~/Library/Application Support/Claude/claude_desktop_config.json` - MCP server config for Herd and Boost

## Important Notes

### MCP Servers
- **Only 2 servers configured**: Herd and Boost (these are the stable, production-ready servers)
- **No manual installation needed**: Herd is built-in, Boost uses npx
- **Must restart Claude Desktop**: MCP servers only load on startup
- **Other servers**: Git, MySQL, Brave Search, and Filesystem MCP servers are not yet publicly available

### Testing MCP Servers
After restarting Claude Desktop, test with:
- **Herd**: "List all my Herd sites"
- **Boost**: "Run artisan route:list"

## After Setup

Always reference these files in future Claude Code prompts by mentioning:
- "Following our project conventions..."
- "Based on our stack configuration..."
- "Using the patterns documented in .claude/..."

## Common MCP Workflows

### Starting Development
```
1. "Check Herd service status"
2. "Open [site].test in browser"
3. "Run artisan migrate"
```

### Adding a Feature
```
1. "Generate a [Model] model with migration"
2. "Run artisan migrate"
3. "Create a Filament resource for [Model]"
4. "Show me all routes"
```

### Debugging
```
1. "What PHP version is this site using?"
2. "Show Herd error logs"
3. "Run artisan queue:work --once"
```
