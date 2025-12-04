# Update Existing .claude Configuration with Enhanced Context Management

Use this prompt when you already have a `.claude/` directory but want to add:
1. The new `.cliignore` token optimization 
2. Session health monitoring
3. Context anchors for long sessions

```bash
claude-code "Update my existing .claude configuration to add context management and .cliignore:

1. Check if .cliignore already exists in the project root
   - If it exists, ask if I want to overwrite it
   - If it doesn't exist, proceed with copying

2. Copy .cliignore from ~/Clients/Sites/claude-setup/.cliignore to project root
   - This file contains optimized exclusions for Laravel + Filament projects
   - Read composer.json to verify installed packages  
   - Read package.json to verify Node dependencies
   - Confirm the .cliignore contents are appropriate for this project

3. CRITICAL INSTRUCTION - Documentation Location:
   - Add this rule to project practices: ALL project notes, tasks, documentation, and logs created by Claude MUST be stored in .claude/ directory
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

4. Update .claude/project-info.md to add CRITICAL CONTEXT SECTION if not already present:
   
   Add at the VERY TOP (before all other content):
   
   ```markdown
   ## ⚠️ CRITICAL - READ THIS FIRST BEFORE EVERY RESPONSE
   
   **You MUST verify these facts before making ANY code changes:**
   
   - **Filament Version**: [existing version from file]
   - **Laravel Version**: [existing version from file]
   - **Livewire Version**: [existing version from file]
   - **PHP Version**: [existing version from file]
   - **Tailwind Version**: [existing version from file]
   - **Database**: [existing from file]
   
   ### Common Mistakes to AVOID:
   - Using Filament v4 syntax when project is v3 (e.g., Record $record vs $record)
   - Using wrong Livewire syntax for version
   - Assuming different PHP version features
   - Using wrong Tailwind classes for version
   
   ### Before Every Code Change - Self Check:
   1. Have I checked the Filament version above?
   2. Have I checked which Livewire version is installed?
   3. Am I using the correct syntax for this version?
   4. Have I reviewed existing code patterns in conventions.md?
   
   ---
   ```
   
   **Important**: Move existing content below this critical section.

5. Create .claude/session-health.md for context monitoring:
   
   ```markdown
   # Session Health Monitoring for Claude Code
   
   ## Purpose
   Helps maintain context quality during extended Claude Code sessions.
   
   ## Check Every 20-30 Messages
   
   ### Context Awareness Check
   - [ ] Can I accurately state the Filament version from project-info.md?
   - [ ] Do I remember the last 3 changes I made?
   - [ ] Am I following conventions in conventions.md?
   - [ ] Am I using correct syntax for the detected versions?
   
   ### Code Quality Check
   - [ ] Using correct Filament [VERSION] class names and patterns?
   - [ ] Maintaining consistency with earlier changes?
   - [ ] Haven't repeated any mistakes from earlier in session?
   
   ### Warning Signs (Suggest fresh session)
   - Making same mistake twice
   - Using wrong version syntax repeatedly
   - Unable to recall project versions accurately
   - Contradicting earlier decisions
   - Circular problem-solving
   
   ## If Context Feels Degraded
   
   **Tell the user:**
   \"I notice we've been working for a while. To ensure I maintain accuracy 
   with Filament [version] syntax and project conventions, I recommend:
   1. Review what we've completed
   2. Document current state  
   3. Start a fresh session with explicit version reminders
   
   This helps prevent expensive mistakes from context degradation.\"
   
   ## For Long Sessions (50+ messages)
   
   Proactively suggest:
   1. Reviewing completed work
   2. Creating a checkpoint
   3. Starting fresh with context reminders
   ```

6. Create .claude/context-anchors.md with project-specific reminders:
   
   ```markdown
   # Context Anchors for User
   
   ## What Are Context Anchors?
   
   Short reminders you give Claude Code every 15-20 messages to keep context fresh.
   
   ## Recommended Anchors for This Project
   
   ### Quick Version Check (Use every 15-20 messages)
   \"Quick reminder: this project uses Filament [VERSION from project-info.md]\"
   \"Remember: Filament [VERSION], not v4\" (if applicable)
   \"Check .claude/project-info.md critical section before continuing\"
   
   ### Pattern Reminder
   \"Following our conventions in .claude/conventions.md\"
   \"Using the patterns we established earlier\"
   \"Maintaining consistency with existing code\"
   
   ### Before Big Changes
   \"Before implementing: verify correct Filament version, check existing patterns\"
   \"Check project-info.md critical section and conventions.md\"
   
   ## Cost-Benefit Analysis
   
   - **Cost of anchor**: ~50 tokens per reminder
   - **Cost of fixing repeated mistake**: 500-1000 tokens + debugging time
   - **Cost of undoing work**: 1000+ tokens + frustration
   - **ROI**: 10-20x by preventing mistakes
   
   ## When to Use
   
   - After 15-20 message exchanges
   - Before starting a major feature
   - When switching between different parts of codebase
   - If you notice Claude using wrong syntax
   - Beginning of each new coding session
   - After breaks or context switches
   
   ## Example Usage Patterns
   
   ### Starting a Session
   \"Working on [feature]. Reminder: Filament [VERSION], check .claude/project-info.md\"
   
   ### Mid-Session
   \"Quick context check: what Filament version and what were our last 3 changes?\"
   
   ### After a Mistake
   \"That's Filament v4 syntax - we're on v3. See .claude/project-info.md critical section\"
   
   ### Before Complex Change
   \"Before we implement this, verify versions and review conventions.md\"
   ```

7. Create .claude/cliignore-guide.md with comprehensive documentation:
   - Purpose of .cliignore file (reduces token usage by 50-70%)
   - What files are excluded and why
   - Specific exceptions allowed:
     * Can reference vendor/filament/ when debugging Filament-specific issues
     * Can reference specific vendor packages when integration issues arise  
     * Can access vendor/ temporarily if explicitly requested by user
   - Instructions for Claude Code:
     * Honor .cliignore exclusions by default in all operations
     * Do not read, analyze, or include ignored files in context unless:
       - User explicitly grants exception (e.g., \"You can check vendor/filament/...\")
       - User specifically requests to see a file in an ignored directory
       - Debugging requires tracing into vendor code temporarily
     * Always ask permission before accessing ignored directories
   - Additional token optimization tips:
     * Use Task/Explore agents for broad codebase searches
     * Read files selectively rather than entire directories
     * For large files, use offset/limit parameters
     * Exclude test directories when not working on tests
     * Exclude migration files when only working on features
   - How to customize .cliignore for project-specific needs

8. Update .claude/README.md to add sections about:
   - **NEW: Context Management Strategy**
     * Why it matters for Claude Code CLI
     * Session health monitoring
     * Using context anchors
     * When to start fresh sessions
   - **NEW: Long Session Best Practices**
     * Check session-health.md every 20-30 messages
     * Use context anchors every 15-20 messages
     * Watch for warning signs
     * Don't fight degradation - restart earlier
   - Token optimization with .cliignore
   - Reference to cliignore-guide.md for detailed usage
   - Balance between context and token efficiency
   - Available MCP servers and capabilities
   
   Add section:
   ```markdown
   ## Context Management for Long Sessions
   
   Claude Code can experience context degradation in extended sessions, 
   leading to repeated mistakes and wasted tokens. This configuration 
   includes tools to prevent this:
   
   ### Session Health Monitoring
   - See `.claude/session-health.md` for self-check questions
   - Claude should reference this every 20-30 messages
   - Watch for warning signs of context degradation
   
   ### Context Anchors
   - See `.claude/context-anchors.md` for reminder templates
   - Use every 15-20 messages to keep context fresh
   - Costs ~50 tokens but prevents 500-1000 token mistakes
   - 10-20x ROI on preventing repeated errors
   
   ### When to Start Fresh
   - Same mistake repeated twice
   - Wrong version syntax used repeatedly  
   - After 50+ message exchanges
   - When context feels \"fuzzy\" or uncertain
   
   ### Cost Management
   - Context anchor: ~50 tokens
   - Prevented mistake: saves 500-1000 tokens
   - Fresh session with reminder: ~100 tokens
   - Fixing repeated mistakes: 1000+ tokens + time
   
   **Bottom line**: Proactive context management is 10-20x cheaper than 
   fixing mistakes from degraded context.
   ```

9. Update .claude/conventions.md (if needed) to add version-specific sections:
   - Check if it has version-specific pattern documentation
   - If not, add section headers for Filament version patterns
   - Add section for common version gotchas
   - Document version-specific syntax patterns

After updating, show me:
- Confirmation that .cliignore was copied
- Confirmation that CRITICAL section was added to project-info.md
- List of what's being excluded by .cliignore
- Summary of new context management files created:
  * session-health.md
  * context-anchors.md
  * cliignore-guide.md
- Summary of what was added to README.md
- Example context anchors specific to this project's versions
- Estimated token savings from .cliignore
- **NEW: Instructions for using context management in daily work**
- **NEW: Warning signs to watch for during sessions**
- **NEW: Cost-benefit analysis of context anchors vs mistakes**
- Any recommendations for customizing .cliignore for this project"
```

