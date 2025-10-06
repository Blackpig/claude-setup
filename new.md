# Claude Code Setup for New TALL Stack + Filament Project

Use this prompt with Claude Code to configure optimal settings for a new project:

```bash
claude-code "Set up Claude Code configuration for a new TALL stack + Filament project:

1. Create a .claude/ directory

2. Create .claude/project-info.md with template for:
   - Laravel version (leave placeholder for me to fill)
   - Alpine.js version (leave placeholder)
   - Livewire version (leave placeholder)
   - Tailwind CSS version (v3 or v4 - leave placeholder)
   - Filament version (v3 or v4 - leave placeholder)
   - PHP version (leave placeholder)
   - Database driver: MySQL (default assumption for TALL stack)
   - Development environment: Laravel Herd
   - Note: Update these versions once stack is installed

3. Create .claude/conventions.md with TALL stack best practices template sections for:
   - Livewire component organization (class-based vs inline views)
   - Filament resource patterns and structure
   - Alpine.js usage guidelines and when to use vs Livewire
   - Tailwind CSS approach (utility-first patterns)
   - Laravel coding standards (PSR-12, naming conventions)
   - Database migration and model conventions
   - Git workflow and branching strategy

4. Create .claude/context.md template with sections for:
   - Project purpose (to be filled in)
   - Target audience/use case
   - Key features to build
   - Special requirements or constraints
   - Custom packages or integrations planned
   - Authentication/authorization approach
   - Deployment strategy

5. Set up MCP servers by checking and updating the Claude Desktop configuration:
   - Install Laravel Herd MCP server following docs at https://herd.laravel.com/docs/macos/advanced-usage/ai-integrations#claude-code
   - Install Laravel Boost MCP server following docs at https://boost.laravel.com/installed
   - Install Git MCP server for enhanced git operations (commit history, branch management, diff analysis)
   - Install MySQL/Database MCP server for direct database schema inspection and queries
   - Install Brave Search MCP for web searches when needing current documentation or package info
   - Install Filesystem MCP (if not already configured) for comprehensive file operations
   - Provide instructions for any manual steps needed to complete MCP setup
   - Test that MCP servers are accessible and properly configured

6. Create .claude/README.md explaining:
   - What these configuration files are for
   - How to keep them updated as the project evolves
   - Best practices for working with Claude Code on TALL stack projects
   - Available MCP servers and their capabilities:
     * Laravel Herd - site management, PHP version switching, local environment control
     * Laravel Boost - Laravel-specific AI assistance and best practices
     * Git - version control operations, history analysis, branch management
     * MySQL - database schema inspection, query building, migration assistance
     * Brave Search - documentation lookup, package discovery, staying current
     * Filesystem - comprehensive file operations and project navigation
   - How to use each MCP server effectively in TALL stack development
   - Common workflows combining multiple MCP servers (e.g., Git + Database for schema versioning)
   - Recommended workflow for filling in version numbers after installation

7. Create a .claude/setup-checklist.md for new project initialization:
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
- MCP server installation status for each server
- Any manual steps I need to complete for MCP servers
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
5. Complete any manual MCP server setup steps
6. Follow the setup checklist to install your TALL stack
7. Update `.claude/project-info.md` with actual versions after installation

## What Gets Created

- `.claude/project-info.md` - Stack version templates (to be filled)
- `.claude/conventions.md` - Best practices templates
- `.claude/context.md` - Project planning template
- `.claude/setup-checklist.md` - Installation guide
- `.claude/README.md` - Configuration guide
- MCP server configurations for Herd, Boost, Git, MySQL, Search, and Filesystem

## After Setup

1. Install your TALL stack following the checklist
2. Update `.claude/project-info.md` with actual versions
3. Fill in `.claude/context.md` with your project details
4. Customize `.claude/conventions.md` to match your preferences
5. Always reference these files in future Claude Code prompts