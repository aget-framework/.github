# AGET Template Selector

**Choose the right template for your use case**

AGET provides three templates for different agent roles. **All templates build on the worker foundation** - advisor and supervisor are specialized workers with additional capabilities.

---

## Architecture Foundation

```
template-worker-aget (CORE)
    │
    ├─► template-advisor-aget (worker + persona system + session artifacts)
    │
    └─► template-supervisor-aget (worker + fleet coordination + process enforcement)
```

**Key Insight**: Every agent is fundamentally a worker. Advisor and supervisor add specialized capabilities on top of the worker foundation.

---

## Quick Decision Tree

```
START: What will your agent do?
│
├─► Need to coordinate multiple agents?
│   └─► YES → Use template-supervisor-aget (worker + fleet coordination)
│
├─► Provide advice/guidance with session memory?
│   └─► YES → Use template-advisor-aget (worker + persona system)
│
└─► General automation or task execution?
    └─► YES → Use template-worker-aget (core foundation)
```

---

## Template Comparison Matrix

| Feature | Worker (Core) | Advisor (Worker+) | Supervisor (Worker+) |
|---------|---------------|-------------------|----------------------|
| **Foundation** | ✅ Core template | ✅ Extends worker | ✅ Extends worker |
| **Primary Role** | Task execution | Advisory & guidance | Fleet coordination |
| **Action-taking** | Configurable (aget/AGET) | Limited (.aget/** only) | Always (AGET) |
| **Internal State** | No | Yes (session artifacts) | Yes (fleet registry) |
| **Multi-agent** | No | No | Yes (coordinates workers) |
| **Persona System** | No | Yes (5 personas) | No |
| **Portfolio Aware** | Yes | Yes | Yes (cross-portfolio) |
| **Contract Tests** | 7 minimum | 30 minimum | 7 minimum |
| **Typical Use Cases** | Automation, CI/CD, data processing | Coaching, consulting, teaching | Release management, fleet ops |
| **Complexity** | Simple | Medium | Advanced |
| **Best For** | Individual developers | Power users | Team leads, org admins |

---

## Template Descriptions

### Worker Template (`template-worker-aget`) - THE CORE

**This is the foundation template. All other templates build on this.**

**Capabilities**:
- Flexible read/write permissions (configure via suffix: `-aget` or `-AGET`)
- Portfolio assignment for governance
- Standard AGET lifecycle (wake/wind down/sign off)
- Git integration and CI/CD workflows
- Contract testing framework (7 tests)
- Core directory structure (`.aget/evolution/`, `.aget/checkpoints/`, etc.)

**Typical Use Cases**:
- GitHub automation (issue management, PR creation)
- Data processing pipelines
- Deployment scripts
- Documentation generation
- Testing and QA workflows

**When to Choose**:
- You need a single-purpose agent for automation
- You want configurable action-taking capabilities
- You don't need advisory features or multi-agent coordination
- Individual developer or small team use case
- **Starting point for learning AGET framework**

**Example Agents**:
- github-automation-aget (manages issues and PRs)
- data-pipeline-AGET (processes and transforms data)
- deployment-helper-AGET (automates deployment workflows)

---

### Advisor Template (`template-advisor-aget`) - Worker + Persona

**This is a worker with added advisory capabilities.**

**Foundation**: Inherits all worker template capabilities

**Additional Capabilities**:
- **Persona System**: 5 personas (teacher, mentor, consultant, guru, coach)
- **Scoped Writes**: Can write to `.aget/**` for session artifacts (read-only elsewhere)
- **Session Management**: Maintains session state and artifacts
- **Internal Artifacts**: Learning notes, session summaries, reflections
- Contract testing framework (30 tests - most rigorous)

**Architecture**:
```
Worker Foundation (all core capabilities)
    + Persona System (teacher/mentor/consultant/guru/coach)
    + Session Artifact Management (.aget/** writes)
    + Enhanced Contract Tests (30 tests)
    = Advisor Template
```

**Typical Use Cases**:
- Executive coaching (persona: coach)
- Technical mentorship (persona: mentor)
- Architecture consulting (persona: consultant)
- Domain expertise (persona: guru)
- Educational guidance (persona: teacher)

**When to Choose**:
- You need advisory capabilities with personality
- Session memory and artifact management required
- Non-action-taking by design (guidance, not execution)
- Power user or consultant use case

**Example Agents**:
- executive-coach-aget (coaches leaders on decision-making)
- architecture-consultant-aget (advises on system design)
- security-mentor-aget (guides security best practices)

**Persona Selection**:
- **Teacher**: Structured lessons, knowledge transfer, assessments
- **Mentor**: Experience-based guidance, career development
- **Consultant**: Expert analysis, recommendations, frameworks
- **Guru**: Deep domain wisdom, philosophical guidance
- **Coach**: Question-based discovery, reflection, accountability

---

### Supervisor Template (`template-supervisor-aget`) - Worker + Fleet Coordination

**This is a worker with added fleet coordination capabilities.**

**Foundation**: Inherits all worker template capabilities

**Additional Capabilities**:
- **Fleet Coordination**: Manage multiple worker/advisor agents
- **Cross-Portfolio Operations**: Coordinate agents across portfolios
- **Process Enforcement**: Gate discipline, quality standards (L099)
- **Recursive Supervision**: Can be supervised by other supervisors (L99)
- **Worker Coordination**: File-based coordination protocol (L100)
- **Issue Routing**: Multi-tier issue management
- Fleet registry (`.aget/registry/`)
- Coordination checkpoints (`.aget/coordination/`)

**Architecture**:
```
Worker Foundation (all core capabilities)
    + Fleet Registry (.aget/registry/)
    + Multi-Agent Coordination (L100 protocol)
    + Process Enforcement (L099 patterns)
    + Recursive Supervision (L99 model)
    = Supervisor Template
```

**Typical Use Cases**:
- Fleet release management (coordinate v2.6 → v2.7 migration)
- Pattern deployment across agents
- Multi-repository operations (batch updates, consistency checks)
- Issue triage and routing
- Quality assurance and process enforcement

**When to Choose**:
- You manage 3+ agents that need coordination
- You need to enforce standards across a fleet
- Multi-repository operations required
- Team lead or organizational admin use case
- You need hierarchical agent management

**Example Supervisors**:
- release-coordinator-AGET (manages fleet upgrades)
- fleet-supervisor-AGET (coordinates multiple domain agents)
- quality-assurance-AGET (enforces standards across fleet)

---

## Portfolio Awareness

**All templates support portfolio assignment** (inherited from worker foundation).

### Portfolio Classifications

- **main** (private): Standard agents, general-purpose capabilities
- **ccb** (very_personal): Personal/confidential agents with sensitive context
- **legalon** (confidential): Domain-specific agents with proprietary data
- **null**: Template or coordinator (no specific portfolio)

### Portfolio Guidance by Template

**Worker** (Core):
- Assign to specific portfolio based on data access
- Examples: `main` for general automation, `ccb` for personal agents

**Advisor** (Worker + Persona):
- Inherits worker portfolio capabilities
- Session artifacts inherit portfolio classification
- Examples: `ccb` for personal coach, `main` for technical mentor

**Supervisor** (Worker + Fleet Coordination):
- Inherits worker portfolio capabilities
- Typically `portfolio: null` (coordinate across portfolios)
- Can be assigned to portfolio for single-portfolio fleet management
- Cross-portfolio operations respect portfolio boundaries

### Setting Portfolio

```bash
# After cloning any template (worker, advisor, or supervisor)
vim .aget/version.json

# Set portfolio field
{
  "portfolio": "main"  // or "ccb", "legalon", null
}
```

---

## Upgrade Paths

### When to Upgrade from Worker to Supervisor

**Remember**: Supervisor is a worker with fleet coordination capabilities.

**Signals you need a supervisor**:

1. **Fleet Size**: Managing 3+ agents manually becomes inefficient
2. **Coordination Overhead**: Spending >30% time coordinating agent work
3. **Consistency Issues**: Agents at different versions or configurations
4. **Pattern Deployment**: Need to deploy patterns/standards across fleet
5. **Release Management**: Coordinating multi-agent migrations

**Migration Process**:

1. Clone `template-supervisor-aget` (inherits all worker capabilities)
2. Copy fleet registry from worker (if tracking agents)
3. Update `.aget/version.json` with supervisor identity
4. Implement fleet coordination protocols (`.aget/coordination/`)
5. Migrate worker agents to report to supervisor

**Timeline**: ~2-4 hours for initial setup + fleet integration

---

### When to Use Advisor Instead of Worker

**Remember**: Advisor is a worker with persona and session management.

**Choose Advisor if**:

- Primary role is guidance/advisory (not action-taking)
- Need session memory across multiple interactions
- Persona-based interaction style required
- Creating session artifacts (notes, summaries, reflections)

**Don't upgrade worker to advisor**. These are distinct specializations of the worker foundation. Create new advisor agent if advisory capabilities needed.

---

## Role-Based Recommendations

### Individual Developer

**Start with**: Worker template (core foundation)
- Simple, single-purpose automation
- Learn AGET patterns with minimal overhead
- All core capabilities included
- Upgrade to supervisor if fleet grows >3 agents

**Why worker first**: Master the foundation before specializing

### Power User / Consultant

**Consider**: Advisor template (worker + persona)
- Leverage persona system for client interaction
- Session management for multi-engagement tracking
- Scoped writes for internal note-taking
- All worker capabilities still available

**Foundation**: Still a worker, with advisory extensions

### Team Lead / Engineering Manager

**Start with**: Supervisor template (worker + fleet coordination)
- Coordinate team's automation agents
- Enforce standards across team fleet
- Pattern deployment to maintain consistency
- All worker capabilities still available

**Alternative**: Worker template (if managing single agent)
- Start simple, upgrade when fleet grows

**Foundation**: Still a worker, with coordination extensions

### Organizational Admin

**Use**: Supervisor template (worker + cross-portfolio fleet coordination)
- Fleet coordination across portfolios
- Organization-wide pattern deployment
- Multi-tier issue routing
- Cross-portfolio governance
- All worker capabilities still available

**Foundation**: Built on worker core with organizational extensions

---

## Getting Started

### 1. Start with Worker Foundation

**Even if you need supervisor/advisor eventually, understand the worker foundation first.**

All templates share:
- `.aget/` directory structure
- Core lifecycle protocols (wake/wind down/sign off)
- Portfolio configuration
- Contract testing framework
- Git integration

### 2. Choose Template (Use Decision Tree Above)

```
General automation → Worker (core)
Advisory role → Advisor (worker + persona)
Fleet coordination → Supervisor (worker + fleet)
```

### 3. Clone Template

```bash
# Worker (core foundation)
gh repo clone aget-framework/template-worker-aget my-agent-name

# Advisor (worker + persona)
gh repo clone aget-framework/template-advisor-aget my-advisor-name

# Supervisor (worker + fleet coordination)
gh repo clone aget-framework/template-supervisor-aget my-supervisor-name
```

### 4. Customize

```bash
cd my-agent-name

# Update identity (same for all templates - inherited from worker)
vim .aget/version.json
# - Set agent_name (match directory name)
# - Set instance_type ("AGET" or "aget" for worker, leave template for others)
# - Set domain (your domain/role)
# - Set portfolio (see Portfolio Guidance above)

# Update configuration
vim AGENTS.md
# - Update Project Context section
# - Add agent-specific protocols
```

### 5. Validate

```bash
# Run contract tests (all templates have this - from worker foundation)
python3 -m pytest tests/ -v

# Should show:
# - 7/7 passed (worker, supervisor)
# - 30/30 passed (advisor)
```

### 6. Deploy

```bash
# Same for all templates (inherited from worker)
gh repo create my-agent-name --private --source=. --remote=origin
git push -u origin main
```

---

## Common Questions

### Q: Are advisor and supervisor different types of agents?

**A**: No. They're **workers with additional capabilities**. All agents share the worker foundation (directory structure, lifecycle, portfolio awareness, contract tests). Advisor adds persona system. Supervisor adds fleet coordination.

### Q: Can I use supervisor capabilities in a worker?

**A**: No. Use the supervisor template if you need fleet coordination. The templates are pre-configured specializations.

### Q: Can advisor agents coordinate other agents?

**A**: No. Advisors are workers with advisory capabilities (persona, session management). For coordination, use supervisor template (worker + fleet coordination).

### Q: Why start with worker if I need a supervisor?

**A**: Understanding the worker foundation helps you understand what supervisors inherit. But if you know you need fleet coordination, you can start with supervisor template directly.

### Q: Do supervisors have personas like advisors?

**A**: No. Supervisor = worker + fleet coordination. Advisor = worker + persona system. These are different specializations of the worker core.

### Q: Can I change templates later?

**A**: Templates define agent architecture. Changing templates = creating new agent. Keep original agent, create new one from different template if needed.

### Q: Can worker agents coordinate each other?

**A**: No. Worker-to-worker coordination leads to complexity. Use supervisor template (worker + fleet coordination) for multi-agent coordination.

### Q: Can advisors take actions?

**A**: Limited. Advisors can write to `.aget/**` for session artifacts (notes, summaries). Cannot modify external systems. This is worker foundation + scoped write restriction.

### Q: Do I need a supervisor for 2 agents?

**A**: No. Manual coordination works for 2 agents. Consider supervisor (worker + fleet coordination) at 3+ agents or when coordination overhead >30%.

### Q: Can supervisors be supervised?

**A**: Yes (L99 - Recursive Supervision Model). Supervisors can report to other supervisors for hierarchical management. This is because supervisors are workers with coordination capabilities.

---

## Template Architecture Summary

```
┌─────────────────────────────────────────────────┐
│  Worker Template (CORE FOUNDATION)              │
│  - Directory structure (.aget/)                 │
│  - Lifecycle protocols (wake/wind down)         │
│  - Portfolio awareness                          │
│  - Git integration                              │
│  - Contract testing (7 tests)                   │
│  - Configurable capabilities (aget/AGET)        │
└─────────────────────────────────────────────────┘
           ▲                          ▲
           │                          │
    ┌──────┴──────┐          ┌───────┴────────┐
    │             │          │                │
┌───▼────────┐  ┌─▼──────────────┐  ┌────────▼───────┐
│  Advisor   │  │  Worker Only   │  │  Supervisor    │
│            │  │                │  │                │
│ + Persona  │  │  (Use as-is)   │  │ + Fleet Coord  │
│ + Session  │  │                │  │ + Process      │
│ + 30 tests │  │                │  │   Enforcement  │
└────────────┘  └────────────────┘  └────────────────┘
```

**Key Takeaway**: Master the worker foundation. Everything builds on it.

---

## Decision Examples

### Example 1: GitHub Automation

**Need**: Automate issue triage and PR management
**Choice**: Worker template (core foundation)
**Portfolio**: `main` (general automation)
**Rationale**: Single-purpose automation, no advisory or coordination needed, use core capabilities

---

### Example 2: Executive Coaching

**Need**: Provide coaching with session memory
**Choice**: Advisor template (worker + persona system)
**Portfolio**: `ccb` (very_personal - confidential coaching context)
**Rationale**: Advisory role, session artifacts required, persona system needed, built on worker foundation

---

### Example 3: Fleet Release Management

**Need**: Coordinate v2.6 → v2.7 migration across 15 agents
**Choice**: Supervisor template (worker + fleet coordination)
**Portfolio**: `null` (cross-portfolio coordination)
**Rationale**: Multi-agent coordination, pattern deployment, release management, built on worker foundation

---

### Example 4: Architecture Consulting

**Need**: Advise on system design with documentation
**Choice**: Advisor template (worker + persona system)
**Portfolio**: `main` (general consulting)
**Rationale**: Expert advisory, session artifacts (design notes), consultant persona, built on worker foundation

---

## Next Steps

1. **Understand Worker Foundation** - All templates build on this
2. **Use Decision Tree** (above) to identify template
3. **Review Template Comparison** to validate choice
4. **Clone Template** and customize for your use case
5. **Run Contract Tests** to validate setup (inherited from worker)
6. **Deploy to GitHub** and start using

**Need Help?** See [Getting Started Guide](GETTING_STARTED.md) for detailed walkthrough.

---

*AGET Framework v2.7.0 - Template Selector*
*Worker Foundation: Core capabilities inherited by all templates*
*Last Updated: 2025-10-13*