## What This Update Adds

### 1. Context Management Files
- **session-health.md** - Self-monitoring for Claude Code
- **context-anchors.md** - Reminder templates for you
- Enhanced README with context strategy

### 2. Critical Section in project-info.md
- Moves versions to very top
- Adds self-check questions
- Lists common mistakes to avoid

### 3. Version-Specific Documentation
- Updates conventions.md with version headers
- Adds gotcha sections
- Documents version-specific patterns

### 4. Token Optimization
- Copies .cliignore (as before)
- Adds comprehensive cliignore-guide.md
- Documents exclusion strategy

## Usage After Update

**Start of each session:**
```bash
claude "Working on [feature]. Reminder: check .claude/project-info.md for versions"
```

**Every 15-20 messages:**
```bash
"Context anchor: Filament [version], following conventions.md"
```

**If mistake happens:**
```bash
"That's wrong version syntax - check .claude/project-info.md critical section"
```

**Long session (30+ messages):**
```bash
"Check .claude/session-health.md - are we maintaining context quality?"
```

## Before and After

**Before update:**
- No systematic context management
- Version info buried in file
- No reminder strategy
- Context degradation undetected until mistakes happen

**After update:**
- CRITICAL section at top of project-info.md
- Session health monitoring
- Context anchor templates
- Proactive degradation detection
- Token optimization via .cliignore

## What Problems This Solves

✅ **Forgetting Filament versions**: Critical section at top  
✅ **Repeated mistakes**: Session health monitoring catches early  
✅ **High token costs**: Anchors prevent mistakes, .cliignore reduces usage  
✅ **Context degradation**: Detected before causing expensive mistakes  
✅ **Frustration**: Clear process for maintaining quality  

This update transforms your existing setup into a context-managed system without 
disrupting your current project structure.

Ready for the enhanced README.md?
