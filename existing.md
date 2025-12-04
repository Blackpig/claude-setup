# Claude Code Setup for Existing TALL Stack + Filament Project (Enhanced)

Use this prompt with Claude Code to configure optimal settings for an existing project with context management to prevent version confusion and repeated mistakes:

```bash
claude-code "Set up optimal Claude Code configuration for this TALL stack + Filament project:

1. Create a .claude/ directory if it doesn't exist

2. Create or update .gitignore to protect sensitive project context:
   - Check if .gitignore exists, create if it doesn't
   - Add '.claude/' to .gitignore if not already present
   - Add a comment explaining why: '# Claude Code configuration (contains project-specific context)'

3. CRITICAL INSTRUCTION - Documentation Location:
   - ALL project notes, tasks, documentation, and logs created by Claude MUST be stored in .claude/ directory
   - NEVER create documentation files in project root or other directories
   - Valid locations for Claude-created documentation:
     * .claude/notes.md - General project notes
     * .claude/tasks.md - Task lists and todos
     * .claude/decisions.md - Architectural decisions
     * .claude/changelog.md - Work log and changes
     * .claude/debug-notes.md - Debugging notes
     * .claude/[any-other-name].md - Any other documentation
   - INVALID locations: root directory, docs/, notes/, or anywhere outside .claude/
   - Exception: README.md in root is acceptable only if specifically requested
   - This keeps project clean and documentation organized in one place

4. Analyze the project to detect current versions and configuration by reading:
   - composer.json for Laravel, Livewire, Filament versions
   - package.json for Tailwind CSS, Alpine.js versions
   - config/filament.php if it exists
   - tailwind.config.js for Tailwind configuration
   - .env for database driver (DB_CONNECTION) and note that it's typically MySQL
   - Detect that local development is managed by Laravel Herd

5. Create .claude/project-info.md with CRITICAL CONTEXT SECTION at the top:
   
   Structure it as:
   
   ```markdown
   # Project Information
   
   ## ⚠️ CRITICAL - READ THIS FIRST BEFORE EVERY RESPONSE
   
   **You MUST verify these facts before making ANY code changes:**
   
   - **Filament Version**: [detected version] (NOT v4 if this is v3!)
   - **Laravel Version**: [detected version]
   - **Livewire Version**: [detected version]
   - **PHP Version**: [detected version]
   - **Tailwind Version**: [detected version]
   - **Database**: [detected from .env]
   
   ### Common Mistakes to AVOID:
   - Using incorrect Filament version for the project e.g. v3 namespace or syntax when the project is v4 (e.g., Record $record vs $record)
   - Using wrong Livewire syntax for version
   - Assuming different PHP version features
   - Using wrong Tailwind classes for version
   
   ### Before Every Code Change - Self Check:
   1. Have I checked the Filament version above?
   2. Have I checked which Livewire version is installed?
   3. Am I using the correct syntax for this version?
   4. Have I reviewed existing code patterns in conventions.md?
   
   ---
   
   ## Stack Details
   [Rest of detected information]
   ```

6. Create .claude/conventions.md with VERSION-SPECIFIC PATTERNS:
   
   Structure it to include:
   
   ```markdown
   # Project Conventions
   
   ## Filament Version-Specific Patterns
   
   **This project uses Filament [version]**
   
   ### Resource Structure (Filament [version])
   [Document existing patterns with version notes]
   
   ### Form/Table Patterns (Filament [version])
   [Document with explicit version syntax]
   
   ### Common Version Gotchas
   - [List version-specific issues found in this project]
   
   ## Livewire Patterns
   
   **This project uses Livewire [version]**
   [Document existing patterns]
   
   ## Code Patterns Found in Codebase
   [Analyze and document existing patterns]
   
   ## Naming Conventions
   [Document observed conventions]
   
   ## Database Conventions
   [Document migration and model patterns]
   
   ## Enum Usage
   [Document existing enum patterns from app/Enums/]
   ```

7. Create .claude/context.md for:
   - Project overview and purpose
   - Key architectural decisions
   - Custom components or packages being used
   - Any special configuration or setup notes
   - Laravel Herd site configuration details
   - Known issues or quirks in this specific project

8. Create .claude/session-health.md for monitoring context during long sessions:
   
   ```markdown
   # Session Health Monitoring
   
   ## Purpose
   This file helps you (Claude Code) maintain context quality during extended sessions.
   
   ## Check Every 20-30 Messages
   
   Ask yourself these questions:
   
   ### Context Awareness Check
   - [ ] Can I accurately state the Filament version from project-info.md?
   - [ ] Do I remember the last 3 changes I made?
   - [ ] Am I still following the conventions in conventions.md?
   - [ ] Have I used the correct syntax for the detected versions?
   
   ### Code Quality Check
   - [ ] Am I using correct class names for this Filament version?
   - [ ] Am I maintaining consistency with earlier changes?
   - [ ] Have I avoided repeating any mistakes from earlier in this session?
   
   ### Warning Signs (Suggest /reset or new session)
   - Making the same mistake twice
   - Using wrong version syntax repeatedly
   - Unable to recall project versions accurately
   - Contradicting earlier decisions
   
   ## If Context Feels Degraded
   
   **Tell the user:**
   "I notice we've been working for a while. To ensure I maintain accuracy with 
   Filament [version] syntax and project conventions, I recommend:
   1. Review what we've completed
   2. Document current state
   3. Start a fresh session with explicit version reminders
   
   This helps prevent expensive mistakes from context degradation."
   ```

9. Create .claude/context-anchors.md with reminders to use:
   
   ```markdown
   # Context Anchors for User
   
   ## What Are Context Anchors?
   
   Short reminders you can give Claude Code every 15-20 messages to keep context fresh.
   
   ## Recommended Anchors for This Project
   
   Every 15-20 messages, say one of these:
   
   ### Quick Version Check
   "Quick reminder: this project uses Filament [version], not v4"
   "Remember: Filament [version] syntax, check project-info.md"
   
   ### Pattern Reminder  
   "Following our conventions in .claude/conventions.md"
   "Using the patterns we established earlier"
   
   ### Before Big Changes
   "Before implementing, verify: correct Filament version, existing patterns"
   "Check project-info.md critical section before proceeding"
   
   ## Cost Analysis
   
   - **Cost of anchor**: ~50 tokens
   - **Cost of fixing repeated mistake**: 500-1000 tokens + time
   - **ROI**: 10-20x by preventing mistakes
   
   ## When to Use
   
   - After 15-20 message exchanges
   - Before starting a major feature
   - When switching between different parts of codebase
   - If you notice Claude using wrong syntax
   - Beginning of each new coding session
   ```

10. Set up MCP servers by creating the Claude Desktop configuration:
   - Configure Laravel Herd MCP server (built into Herd)
   - Configure Laravel Boost MCP server (runs via npx, no installation needed)
   - Create configuration at ~/Library/Application Support/Claude/claude_desktop_config.json
   - Note: Only Herd and Boost MCP servers are currently stable and recommended
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

11. Create .claude/mcp-setup.md documenting:
    - MCP server configuration details
    - How to restart Claude Desktop to activate MCP servers
    - Test commands for each server
    - Common use cases and workflows
    - Troubleshooting guide

12. FINAL STEP - Copy .cliignore file to optimize token usage:
    - Copy .cliignore from ~/Clients/Sites/claude-setup/.cliignore to project root
    - This file contains optimized exclusions for Laravel + Filament projects
    - Read composer.json to detect installed packages and versions
    - Read package.json to detect Node dependencies
    - Verify the .cliignore contents are appropriate for this project
    - This is created AFTER analyzing project structure

13. Create .claude/cliignore-guide.md documenting:
    - Purpose of .cliignore file (reduces token usage by 50-70%)
    - What files are excluded and why
    - Specific exceptions allowed (vendor/filament/ when debugging, etc.)
    - Instructions for Claude Code on honoring exclusions
    - Additional token optimization tips

14. Add a .claude/README.md explaining:
    - What these files are for
    - How to keep them updated
    - **NEW: Context management strategy**
    - **NEW: How to use session-health.md**
    - **NEW: When to use context anchors**
    - Best practices for long Claude Code sessions
    - Available MCP servers and their capabilities
    - How to prevent context degradation and repeated mistakes

After creating these files, show me:
- Summary of detected versions with EMPHASIS on Filament version
- Confirmation that CRITICAL section is at top of project-info.md
- Database connection details
- MCP server installation status
- Confirmation that .cliignore was copied
- **NEW: Instructions for context management during long sessions**
- **NEW: Example context anchors specific to this project's versions**
- **NEW: Warning signs to watch for during extended sessions**
- Estimated token savings from .cliignore
- Next steps for maintaining context quality"
```

