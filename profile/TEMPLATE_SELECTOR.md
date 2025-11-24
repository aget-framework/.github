# AGET Template Selector

**Choose the right template for your use case**

AGET provides four templates for different agent roles. **All templates build on the worker foundation** - advisor, consultant, and supervisor are specialized workers with additional capabilities.

---

## Architecture Foundation

```
template-worker-aget (CORE)
    │
    ├─► template-advisor-aget (worker + 5 personas + session artifacts)
    │
    ├─► template-consultant-aget (worker + consultant patterns + proactive analysis)
    │
    └─► template-supervisor-aget (worker + fleet coordination + process enforcement)
```

**Key Insight**: Every agent is fundamentally a worker. Advisor, consultant, and supervisor add specialized capabilities on top of the worker foundation.

---

## Quick Decision Tree

```
START: What will your agent do?
│
├─► Need to coordinate multiple agents?
│   └─► YES → Use template-supervisor-aget (worker + fleet coordination)
│
├─► Provide advice/guidance with session memory?
│   ├─► Need multiple personas (teacher/mentor/guru/coach)?
│   │   └─► YES → Use template-advisor-aget (worker + 5 personas)
│   │
│   └─► Solutions-focused proactive consulting only?
│       └─► YES → Use template-consultant-aget (worker + consultant patterns)
│
└─► General automation or task execution?
    └─► YES → Use template-worker-aget (core foundation)
```

---

## Template Comparison Matrix

