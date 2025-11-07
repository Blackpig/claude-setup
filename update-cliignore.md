# Update Existing .claude Configuration with .cliignore Support

Use this prompt when you already have a `.claude/` directory set up but want to add the new .cliignore token optimization functionality:

```bash
claude-code "Update my existing .claude configuration to add .cliignore token optimization:

1. Check if .cliignore already exists in the project root
   - If it exists, ask if I want to overwrite it
   - If it doesn't exist, proceed with copying

2. Copy .cliignore from ~/Clients/Sites/claude-setup/.cliignore to project root
   - This file contains optimized exclusions for Laravel + Filament projects
   - Read composer.json to verify installed packages
   - Read package.json to verify Node dependencies
   - Confirm the .cliignore contents are appropriate for this project

3. Create .claude/cliignore-guide.md with comprehensive documentation:
   - Purpose of .cliignore file (reduces token usage by 50-70%)
   - What files are excluded and why
   - Specific exceptions allowed:
     * Can reference vendor/filament/ when debugging Filament-specific issues
     * Can reference specific vendor packages when integration issues arise
     * Can access vendor/ temporarily if explicitly requested by user
   - Instructions for Claude Code:
     * Honor .cliignore exclusions by default in all operations
     * Do not read, analyze, or include ignored files in context unless:
       - User explicitly grants exception (e.g., 'You can check vendor/filament/...')
       - User specifically requests to see a file in an ignored directory
       - Debugging requires tracing into vendor code temporarily
     * Always ask permission before accessing ignored directories
   - Additional token optimization tips:
     * Use Task/Explore agents for broad codebase searches instead of direct Grep
     * Read files selectively rather than entire directories
     * For large files, use offset/limit parameters
     * Exclude test directories when not working on tests
     * Exclude migration files when only working on features
   - How to customize .cliignore for project-specific needs

4. Update .claude/README.md to add a section about .cliignore:
   - Add a new section explaining the token optimization strategy
   - Reference the cliignore-guide.md for detailed usage
   - Explain the balance between context and token efficiency

After updating, show me:
- Confirmation that .cliignore was copied
- List of what's being excluded
- Estimated token savings based on project size
- Summary of what was added to cliignore-guide.md
- Any recommendations for customizing .cliignore for this specific project"
```

## Quick Reference

**Usage:**
1. Navigate to your project directory (must have `.claude/` already set up)
2. Copy the command above
3. Paste into your terminal and run
4. Review the new/updated files
5. Test with a simple query to verify token usage has decreased

## What Gets Updated/Created

- `.cliignore` - Copied to project root (if not exists)
- `.claude/cliignore-guide.md` - Complete usage guide (new file)
- `.claude/README.md` - Updated with .cliignore section

## Before and After

**Before update:**
- Simple queries might use 4-6k tokens
- Context includes vendor/, node_modules/, build files

**After update:**
- Same queries should use 1-3k tokens (50-70% reduction)
- Context focused on your application code only
- Vendor code accessible when needed via explicit permission

## Verifying It Works

After the update, test with a simple command like:
```
"List all my Filament resources"
```

Check the token count in the response - you should see significant reduction compared to before.

## When to Customize .cliignore

You may want to edit `.cliignore` to add project-specific exclusions:
- Custom documentation directories
- Generated code directories
- Large data/fixture files
- Legacy code sections not actively being worked on
- Third-party integrations that don't need AI context

## Important Notes

- **Safe to run multiple times**: Won't break existing configuration
- **Preserves your customizations**: Only adds/updates specific files
- **No restart required**: Changes take effect immediately
- **Reversible**: Can delete .cliignore to disable token filtering