## Key Enhancements for Claude Code CLI

### 1. Critical Context Section
- Puts versions at the VERY TOP of project-info.md
- Claude Code reads this first in every session
- Explicit warnings about common version mistakes

### 2. Session Health Monitoring
- New file: `.claude/session-health.md`
- Self-check questions for Claude Code
- Warning signs of context degradation
- When to suggest starting fresh

### 3. Context Anchors
- New file: `.claude/context-anchors.md`
- Short reminders for you to use every 15-20 messages
- Costs ~50 tokens but prevents 500-1000 token mistakes
- Project-specific anchor examples

### 4. Version-Specific Conventions
- Enhanced conventions.md structure
- Explicitly documents version-specific patterns
- Lists common version gotchas
- Makes version central to every pattern

## Usage Pattern

**Start of session:**
```bash
claude "Working on [feature]. Reminder: Filament [version], check .claude/project-info.md"
```

**Every 15-20 messages:**
```bash
"Quick check: what Filament version are we using?"
# or
"Reminder: following conventions in .claude/conventions.md"
```

**When Claude makes mistake:**
```bash
"That's Filament v4 syntax - we're on v3. Check .claude/project-info.md critical section"
```

## What This Solves

✅ **Version confusion**: Critical section always at top  
✅ **Repeated mistakes**: Session health monitoring  
✅ **Context degradation**: Anchor reminders every 15-20 messages  
✅ **High costs**: Prevention is cheaper than fixing  
✅ **Frustration**: Clear process for maintaining quality  

## Quick Reference

**Every New Session:**
1. Open with version reminder
2. Reference .claude/ files explicitly

**Every 15-20 Messages:**
1. Use a context anchor
2. Quick version check

**If Mistakes Happen:**
1. Point to project-info.md critical section
2. Reference conventions.md
3. Consider starting fresh if repeated

**Long Sessions (50+ messages):**
1. Check session-health.md
2. Document current state
3. Consider fresh start with handoff

Want me to continue with the other files (new.md, update-cliignore.md, README.md)?
