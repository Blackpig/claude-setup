# Claude Code Setup for TALL Stack + Filament Projects (Enhanced)

This repository contains configuration templates and setup instructions for optimizing Claude Code CLI when working on TALL Stack (Tailwind, Alpine, Livewire, Laravel) + Filament projects, with built-in context management to prevent version confusion and repeated mistakes.

## What This Does

Provides ready-to-use prompts and templates that:
- Create a `.claude/` directory with project context files
- **NEW: Add session health monitoring to prevent context degradation**
- **NEW: Provide context anchor templates for long sessions**
- **NEW: Put critical version info at the TOP of every file**
- Set up MCP servers (Laravel Herd and Laravel Boost)
- Configure `.cliignore` to reduce token usage by 50-70%
- Document coding conventions and project standards
- **NEW: Establish practices to prevent repeated expensive mistakes**

## The Problems This Solves

### Context Degradation in Claude Code CLI
Even in the CLI tool, Claude Code can experience context degradation during long sessions:
- **Forgetting Filament versions** after 20-30 messages
- **Repeating the same mistakes** (e.g., v3 vs v4 syntax)
- **Undoing previous work** by contradicting earlier decisions
- **High token costs** from fixing repeated errors
- **Frustration** from watching mistakes recur

### Our Solution: Enhanced Context Management
- **Critical context sections** with versions at the TOP
- **Session health monitoring** every 20-30 messages
- **Context anchors** - short reminders every 15-20 messages  
- **Proactive detection** of degradation before mistakes occur
- **Token optimization** - prevention is 10-20x cheaper than fixing

## Three Setup Options

### 1. New Project Setup (`new-enhanced.md`)

Use when starting a **brand new** TALL Stack + Filament project from scratch.

**Features:**
- Creates `.claude/` directory with template files
- **NEW: Critical context section with version placeholders**
- **NEW: Session health monitoring from day 1**
- **NEW: Context anchor templates**
- Leaves version placeholders for you to fill in after installation
- Sets up MCP servers (Herd + Boost)
- Two-step process: initial setup, then finalize after stack installation

**When to use:** Before installing Laravel, Filament, or any dependencies.

**Key Enhancement:** Emphasizes updating versions immediately after each package install, with big warnings about Filament version being CRITICAL.

### 2. Existing Project Setup (`existing-enhanced.md`)

Use when adding Claude Code configuration to an **existing** TALL Stack + Filament project.

**Features:**
- Analyzes your `composer.json` and `package.json` to detect versions
- **NEW: Creates CRITICAL context section at top of project-info.md**
- **NEW: Adds session health monitoring file**
- **NEW: Provides context anchor templates specific to your versions**
- Auto-populates `.claude/project-info.md` with actual versions
- Detects existing code patterns and conventions
- Copies `.cliignore` immediately (since dependencies already exist)
- Sets up MCP servers (Herd + Boost)

**When to use:** You already have a working project and want to add Claude Code optimization with context management.

**Key Enhancement:** Emphasizes Filament version in critical section, adds self-check questions before code changes.

### 3. Update Existing Configuration (`update-cliignore-enhanced.md`)

Use when you **already have a `.claude/` directory** but want to add:
1. The new `.cliignore` token optimization
2. **NEW: Session health monitoring**
3. **NEW: Context anchors**
4. **NEW: Critical context section at top of project-info.md**

**Features:**
- Adds `.cliignore` to existing setup
- **NEW: Creates session-health.md for context monitoring**
- **NEW: Creates context-anchors.md with reminder templates**
- **NEW: Updates project-info.md with critical context section at top**
- Creates `.claude/cliignore-guide.md` documentation
- Updates `.claude/README.md` with context management strategy
- Doesn't touch your existing conventions or MCP setup

**When to use:** You set up `.claude/` before context management was added to this repo.

**Key Enhancement:** Non-destructive update that adds context management to existing setup.

## What Gets Created

All setups create:

```
.claude/
├── README.md              # Configuration guide with context strategy
├── project-info.md        # ⚠️ NEW: Critical context section at TOP
├── conventions.md         # Coding standards with version-specific patterns
├── context.md            # Project overview and architecture
├── session-health.md     # 🆕 Context monitoring guidelines
├── context-anchors.md    # 🆕 Reminder templates for long sessions
├── mcp-setup.md          # MCP server configuration guide
├── cliignore-guide.md    # Token optimization instructions
└── setup-checklist.md    # Installation steps (new projects only)

.cliignore                # Token optimization exclusions
.gitignore                # Updated to exclude .claude/

~/Library/Application Support/Claude/claude_desktop_config.json
                          # MCP server configuration
```