| Feature | Worker (Core) | Consultant | Advisor | Supervisor |
|---------|---------------|------------|---------|------------|
| **Foundation** | ✅ Core template | ✅ Extends worker | ✅ Extends worker | ✅ Extends worker |
| **Primary Role** | Task execution | Proactive consulting | Multi-persona advisory | Fleet coordination |
| **Action-taking** | Configurable (aget/AGET) | Limited (.aget/** only) | Limited (.aget/** only) | Always (AGET) |
| **Internal State** | No | Yes (consultant artifacts) | Yes (session artifacts) | Yes (fleet registry) |
| **Multi-agent** | No | No | No | Yes (coordinates workers) |
| **Persona System** | No | No (consultant only) | Yes (5 personas) | No |
| **Specialized Patterns** | No | Yes (6 consultant patterns) | No (generic advisory) | Yes (coordination) |
| **Portfolio Aware** | Yes | Yes | Yes | Yes (cross-portfolio) |
| **Contract Tests** | 7 minimum | 55 (most rigorous) | 30 | 7 minimum |
| **Typical Use Cases** | Automation, CI/CD | Strategic advisory, options frameworks | Coaching, teaching, mentoring | Release management, fleet ops |
| **Complexity** | Simple | Medium | Medium | Advanced |
| **Best For** | Individual developers | Consultants, strategists | Power users, coaches | Team leads, org admins |

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

**Repository**: https://github.com/aget-framework/template-worker-aget

---

### Consultant Template (`template-consultant-aget`) - Worker + Consultant Patterns

**This is a worker with formalized consultant-specific patterns.**

**Foundation**: Inherits all worker template capabilities

**Additional Capabilities**:
- **6 Consultant Patterns**: Proactive analysis, framework-based knowledge, decision journals, options generation, evidence-based recommendations, low-continuity engagements
- **Specialized Directories**: `.aget/analysis/` (proactive findings), `.aget/evidence/` (case studies, benchmarks)
- **Scoped Writes**: Can write to `.aget/**` for consultant artifacts (read-only elsewhere)
- **Fixed Persona**: Consultant-only (not configurable) - solutions-focused, professional analysis
- Contract testing framework (55 tests - most rigorous of all templates)

**Architecture**:
```
Worker Foundation (all core capabilities)
    + 6 Consultant Patterns (formalized workflows)
    + Consultant-Specific Directories (.aget/analysis/, .aget/evidence/)
    + Enhanced Contract Tests (55 tests)
    = Consultant Template
```

**Typical Use Cases**:
- Strategic advisory (architecture decisions, technology selection)
- Options frameworks (2-4 paths with explicit tradeoffs)
- Evidence-based recommendations (cite case studies, benchmarks, research)
- Decision journals (track options, rationale, outcomes)
- Risk assessment with mitigation options
- Vendor/technology selection with weighted criteria

**When to Choose**:
- Need **proactive analysis** (identify issues without prompting)
- Want **systematic decision frameworks** (repeatable processes)
- Require **evidence-based recommendations** (data-driven, not opinion)
- Prefer **options frameworks** (2-4 paths with tradeoffs vs single recommendation)
- Value **discrete engagements** (session-based advisory, not long-term coaching)
- Solutions-focused professional analysis (not teaching, mentoring, or coaching)

**When to Use Advisor Instead**:
- Need to **switch personas** (teacher for education, coach for performance, etc.)
- Curriculum-based learning required (teacher persona)
- Guided discovery coaching needed (coach persona)
- Career development focus (mentor persona)

**Example Agents**:
- architecture-consultant-aget (system design advisory with options frameworks)
- technology-selection-consultant-aget (vendor evaluation with weighted criteria)
- risk-assessment-consultant-aget (identify risks, generate mitigation options)

**Extraction Story**:
- **Extracted from**: template-advisor-aget (v2.7.0)
- **Evidence**: 5 production instances, 100% consultant persona adoption
- **Rationale**: Dominant usage pattern (>80% concentration) signaled dedicated template extraction
- **Learning**: L227 - Template Extraction from Dominant Persona Usage

**Repository**: https://github.com/aget-framework/template-consultant-aget

---

### Advisor Template (`template-advisor-aget`) - Worker + 5 Personas

**This is a worker with multi-persona advisory capabilities.**

**Foundation**: Inherits all worker template capabilities

**Additional Capabilities**:
- **Persona System**: 5 personas (teacher, mentor, consultant, guru, coach)
- **Scoped Writes**: Can write to `.aget/**` for session artifacts (read-only elsewhere)
- **Session Management**: Maintains session state and artifacts
- **Internal Artifacts**: Learning notes, session summaries, reflections
- Contract testing framework (30 tests)

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
- Domain expertise (persona: guru)
- Educational guidance (persona: teacher)
- General consulting (persona: consultant - consider dedicated consultant template for specialized patterns)

**When to Choose**:
- You need **multiple advisory styles** (switch between personas)
- Session memory and artifact management required
- Non-action-taking by design (guidance, not execution)
- Power user or consultant use case with persona flexibility

**When to Use Consultant Template Instead**:
- **Always** use consultant persona (never switch)
- Need formalized consultant patterns (proactive analysis, decision journals, evidence repository)
- Want consultant-specific optimizations (55 tests vs 30, specialized directories)

**Example Agents**:
- executive-coach-aget (coaches leaders on decision-making)
- security-mentor-aget (guides security best practices)
- python-teacher-aget (teaches Python with curriculum)

**Persona Selection**:
- **Teacher**: Structured lessons, knowledge transfer, assessments
- **Mentor**: Experience-based guidance, career development
- **Consultant**: Expert analysis, recommendations, frameworks (→ consider template-consultant-aget for specialization)
- **Guru**: Deep domain wisdom, philosophical guidance
- **Coach**: Question-based discovery, reflection, accountability

**Note on Consultant Persona**: If you exclusively use consultant persona, consider migrating to `template-consultant-aget` for formalized consultant patterns and enhanced capabilities.

**Repository**: https://github.com/aget-framework/template-advisor-aget

---

### Supervisor Template (`template-supervisor-aget`) - Worker + Fleet Coordination

**This is a worker with added fleet coordination capabilities.**

**Foundation**: Inherits all worker template capabilities

**Additional Capabilities**:
- **Fleet Coordination**: Manage multiple worker/advisor/consultant agents
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

**Repository**: https://github.com/aget-framework/template-supervisor-aget (private until public release)

---

## Consultant vs Advisor: When to Choose

### Use Consultant Template When:

✅ **Always** use consultant communication style (never switch personas)
✅ Need **proactive analysis** (identify issues without prompting)
✅ Want **systematic frameworks** (decision matrices, risk models, evaluation rubrics)
✅ Require **evidence-based recommendations** (cite case studies, benchmarks, research)
✅ Provide **options frameworks** (2-4 paths with explicit tradeoffs)
✅ Value **discrete engagements** (session-based, actionable deliverables)
✅ Need consultant-specific directories (`.aget/analysis/`, `.aget/evidence/`)

### Use Advisor Template When:

✅ **Switch between personas** based on context (teacher, mentor, consultant, guru, coach)
✅ Curriculum-based teaching required (teacher persona)
✅ Guided discovery coaching needed (coach persona)
✅ Career development mentorship (mentor persona)
✅ Deep domain wisdom sharing (guru persona)
✅ Might change advisory style over time

### Migration Path

If you have advisor instance using **only** consultant persona:
- Consider migrating to `template-consultant-aget`
- See: [Consultant Template Migration Guide](https://github.com/aget-framework/template-consultant-aget/blob/main/docs/MIGRATION_GUIDE.md)
- Benefit: Formalized patterns, specialized testing (55 vs 30 tests), optimized structure

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

**Consultant** (Worker + Patterns):
- Inherits worker portfolio capabilities
- Consultant artifacts inherit portfolio classification
- Examples: `main` for general consulting, `ccb` for personal advisory

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
# After cloning any template (worker, consultant, advisor, or supervisor)
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

### When to Use Consultant vs Advisor

**Choose Consultant if**:
- You know you need consultant-specific patterns (proactive, frameworks, decisions, options, evidence)
- You value formalized workflows over persona flexibility
- You want the most rigorous testing (55 contract tests)

**Choose Advisor if**:
- You need persona flexibility (might use teacher, mentor, coach, guru)
- You're exploring advisory styles and haven't settled on one
- Generic advisory patterns sufficient

**Don't upgrade advisor to consultant**. These are distinct specializations of the worker foundation. Migrate existing advisor instances if they exclusively use consultant persona (see migration guide).

---

## Role-Based Recommendations

### Individual Developer

**Start with**: Worker template (core foundation)
- Simple, single-purpose automation
- Learn AGET patterns with minimal overhead
- All core capabilities included
- Upgrade to supervisor if fleet grows >3 agents

**Why worker first**: Master the foundation before specializing

### Consultant / Strategic Advisor

**Consider**: Consultant template (worker + formalized patterns)
- Proactive analysis and options frameworks
- Evidence-based recommendations with citation
- Decision journals for outcome tracking
- Specialized directories for consultant workflows
- All worker capabilities still available

**Foundation**: Still a worker, with consultant pattern formalization

### Power User / Multi-Style Advisor

**Consider**: Advisor template (worker + 5 personas)
- Leverage persona system for varied interaction styles
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

**Even if you need supervisor/advisor/consultant eventually, understand the worker foundation first.**

All templates share:
- `.aget/` directory structure
- Core lifecycle protocols (wake/wind down/sign off)
- Portfolio configuration
- Contract testing framework
- Git integration

### 2. Choose Template (Use Decision Tree Above)

```
General automation → Worker (core)
Solutions-focused consulting → Consultant (worker + patterns)
Multi-style advisory → Advisor (worker + personas)
Fleet coordination → Supervisor (worker + fleet)
```

### 3. Clone Template

```bash
# Worker (core foundation)
gh repo clone aget-framework/template-worker-aget my-agent-name

# Consultant (worker + formalized patterns)
gh repo clone aget-framework/template-consultant-aget my-consultant-name

# Advisor (worker + 5 personas)
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
# - 55/55 passed (consultant) - most rigorous
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

### Q: When should I use consultant vs advisor template?

**A**: Use **consultant** if you exclusively use consultant communication style (solutions-focused, options frameworks, evidence-based). Use **advisor** if you switch between personas (teacher, mentor, coach, guru) or might in the future. Consultant has formalized patterns and enhanced testing (55 vs 30 tests).

### Q: Are consultant, advisor, and supervisor different types of agents?

**A**: No. They're **workers with additional capabilities**. All agents share the worker foundation (directory structure, lifecycle, portfolio awareness, contract tests). Consultant adds formalized patterns. Advisor adds persona system. Supervisor adds fleet coordination.

### Q: Can I migrate from advisor to consultant template?

**A**: Yes, if you exclusively use consultant persona. See [Migration Guide](https://github.com/aget-framework/template-consultant-aget/blob/main/docs/MIGRATION_GUIDE.md). Benefits: formalized consultant patterns, specialized testing, optimized structure.

### Q: Can I use supervisor capabilities in a worker?

**A**: No. Use the supervisor template if you need fleet coordination. The templates are pre-configured specializations.

### Q: Can advisor or consultant agents coordinate other agents?

**A**: No. Advisors and consultants are workers with advisory capabilities. For coordination, use supervisor template (worker + fleet coordination).

### Q: Why start with worker if I need a consultant?

**A**: Understanding the worker foundation helps you understand what consultants inherit. But if you know you need consultant patterns, you can start with consultant template directly.

### Q: Do supervisors or consultants have personas like advisors?

**A**: No. Consultant = worker + consultant patterns (fixed consultant persona). Supervisor = worker + fleet coordination (no personas). Advisor = worker + 5 persona system. These are different specializations of the worker core.

### Q: Can I change templates later?

**A**: Templates define agent architecture. Changing templates = creating new agent or migration (for advisor→consultant). Keep original agent, create new one from different template if needed, or follow migration guide for supported paths.

### Q: Can worker agents coordinate each other?

**A**: No. Worker-to-worker coordination leads to complexity. Use supervisor template (worker + fleet coordination) for multi-agent coordination.

### Q: Can consultants or advisors take actions?

**A**: Limited. Consultants and advisors can write to `.aget/**` for artifacts (consultant: `.aget/analysis/`, `.aget/evidence/`; advisor: `.aget/sessions/`). Cannot modify external systems. This is worker foundation + scoped write restriction.

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
           ▲                ▲                ▲
           │                │                │
    ┌──────┴──────┐  ┌──────┴──────┐  ┌─────┴──────┐
    │             │  │             │  │            │
┌───▼────────┐  ┌─▼──────────┐  ┌─▼─────────┐  ┌─▼────────────┐
│ Consultant │  │  Advisor   │  │  Worker   │  │ Supervisor   │
│            │  │            │  │   Only    │  │              │
│ + 6 Patterns│  │ + 5 Personas│  │          │  │ + Fleet Coord│
│ + Analysis │  │ + Session  │  │(Use as-is)│  │ + Process    │
│ + Evidence │  │ + 30 tests │  │           │  │  Enforcement │
│ + 55 tests │  │            │  │           │  │              │
└────────────┘  └────────────┘  └───────────┘  └──────────────┘
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

### Example 2: Architecture Decision Advisory

**Need**: Provide architecture recommendations with options frameworks and evidence
**Choice**: Consultant template (worker + formalized patterns)
**Portfolio**: `main` (general consulting)
**Rationale**: Proactive analysis, options frameworks, decision journals, evidence-based recommendations, built on worker foundation

---

### Example 3: Executive Coaching with Multiple Styles

**Need**: Provide coaching with ability to switch to mentoring or teaching
**Choice**: Advisor template (worker + 5 personas)
**Portfolio**: `ccb` (very_personal - confidential coaching context)
**Rationale**: Multi-persona flexibility, session artifacts required, persona system needed, built on worker foundation

---

### Example 4: Fleet Release Management

**Need**: Coordinate v2.6 → v2.7 migration across 15 agents
**Choice**: Supervisor template (worker + fleet coordination)
**Portfolio**: `null` (cross-portfolio coordination)
**Rationale**: Multi-agent coordination, pattern deployment, release management, built on worker foundation

---

### Example 5: Strategic Technology Selection

**Need**: Evaluate vendors with weighted criteria and evidence-based recommendations
**Choice**: Consultant template (worker + formalized patterns)
**Portfolio**: `main` (general consulting)
**Rationale**: Evidence repository, decision journals, options generation, systematic frameworks, built on worker foundation

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

*AGET Framework v2.9.0 - Template Selector*
*Worker Foundation: Core capabilities inherited by all templates*
*Consultant Template: Extracted v2.7.0 based on dominant usage evidence (L227)*
*Last Updated: 2025-11-10*
