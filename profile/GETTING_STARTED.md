# Getting Started with AGET Framework

**Create your first AGET agent in 30 minutes**

This guide walks you through creating your first AGET agent from template selection to first session.

---

## Prerequisites

Before starting, ensure you have:

✅ **Python 3.8+** - For contract tests and tooling
```bash
python3 --version  # Should show 3.8 or higher
```

✅ **Git** - For version control and cloning templates
```bash
git --version  # Any modern version
```

✅ **GitHub CLI (gh)** - For repository operations
```bash
gh --version  # Install: https://cli.github.com/
gh auth login  # Authenticate with GitHub
```

✅ **Claude Code** - Or your preferred CLI coding tool (Cursor, Aider, Windsurf)
- [Claude Code Installation](https://docs.claude.com/claude-code)

✅ **pytest** - For contract test validation
```bash
pip3 install pytest
```

---

## Step 1: Choose Your Template

Use this decision tree to select the right template:

```
┌─────────────────────────────────────────────────────────────┐
│ What is your agent's primary role?                          │
└─────────────────────────────────────────────────────────────┘
                           │
        ┌──────────────────┼──────────────────┐
        │                  │                  │
        ▼                  ▼                  ▼
  ┌─────────┐        ┌─────────┐      ┌──────────┐
  │ Manage  │        │ Provide │      │ General  │
  │ Multiple│        │ Advisory│      │ Purpose  │
  │ Agents? │        │ Role?   │      │ Task?    │
  └─────────┘        └─────────┘      └──────────┘
        │                  │                  │
        ▼                  ▼                  ▼
  supervisor         advisor            worker
  template           template           template
```

### Template Selection Guide

| Template | When to Use | Key Features | Complexity |
|----------|-------------|--------------|------------|
| **template-worker-aget** | General-purpose tasks, data analysis, API integration | Flexible capability (AGET or aget), 7 contract tests | ⭐ Beginner-friendly |
| **template-advisor-aget** | Coaching, mentoring, consulting, teaching | Persona-based (5 personas), scoped writes, 30 contract tests | ⭐⭐ Intermediate |
| **template-supervisor-aget** | Fleet coordination, multi-agent orchestration | Worker coordination, issue routing, fleet registry | ⭐⭐⭐ Advanced |

### Common Use Cases

**Worker Template**:
- GitHub automation (create PRs, manage issues)
- Data analysis and reporting
- API integration and monitoring
- Document generation
- Build and deployment tasks

**Advisor Template**:
- Executive coaching (persona: coach)
- Technical mentoring (persona: mentor)
- Strategic consulting (persona: consultant)
- Knowledge synthesis (persona: teacher)
- Domain expertise (persona: guru)

**Supervisor Template**:
- Fleet management (10+ agents)
- Cross-agent coordination
- Pattern deployment across agents
- Issue triage and routing
- Migration orchestration

### Recommendation for First Agent

**Start with template-worker-aget** - It's the simplest and most flexible. You can always upgrade to advisor or supervisor later as you learn the framework.

---

## Step 2: Clone Template Repository

Once you've chosen a template, clone it to create your agent:

```bash
# Example: Creating a worker agent
gh repo clone aget-framework/template-worker-aget my-first-aget
cd my-first-aget

# Verify directory structure
ls -la
# You should see: AGENTS.md, .aget/, tests/, src/, etc.
```

**Important**: Replace `my-first-aget` with your actual agent name following the naming convention:
- Use `-AGET` suffix if agent can modify systems (create files, make API calls)
- Use `-aget` suffix if agent is read-only (data analysis, reporting)

**Examples**:
```bash
# Action-taking agents (personal deployments)
private-github-AGET              # Creates PRs, manages issues
private-deployment-AGET          # Deploys to servers
private-database-AGET            # Modifies database schemas

# Information-only agents (personal deployments)
private-analytics-aget           # Reports metrics
private-log-analyzer-aget        # Analyzes logs
private-documentation-aget       # Generates docs (read-only context)
```

---

## Step 3: Verify CLAUDE.md Symlink

**Critical**: AGET uses `AGENTS.md` as the canonical configuration file, with `CLAUDE.md` as a symlink for backward compatibility with Claude Code.

```bash
# Check if CLAUDE.md is a symlink
ls -lh CLAUDE.md
# Should show: lrwxr-xr-x ... CLAUDE.md -> AGENTS.md

# Verify symlink target
readlink CLAUDE.md
# Should return: AGENTS.md
```

**If symlink is broken** (file instead of symlink):
```bash
# Remove file and recreate symlink
rm CLAUDE.md
ln -s AGENTS.md CLAUDE.md

# Verify
ls -lh CLAUDE.md  # Should now show symlink
```

**Why this matters**: If `CLAUDE.md` is a file (not symlink), updates to `AGENTS.md` won't be reflected in Claude Code's configuration, causing confusion.

---

## Step 4: Update Agent Identity

Edit `.aget/version.json` to define your agent's identity:

```bash
# Open in editor
vim .aget/version.json

# Or use sed for quick updates
cd ~/github/my-first-aget
sed -i '' 's/"agent_name": ".*"/"agent_name": "my-first-aget"/' .aget/version.json
sed -i '' 's/"domain": ".*"/"domain": "automation"/' .aget/version.json
```

**Required fields**:
```json
{
  "aget_version": "2.7.0",
  "agent_name": "my-first-aget",
  "instance_type": "AGET",
  "domain": "automation",
  "created_at": "2025-10-13",
  "updated_at": "2025-10-13"
}
```

**Field Descriptions**:
- `aget_version`: Framework version (must be 2.7.0+ for new agents)
- `agent_name`: Must match directory name exactly (e.g., `my-first-aget`)
- `instance_type`: `AGET` (action-taking) or `aget` (read-only)
- `domain`: Agent's primary domain (e.g., "github", "automation", "analytics")
- `created_at`: Today's date (YYYY-MM-DD)
- `updated_at`: Today's date (YYYY-MM-DD)

**Optional fields** (for advisor template):
```json
{
  "persona": "mentor"  // One of: teacher, mentor, consultant, guru, coach
}
```

---

## Step 5: Customize AGENTS.md

Edit `AGENTS.md` to define your agent's specific behavior:

```bash
vim AGENTS.md
```

**Key sections to customize**:

### Agent Compatibility Section
```markdown
## Agent Compatibility
This configuration follows the AGENTS.md open-source standard for universal agent configuration.
Works with Claude Code, Cursor, Aider, Windsurf, and other CLI coding agents.

@aget-version: 2.7.0
```

### Project Context Section
```markdown
## Project Context
my-first-aget - [Brief description of agent's purpose] - v2.7.0

[Explain what this agent does, what problems it solves, what it's responsible for]
```

### Available Capabilities Section
```markdown
## Available Capabilities

### Core Operations
- Capability 1: [Description]
- Capability 2: [Description]
- Capability 3: [Description]

### Helper Commands
- Command 1: [Usage example]
- Command 2: [Usage example]
```

**Example** (GitHub automation agent):
```markdown
## Available Capabilities

### GitHub Operations
- Create pull requests with description from commits
- Manage issue labels and assignments
- Review PR comments and respond to feedback
- Generate release notes from git history

### Helper Commands
```bash
# Create PR from current branch
gh pr create --fill

# List open issues
gh issue list --state open
```
```

---

## Step 6: Run Contract Tests

Contract tests validate your agent's configuration and identity:

```bash
# Run all contract tests
python3 -m pytest tests/ -v

# Expected output:
# tests/test_aget_contract.py::test_version_json_exists PASSED
# tests/test_aget_contract.py::test_aget_version_format PASSED
# tests/test_aget_contract.py::test_agent_name_matches_directory PASSED
# tests/test_aget_contract.py::test_instance_type_valid PASSED
# tests/test_aget_contract.py::test_domain_field_exists PASSED
# tests/test_aget_contract.py::test_agents_md_exists PASSED
# tests/test_aget_contract.py::test_claude_md_symlink PASSED
```

**If tests fail**:

1. **test_agent_name_matches_directory FAILED**:
   - Update `.aget/version.json` → `agent_name` to match directory name exactly

2. **test_claude_md_symlink FAILED**:
   - Run: `rm CLAUDE.md && ln -s AGENTS.md CLAUDE.md`

3. **test_instance_type_valid FAILED**:
   - Update `.aget/version.json` → `instance_type` to "AGET" or "aget"

4. **test_domain_field_exists FAILED**:
   - Add `"domain": "your-domain"` to `.aget/version.json`

**All tests must pass** before proceeding to first session.

---

## Step 7: Create GitHub Repository

Create a GitHub repository for your agent:

```bash
# Create repository (choose private or public)
gh repo create my-first-aget --private --source=. --remote=origin

# Push initial commit
git add .
git commit -m "Initial commit: my-first-aget v2.7.0

AGET agent created from template-worker-aget.

🤖 Generated with Claude Code (https://claude.com/claude-code)

Co-Authored-By: Claude <noreply@anthropic.com>"

git push -u origin main
```

**Repository visibility guidance**:
- **Private**: Personal agents, proprietary workflows, sensitive configurations
- **Public**: Reusable patterns, community contributions, reference implementations

**Note**: You can change visibility later with `gh repo edit --visibility public|private`.

---

## Step 8: First Session

Now you're ready for your first session with your agent!

### Wake Up Your Agent

Open Claude Code (or your preferred CLI tool) in your agent's directory:

```bash
cd ~/github/my-first-aget
# Open Claude Code in this directory
```

Then say:
```
wake up
```

**Expected response**:
```
my-first-aget v2.7.0 (Worker)

📍 Location: ~/github/my-first-aget
📊 Git: Clean working tree

🎯 Key Capabilities:
• [Your capabilities from AGENTS.md]

Ready for instructions.
```

### Give Your First Task

Start with something simple:

```
Create a simple README.md explaining what this agent does
```

Your agent will:
1. Read its configuration from AGENTS.md
2. Understand its identity from version.json
3. Create the README.md file
4. Show you the result

### Wind Down Your Session

When finished:
```
wind down
```

Your agent will:
1. Commit changes with descriptive message
2. Create session notes in `sessions/SESSION_YYYY-MM-DD.md`
3. Show completion summary

**Session notes** capture what happened (exchanges, tools used, objectives completed) for future reference.

---

## Step 9: Verify Deployment

Verify your agent is properly deployed to GitHub:

```bash
# Check GitHub deployment
gh repo view

# Verify version.json is accessible
gh api repos/$(gh repo view --json nameWithOwner -q .nameWithOwner)/contents/.aget/version.json | jq -r '.content' | base64 -d | jq -r '.aget_version'
# Should return: 2.7.0
```

---

## Common Issues and Troubleshooting

### Issue 1: Contract tests fail with "agent_name mismatch"

**Problem**: `.aget/version.json` has different name than directory

**Solution**:
```bash
# Get directory name
basename $(pwd)
# Update version.json to match
vim .aget/version.json  # Change "agent_name" field
```

### Issue 2: CLAUDE.md is not a symlink

**Problem**: Template cloning created CLAUDE.md as a file, not symlink

**Solution**:
```bash
rm CLAUDE.md
ln -s AGENTS.md CLAUDE.md
ls -lh CLAUDE.md  # Verify symlink
```

### Issue 3: Agent doesn't recognize capabilities

**Problem**: AGENTS.md not customized for your specific use case

**Solution**:
- Edit AGENTS.md → "Available Capabilities" section
- Be specific about what agent can/cannot do
- Include example commands for common operations
- Test by asking agent "what can you do?"

### Issue 4: Session notes not created on wind down

**Problem**: `sessions/` directory doesn't exist

**Solution**:
```bash
mkdir -p sessions
# Try wind down again
```

### Issue 5: Git push fails with authentication error

**Problem**: GitHub CLI not authenticated

**Solution**:
```bash
gh auth login
# Follow prompts to authenticate
```

---

## Next Steps

### Customize Your Agent Further

**Add patterns** from `.aget/evolution/`:
- L042: Gate discipline for substantial changes
- L084: Evidence before implementation
- L099: Multi-agent process enforcement
- L100: File-based coordination

**Create specifications** for complex capabilities:
- See `.aget/docs/SPEC_FORMAT_v1.1.md`
- Example: `.aget/specs/COORDINATOR_SPEC_v3.0.yaml`

**Add helper tools** in `.aget/tools/`:
- Python scripts for common operations
- Validation tools
- Automation helpers

### Learn Core Patterns

Read the framework's core patterns:
- [Design Philosophy](./DESIGN_PHILOSOPHY.md) - Human-supervised collaboration principles
- [Core Patterns](./CORE_PATTERNS.md) - Gate discipline, recursive supervision, coordination

### Join the Community

- **File issues**: Report bugs or request features in relevant repositories
- **Share learnings**: Contribute sanitized patterns to `.aget/evolution/`
- **Improve templates**: Suggest template enhancements via issues

### Create Additional Agents

Once comfortable with your first agent:
1. Create specialized agents for different domains
2. Consider supervisor agent for coordination (5+ agents)
3. Use advisor agents for guidance and coaching

---

## Template-Specific Guides

### Worker Template Deep Dive

**Best practices**:
- Start with clear capability list in AGENTS.md
- Add helper commands with usage examples
- Create learning documents for discovered patterns
- Use contract tests to validate configuration

**Advanced features**:
- Portfolio assignment (v2.7.0+)
- Learning discovery system
- Issue routing to supervisor
- Session metadata tracking

### Advisor Template Deep Dive

**Choosing a persona**:
- **Teacher**: Structured lessons, step-by-step guidance
- **Mentor**: Long-term development, skill building
- **Consultant**: Problem-specific advice, tactical recommendations
- **Guru**: Deep expertise, nuanced insights
- **Coach**: Reflective questioning, self-discovery

**Scoped write permissions**:
- Can write to `.aget/**` (internal state)
- Cannot modify code or external systems
- 30 contract tests validate boundaries

### Supervisor Template Deep Dive

**When to create supervisor**:
- Managing 5+ specialized agents
- Need cross-agent coordination
- Multi-agent migrations
- Fleet-wide pattern deployment

**Key capabilities**:
- Worker coordination via file-based checkpoints (L100)
- Issue triage and routing (multi-tier)
- Fleet registry and versioning
- Learning propagation across agents

---

## Success Criteria

You've successfully completed getting started when:

✅ Contract tests pass (7 tests for worker, 30 for advisor, 7 for supervisor)
✅ Agent responds to "wake up" with correct identity
✅ First task completed successfully
✅ Session notes created on "wind down"
✅ GitHub repository created and pushed
✅ Version.json shows 2.7.0
✅ CLAUDE.md is symlink to AGENTS.md

**Estimated time**: 30 minutes for worker, 45 minutes for advisor, 60 minutes for supervisor

---

## Resources

- **Framework Homepage**: [README.md](./README.md)
- **Design Philosophy**: [DESIGN_PHILOSOPHY.md](./DESIGN_PHILOSOPHY.md)
- **Core Patterns**: [CORE_PATTERNS.md](./CORE_PATTERNS.md)
- **Specification Format**: [SPEC_FORMAT_v1.1.md](https://github.com/aget-framework/template-worker-aget/blob/main/.aget/docs/SPEC_FORMAT_v1.1.md)
- **Template Repositories**: [aget-framework organization](https://github.com/aget-framework)

---

*Getting Started Guide v2.7.0 - Last updated: 2025-10-13*