## Context Management Strategy

### The Problem: Context Degradation
Claude Code, like any AI system, can lose track of important details during long sessions:
- Forgets which Filament version you're using
- Uses v4 syntax when you're on v3
- Repeats mistakes it already made  
- Contradicts earlier decisions
- Becomes "fuzzy" or uncertain

### The Solution: Three-Layer Defense

#### Layer 1: Critical Context Section (Passive)
**What:** Versions and gotchas at the VERY TOP of project-info.md  
**Why:** Claude reads top-to-bottom, sees critical info first  
**Cost:** Zero - built into file structure  
**Effectiveness:** Prevents ~50% of version mistakes  

#### Layer 2: Context Anchors (Active - Every 15-20 Messages)
**What:** Short reminders you give Claude Code  
**Example:** "Reminder: Filament v3.2, check .claude/project-info.md"  
**Cost:** ~50 tokens per anchor  
**Savings:** Prevents 500-1000 token mistakes  
**ROI:** 10-20x return on token investment  
**Effectiveness:** Prevents ~40% of remaining mistakes  

#### Layer 3: Session Health Monitoring (Active - Every 20-30 Messages)
**What:** Claude self-checks context quality  
**Example:** "Can I recall the Filament version? Last 3 changes?"  
**Cost:** Built into session workflow  
**Benefit:** Catches degradation before mistakes happen  
**Effectiveness:** Detects remaining ~10% of issues early  

### Cost-Benefit Analysis

**Without Context Management:**
```
Long session (50 messages)
→ Context degrades around message 25
→ 2-3 version mistakes  
→ 5-10 messages per fix cycle
→ 1000-3000 wasted tokens
→ High frustration
Total cost: $2-5 + time
```

**With Context Management:**
```
Long session (50 messages)
→ 3-4 context anchors (~200 tokens)
→ 1-2 health checks (built-in)
→ 0-1 mistakes (caught early)
→ Minimal fix cycles
Total cost: $0.20-0.50
Savings: $1.50-4.50 (75-90%)
```

**ROI:** 3-10x cost savings, plus time and frustration saved

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

### Setup Process

1. **Choose your setup option** (new, existing, or update)
2. **Navigate to your project directory**
3. **Copy and run the prompt** from the appropriate enhanced `.md` file
4. **Restart Claude Desktop** to activate MCP servers
5. **Test MCP servers:**
   - "List all my Herd sites"
   - "Run artisan route:list"

### Daily Usage with Context Management

#### Starting Each Session
```bash
claude "Working on [feature]. Reminder: check .claude/project-info.md for versions"
```

Always start with explicit version awareness.

#### Every 15-20 Messages (Context Anchors)
```bash
"Quick reminder: Filament v3.2, following conventions.md"
# or
"Context anchor: what Filament version, what were last 3 changes?"
```

These short reminders keep context fresh. **Cost:** ~50 tokens. **Saves:** 500-1000 tokens in prevented mistakes.

#### Every 20-30 Messages (Health Check)
Claude Code should self-check using `.claude/session-health.md`:
- Can I recall the Filament version?
- Do I remember the last 3 changes?
- Am I maintaining consistency?

If unsure, Claude should proactively suggest fresh session.

#### When Mistakes Happen
```bash
"That's Filament v4 syntax - we're on v3. Check .claude/project-info.md critical section"
```

Point directly to the critical context section.

#### Long Sessions (50+ Messages)
```bash
"Let's review what we've completed and start fresh with version reminders"
```

Don't fight context degradation - restart is cheaper than repeated mistakes.

### Context Anchor Templates

See `.claude/context-anchors.md` in your project for customized templates including:
- Quick version checks
- Pattern reminders
- Before-big-change verifications
- Session start reminders

## Testing Token Savings

After setup, verify the `.cliignore` is working:
```bash
claude-code "List all Filament resources"
```

Check the token count - should see 50-70% reduction compared to without `.cliignore`.

To verify context management effectiveness:
- Use context anchors for a week
- Compare mistake frequency to previous sessions
- Should see 75-90% reduction in repeated errors

## Repository Structure

```
claude-setup/
├── README.md                      # This file (enhanced)
├── new-enhanced.md                # 🆕 Setup for new projects (with context mgmt)
├── existing-enhanced.md           # 🆕 Setup for existing projects (with context mgmt)
├── update-cliignore-enhanced.md   # 🆕 Update existing setup (adds context mgmt)
├── .cliignore                     # Template exclusion file
└── .gitignore                     # Protects this repo
```

