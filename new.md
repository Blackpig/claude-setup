# Claude Code Setup for New TALL Stack + Filament Project

Use this prompt with Claude Code to configure optimal settings for a new project:

```bash
claude-code "Set up Claude Code configuration for a new TALL stack + Filament project:

1. Create a .claude/ directory

2. Create or update .gitignore to protect sensitive project context:
   - Check if .gitignore exists, create if it doesn't
   - Add '.claude/' to .gitignore if not already present
   - Add a comment explaining why: '# Claude Code configuration (contains project-specific context)'

3. Create .claude/project-info.md with template for:
   - Laravel version (leave placeholder for me to fill)
   - Alpine.js version (leave placeholder)
   - Livewire version (leave placeholder)
   - Tailwind CSS version (v3 or v4 - leave placeholder)
   - Filament version (v3 or v4 - leave placeholder)
   - PHP version (leave placeholder)
   - Database driver: MySQL (default assumption for TALL stack)
   - Development environment: Laravel Herd
   - Note: Update these versions once stack is installed

4. Create .claude/conventions.md with TALL stack best practices template sections for:
   - Livewire component organization (class-based vs inline views)
   - Filament resource patterns and structure
   - Alpine.js usage guidelines and when to use vs Livewire
   - Tailwind CSS approach (utility-first patterns)
   - Laravel coding standards (PSR-12, naming conventions)
   - Database migration and model conventions
   - Git workflow and branching strategy

5. Create .claude/context.md template with sections for:
   - Project purpose (to be filled in)
   - Target audience/use case
   - Key features to build
   - Special requirements or constraints
   - Custom packages or integrations planned
   - Authentication/authorization approach
   - Deployment strategy

6. Set up MCP servers by creating the Claude Desktop configuration:
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

7. Create .claude/mcp-setup.md documenting:
   - MCP server configuration details
   - How to restart Claude Desktop to activate MCP servers
   - Test commands for each server
   - Common use cases and workflows
   - Troubleshooting guide

8. Create .claude/README.md explaining:
   - What these configuration files are for
   - How to keep them updated as the project evolves
   - Best practices for working with Claude Code on TALL stack projects
   - Available MCP servers and their capabilities:
     * Laravel Herd - site management, PHP version switching, local environment control, database management
     * Laravel Boost - Laravel-specific AI assistance, artisan commands, code generation, testing
   - How to use each MCP server effectively in TALL stack development
   - Common workflows combining both MCP servers
   - Recommended workflow for filling in version numbers after installation

9. Create a .claude/setup-checklist.md for new project initialization:
   - Laravel installation steps
   - Filament installation and configuration
   - Livewire setup
   - Tailwind CSS installation (v3 vs v4 decision)
   - Alpine.js integration
   - Database configuration and first migration
   - Git repository initialization
   - Laravel Herd site setup
   - Environment configuration (.env setup)
   - Reminder to update project-info.md with actual versions

After setup, show me:
- Summary of created configuration files
- MCP server installation status (should show Herd and Boost configured)
- Instructions to restart Claude Desktop to activate MCP servers
- Test commands to verify MCP servers are working
- Checklist of information I need to provide once I start installing the stack
- Next steps for project initialization
- Suggestions for customizing conventions.md based on my preferences"
```

## Quick Reference

**Usage:**
1. Create and navigate to your new project directory
2. Copy the command above
3. Paste into your terminal and run
4. Review the generated template configuration files
5. **Restart Claude Desktop** (Cmd+Q, then reopen) to activate MCP servers
6. Test MCP servers with "List all my Herd sites" and "Run artisan route:list"
7. Follow the setup checklist to install your TALL stack
8. Update `.claude/project-info.md` with actual versions after installation

## What Gets Created

- `.gitignore` entry for `.claude/` directory (protects sensitive data)
- `.claude/project-info.md` - Stack version templates (to be filled)
- `.claude/conventions.md` - Best practices templates
- `.claude/context.md` - Project planning template
- `.claude/setup-checklist.md` - Installation guide
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

1. Install your TALL stack following the checklist
2. Update `.claude/project-info.md` with actual versions
3. Fill in `.claude/context.md` with your project details
4. Customize `.claude/conventions.md` to match your preferences
5. Always reference these files in future Claude Code prompts

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

### Setting Up Database
```
1. "Show me all MySQL databases"
2. "Run artisan migrate"
3. "List tables in [database]"
```

### Code Generation
```
1. "Generate a [Model] model with fillable fields [fields]"
2. "Create a migration for [table] with columns [columns]"
3. "Create a Filament resource with form fields [fields]"
```
