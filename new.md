# Claude Code Setup for New TALL Stack + Filament Project (Enhanced)

Use this prompt with Claude Code to configure optimal settings for a new project with built-in context management:

```bash
claude-code "Set up Claude Code configuration for a new TALL stack + Filament project with context management:

1. Create a .claude/ directory

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

4. Create .claude/project-info.md with CRITICAL CONTEXT SECTION template:
   
   ```markdown
   # Project Information
   
   ## ⚠️ CRITICAL - READ THIS FIRST BEFORE EVERY RESPONSE
   
   **You MUST verify these facts before making ANY code changes:**
   
   - **Filament Version**: [TO BE FILLED - v3 or v4?] ⚠️ UPDATE AFTER INSTALLATION
   - **Laravel Version**: [TO BE FILLED] ⚠️ UPDATE AFTER INSTALLATION
   - **Livewire Version**: [TO BE FILLED] ⚠️ UPDATE AFTER INSTALLATION  
   - **PHP Version**: [TO BE FILLED] ⚠️ UPDATE AFTER INSTALLATION
   - **Tailwind Version**: [TO BE FILLED - v3 or v4?] ⚠️ UPDATE AFTER INSTALLATION
   - **Database**: MySQL (assumed for TALL stack)
   
   ### ⚠️ IMPORTANT: Update versions IMMEDIATELY after installation!
   
   ### Common Mistakes to AVOID:
   - Using Filament v4 syntax when project is v3 (e.g., Record $record vs $record)
   - Using wrong Livewire syntax for version
   - Assuming different PHP version features
   - Using wrong Tailwind classes for version
   
   ### Before Every Code Change - Self Check:
   1. Have I checked the Filament version above?
   2. Have I checked which Livewire version is installed?
   3. Am I using the correct syntax for this version?
   4. Have I reviewed conventions.md for established patterns?
   
   ### After Stack Installation:
   **Run the setup command again to auto-detect and fill in versions!**
   
   ---
   
   ## Stack Details (Templates)
   - Laravel version: [TBD]
   - Alpine.js version: [TBD]
   - Livewire version: [TBD]
   - Tailwind CSS version: [TBD - v3 or v4]
   - Filament version: [TBD - v3 or v4]
   - PHP version: [TBD]
   - Database driver: MySQL (default assumption)
   - Development environment: Laravel Herd
   ```

5. Create .claude/conventions.md with TALL stack best practices template AND version placeholders:
   
   ```markdown
   # Project Conventions
   
   ## ⚠️ UPDATE AFTER STACK INSTALLATION
   This file should be updated with actual versions and patterns after installing the stack.
   
   ## Filament Version-Specific Patterns
   
   **This project uses Filament [VERSION TO BE DETERMINED]**
   
   ### Resource Structure (Filament [VERSION])
   [Will be filled in as patterns emerge]
   
   ### Form/Table Patterns (Filament [VERSION])
   [Will be filled in with version-specific syntax]
   
   ### Version-Specific Gotchas
   - [Add as discovered]
   
   ## Livewire Patterns
   
   **This project uses Livewire [VERSION TO BE DETERMINED]**
   
   ### Component Organization
   - Class-based vs inline views
   - [Add patterns as established]
   
   ## Alpine.js Usage Guidelines
   - When to use Alpine vs Livewire
   - [Add patterns as established]
   
   ## Tailwind CSS Approach
   - Utility-first patterns
   - [Add as established]
   
   ## Laravel Coding Standards
   - PSR-12 compliance
   - Naming conventions
   - [Add as established]
   
   ## Database Conventions
   - Migration patterns
   - Model conventions
   - [Add as established]
   
   ## Enum Usage
   - For status, type, role fields
   - [Add as patterns emerge]
   
   ## Git Workflow
   - Branching strategy
   - [Add as established]
   ```

6. Create .claude/session-health.md for monitoring context during development:
   
   ```markdown
   # Session Health Monitoring for Claude Code
   
   ## Purpose
   Helps maintain context quality during extended Claude Code sessions.
   
   ## ⚠️ AFTER STACK INSTALLATION: Update with actual versions!
   
   ## Check Every 20-30 Messages
   
   ### Context Awareness Check
   - [ ] Can I accurately state the Filament version? (Check project-info.md)
   - [ ] Do I remember the last 3 changes I made?
   - [ ] Am I following conventions documented in conventions.md?
   - [ ] Am I using correct syntax for the versions installed?
   
   ### Code Quality Check
   - [ ] Using correct Filament [VERSION] syntax?
   - [ ] Maintaining consistency with earlier changes?
   - [ ] No repeated mistakes from earlier in session?
   
   ### Warning Signs (Suggest fresh session)
   - Making same mistake twice
   - Using wrong version syntax
   - Can't recall project versions
   - Contradicting earlier decisions
   
   ## During Initial Setup
   
   Until versions are installed and filled in:
   - Remind user to update project-info.md after each package install
   - Don't make assumptions about versions
   - Ask before using version-specific syntax
   
   ## After Versions Filled In
   
   - Reference project-info.md critical section frequently
   - Self-check version syntax before every code change
   - Watch for context degradation signs
   
   ## If Context Feels Degraded
   
   **Tell the user:**
   \"I notice we've been working for a while. To maintain accuracy with 
   version syntax and project conventions, I recommend documenting current 
   state and starting a fresh session with explicit version reminders.\"
   ```

7. Create .claude/context-anchors.md with templates to fill after installation:
   
   ```markdown
   # Context Anchors for User
   
   ## What Are Context Anchors?
   Short reminders to keep Claude Code's context fresh during long sessions.
   
   ## ⚠️ UPDATE THESE AFTER STACK INSTALLATION
   
   Replace [VERSION] placeholders with actual versions after installation.
   
   ## Recommended Anchors for This Project
   
   ### Quick Version Check (Use every 15-20 messages)
   \"Quick reminder: Filament [VERSION], Livewire [VERSION]\"
   \"Check .claude/project-info.md for versions before continuing\"
   
   ### Pattern Reminder
   \"Following conventions in .claude/conventions.md\"
   \"Using patterns we established earlier\"
   
   ### Before Big Changes
   \"Verify: correct versions, existing patterns before implementing\"
   \"Check project-info.md critical section\"
   
   ## During Initial Development (Before patterns established)
   \"Document any new patterns in .claude/conventions.md\"
   \"Update conventions.md as we establish patterns\"
   
   ## Cost Analysis
   - **Cost of anchor**: ~50 tokens
   - **Cost of fixing mistake**: 500-1000 tokens
   - **ROI**: 10-20x by preventing mistakes
   
   ## When to Use
   - After 15-20 messages
   - Before major features
   - When switching codebase areas
   - If wrong syntax appears
   - Start of each session
   - **During installation**: After each package install
   ```

8. Create .claude/context.md template:
   - Project purpose (to be filled in)
   - Target audience/use case  
   - Key features to build
   - Special requirements or constraints
   - Custom packages or integrations planned
   - Authentication/authorization approach
   - Deployment strategy

9. Create .claude/setup-checklist.md with version-tracking reminders:
   
   ```markdown
   # New Project Setup Checklist
   
   ## Critical: Update .claude/project-info.md after EACH step!
   
   ### 1. Laravel Installation
   - [ ] Install Laravel
   - [ ] **Immediately update project-info.md with Laravel version**
   - [ ] Run: composer show laravel/framework | grep versions
   
   ### 2. Filament Installation  
   - [ ] Install Filament (v3 or v4)
   - [ ] **⚠️ CRITICAL: Update project-info.md with Filament version**
   - [ ] Run: composer show filament/filament | grep versions
   - [ ] This is the MOST IMPORTANT version to track!
   
   ### 3. Livewire Setup
   - [ ] Verify Livewire installation (comes with Filament)
   - [ ] **Update project-info.md with Livewire version**
   - [ ] Run: composer show livewire/livewire | grep versions
   
   ### 4. Tailwind CSS Installation
   - [ ] Install Tailwind (v3 or v4)
   - [ ] **Update project-info.md with Tailwind version**
   - [ ] Check package.json
   
   ### 5. Alpine.js Integration
   - [ ] Verify Alpine.js (comes with Livewire)
   - [ ] **Update project-info.md with Alpine version**
   - [ ] Check package.json
   
   ### 6. After ALL installations complete:
   - [ ] **Run the Claude Code setup command AGAIN**
   - [ ] This will auto-detect and fill in all versions
   - [ ] Verify project-info.md critical section is complete
   - [ ] Copy .cliignore file
   
   ### 7. Database Configuration
   - [ ] Configure .env
   - [ ] Create database
   - [ ] Run first migration
   
   ### 8. Git Setup
   - [ ] Initialize repository
   - [ ] Verify .gitignore includes .claude/
   - [ ] Initial commit
   
   ### 9. Laravel Herd Setup
   - [ ] Add site to Herd
   - [ ] Configure PHP version
   - [ ] Test site access
   
   ### 10. Final Verification
   - [ ] All versions in project-info.md are filled in
   - [ ] Filament version is CONFIRMED (v3 or v4)
   - [ ] .cliignore is in place
   - [ ] Ready for development!
   ```

10. Set up MCP servers:
   - Configure Laravel Herd MCP server
   - Configure Laravel Boost MCP server
   - Create configuration at ~/Library/Application Support/Claude/claude_desktop_config.json
   - Configuration example with both servers

11. Create .claude/mcp-setup.md documenting MCP configuration

12. Create .claude/cliignore-guide.md documenting token optimization
    - NOTE: .cliignore will be copied AFTER running setup again post-installation

13. Add a .claude/README.md explaining:
    - What these configuration files are for
    - **NEW: Two-phase setup process (before and after installation)**
    - **NEW: Critical importance of updating versions**
    - **NEW: Context management during initial development**
    - **NEW: Using session-health.md and context anchors**
    - How to keep files updated as project evolves
    - Best practices for Claude Code on TALL stack projects
    - Available MCP servers and capabilities
    - Common workflows
    - **NEW: How to prevent context degradation during development**

After setup, show me:
- Summary of created template files
- **NEW: Big red warning about updating versions after installation**
- **NEW: Reminder to run setup AGAIN after stack installation**
- MCP server installation status
- Test commands for MCP servers
- Checklist of information to provide during installation
- **NEW: Example context anchors (with version placeholders)**
- **NEW: Instructions for maintaining context during initial development**
- Next steps for project initialization"
```