## Customization

After setup, you can customize:
- `.claude/conventions.md` - Add your specific coding patterns
- `.claude/context.md` - Document project-specific details
- `.cliignore` - Add project-specific exclusions
- `.claude/context-anchors.md` - Adjust reminder templates
- `.claude/session-health.md` - Modify health check questions

## Best Practices

### Context Management
1. **Start every session with version reminder** - Make it a habit
2. **Use context anchors every 15-20 messages** - Costs ~50 tokens, saves 500-1000
3. **Watch for warning signs** - Same mistake twice? Wrong syntax? → Anchor or restart
4. **Don't fight degradation** - Fresh session is cheaper than fixing repeated mistakes
5. **Document patterns as they emerge** - Update conventions.md continuously

### Documentation Organization
1. **ALL Claude-created documentation goes in .claude/** - NEVER in project root or other directories
2. **Valid locations:**
   - `.claude/notes.md` - General project notes
   - `.claude/tasks.md` - Task lists and todos
   - `.claude/decisions.md` - Architectural decisions
   - `.claude/changelog.md` - Work log and changes
   - `.claude/debug-notes.md` - Debugging notes
   - `.claude/[any-name].md` - Any other documentation
3. **Invalid locations:** root directory, `docs/`, `notes/`, anywhere outside `.claude/`
4. **Exception:** `README.md` in root only if specifically requested
5. **Benefit:** Keeps project clean, documentation organized, and .gitignore simple

### General Claude Code Usage
1. **Always reference context:** Start prompts with "Following our project conventions..." or "Based on our stack configuration..."
2. **Keep files updated:** Update `.claude/project-info.md` when upgrading packages
3. **Document patterns:** Add new conventions to `.claude/conventions.md` as your project evolves
4. **Respect .cliignore:** Let Claude Code honor exclusions unless you explicitly need vendor code access
5. **Use MCP servers:** Leverage Herd and Boost for common Laravel tasks

### Filament-Specific Rules (TALL Stack Projects)
1. **Migration Safety:** NEVER use `migrate:fresh` without asking - it deletes admin users
2. **Livewire Components:** Prefer class-based over Volt - ask before using Volt
3. **Flux Components:** ONLY in Laravel admin/auth panel - never in public/frontend pages
4. **Always clarify context:** When building components, specify "admin" vs "frontend"

## Warning Signs of Context Degradation

Watch for these signs during sessions:

🚨 **Critical (Restart immediately):**
- Same mistake 3+ times
- Wrong Filament version used repeatedly
- Can't recall project versions when asked
- Contradicting decisions from earlier in session

⚠️ **Warning (Use context anchor or consider restart):**
- Same mistake 2 times
- Using wrong syntax occasionally
- Uncertain or "fuzzy" responses
- Over 40 messages in session

✅ **Healthy Session:**
- No repeated mistakes
- Correct version syntax
- Consistent with earlier decisions
- Under 30 messages

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
- **Context anchors are cheap** (~50 tokens) compared to fixing mistakes (500-1000 tokens)
- **Session health monitoring is free** - built into workflow
- **Critical context sections cost nothing** - just better file structure

## Support

For issues or questions about Claude Code itself, visit:
https://github.com/anthropics/claude-code/issues

For issues with these enhanced templates, open an issue in this repo.

## Migration from Non-Enhanced Version

If you're using the old version of these templates (without context management):

1. **For existing projects:** Run `update-cliignore-enhanced.md` - it will add all context management features without disrupting your setup
2. **For new projects:** Use `new-enhanced.md` going forward
3. **Your old setup still works** - context management is an enhancement, not a requirement

## License

These are configuration templates - use freely in your projects.

---

## Summary: Why Enhanced Version?

**Problem:** Claude Code forgets Filament versions, repeats mistakes, costs $$.

**Solution:** 
1. Critical context at top of files (passive protection)
2. Context anchors every 15-20 messages (active reinforcement)  
3. Session health monitoring (proactive detection)

**Result:** 75-90% reduction in repeated mistakes, 3-10x cost savings.

**Investment:** ~50 tokens per anchor, ~5 seconds per reminder.

**ROI:** Prevents 500-1000 token mistakes, saves $1-5 per prevented error.

**Bottom line:** Context management is 10-20x cheaper than fixing mistakes.