## Key Enhancements for New Projects

### 1. Two-Phase Setup
- **Phase 1**: Before installation - creates templates
- **Phase 2**: After installation - fills in versions and copies .cliignore

### 2. Version Placeholders
- All version fields marked with ⚠️ UPDATE AFTER INSTALLATION
- Critical section has placeholder warnings
- Reminders throughout to update versions

### 3. Setup Checklist Integration
- Links version updates to installation steps
- Reminds to update project-info.md after EACH package install
- Emphasizes Filament version as MOST critical

### 4. Context Management from Day 1
- Session health monitoring starts from first session
- Context anchors available with placeholders
- Conventions documented as patterns emerge

## Usage Pattern for New Projects

**Initial Setup (before installing Laravel):**
```bash
claude-code "Run the new project setup from claude-setup/new.md"
```

**After installing Laravel:**
```bash
"Just installed Laravel 11.x - updating .claude/project-info.md"
```

**After installing Filament (CRITICAL!):**
```bash
"Installed Filament v3.2 - UPDATING .claude/project-info.md critical section"
```

**After ALL packages installed:**
```bash
claude-code "Run the setup command again to auto-detect all versions and copy .cliignore"
```

**During development:**
- Use context anchors every 15-20 messages
- Reference .claude/conventions.md as patterns emerge
- Update conventions.md with new patterns

## What This Solves

✅ **Version tracking from start**: Templates force version awareness  
✅ **Two-phase setup**: Prevents assumptions, forces verification  
✅ **Context from day 1**: Management practices from first session  
✅ **Pattern documentation**: Conventions build as project grows  
✅ **Prevents mistakes**: Critical section enforces version checks  

Next: update-cliignore.md and README.md?
