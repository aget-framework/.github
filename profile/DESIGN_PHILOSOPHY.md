# AGET Design Philosophy

**Human-supervised collaboration principles for AI coding agents**

This document articulates the core design principles that guide AGET's architecture, patterns, and evolution. These principles emerged from practical experience managing fleets of specialized coding agents, not from theoretical frameworks.

---

## Core Principles

### 1. Human-Supervised Collaboration (Not Autonomous Execution)

**Principle**: Humans remain decision-makers; agents are capable assistants.

**Rationale**: While autonomous agents excel at bounded tasks, complex software engineering requires human judgment, context, and accountability. AGET recognizes this reality and structures collaboration accordingly.

**In Practice**:
- GO/NOGO gates for substantial changes (multi-file operations, structural changes)
- Evidence-before-implementation protocols (L084: confirm requirements before building)
- Incremental delivery with decision points
- Supervisor agents coordinate, but humans approve

**Anti-Pattern**: "Agent, implement this feature" → agent disappears for hours → returns with 1000 lines
**AGET Pattern**: "Agent, plan this feature with gates" → agent presents 5-gate plan → human approves Gate 1 → agent executes → presents Gate 2 → repeat

**Learning References**:
- L042: Gate execution discipline (stop at boundaries, wait for GO)
- L084: Evidence before implementation (avoid wasted work)
- L099: Multi-agent process enforcement (supervisor reviews outputs)

---

### 2. Configuration Over Code

**Principle**: Agent behavior defined via configuration files, not custom runtimes.

**Rationale**: Configuration files are:
- Version-controlled alongside code
- Human-readable and auditable
- Portable across CLI tools
- Easy to diff and review
- Require no infrastructure

**In Practice**:
- `AGENTS.md` defines agent capabilities and protocols
- `.aget/version.json` defines identity and compliance level
- `.aget/specs/*.yaml` defines formal specifications
- Contract tests validate configuration consistency

**Anti-Pattern**: Custom agent runtime with API configuration → vendor lock-in, infrastructure overhead
**AGET Pattern**: Markdown configuration files → works with Claude Code, Cursor, Aider, Windsurf, etc.

**Example**:
```markdown
## Available Capabilities
- Create pull requests with description from commits
- Manage issue labels and assignments
- Generate release notes from git history
```

vs. API configuration:
```json
{
  "capabilities": ["pr.create", "issue.manage", "release.generate"],
  "api_endpoint": "https://vendor.com/api/v1",
  "auth_token": "..."
}
```

AGET favors the first approach (configuration over code).

---

### 3. Universal CLI Compatibility

**Principle**: AGET works across competing CLI coding tools.

**Rationale**: The CLI coding tool landscape is rapidly evolving with multiple competing platforms (Claude Code, Cursor, Aider, Windsurf, Cline, etc.). Vendor lock-in limits flexibility and creates migration risk.

**In Practice**:
- `AGENTS.md` standard adopted by multiple tools
- `CLAUDE.md` symlink for backward compatibility
- No tool-specific APIs or features required
- Plain markdown and JSON configuration

**Anti-Pattern**: "This agent only works with Claude Code v2.3+"
**AGET Pattern**: "This agent works with any tool that reads AGENTS.md"

**Competitive Advantage**: User can switch CLI tools without recreating agents from scratch.

**Learning References**:
- L143: Framework landscape positioning (CLI compatibility gap)

---

### 4. Evidence-Based Evolution

**Principle**: Organizational memory captures "why" decisions were made, not just "what" changed.

**Rationale**: Traditional version control tracks code changes, but not the reasoning behind them. Six months later, "Why did we implement it this way?" has no answer. AGET's learning system preserves organizational knowledge.

**In Practice**:
- `.aget/evolution/` contains L-numbered learning documents
- Each learning captures: Problem, Solution, Impact, Anti-Patterns
- Learnings reference each other (L042 → L104 → L099)
- Patterns propagate across agent fleet via shared repository

**Anti-Pattern**: Git history only
```bash
git log
# "fix: updated gate logic"  ← No context on WHY
```

**AGET Pattern**: Git history + learning documents
```bash
git log
# "fix: Gate discipline enforcement per L042"
# → Read L042 to understand complete pattern
```

**Example Learning Structure** (L042):
```markdown
# L42: Gate Execution Discipline

## Problem
Agents executing next gate without approval ("While we're at it...").

## Learning
Execute ONLY current gate deliverables, stop at boundary, WAIT for explicit GO.

## Impact
- Process violations: 2/10 → 9/10 (350% improvement)
- User control restored
```

**Learning References**:
- L051: Learning document structure specification
- L042: Gate execution discipline
- L084: Evidence before implementation
- L099: Multi-agent process enforcement

---

### 5. Lightweight Architecture (Zero Infrastructure)

**Principle**: No servers, no databases, no deployment overhead.

**Rationale**: Enterprise agent platforms require infrastructure (servers, monitoring, databases), creating operational burden. AGET uses filesystem + git, requiring zero infrastructure.

**In Practice**:
- Markdown files for configuration
- JSON for structured data (version.json)
- YAML for specifications
- Git for version control and distribution
- Local filesystem for state

**Infrastructure Comparison**:

| Approach | Infrastructure | Setup Time | Cost |
|----------|----------------|------------|------|
| **AgentOps/ALM** | Servers, databases, monitoring | Days | $100-500/month |
| **AGET** | Git repository | Minutes | $0 |

**Trade-off**: AGET sacrifices runtime observability for zero operational overhead. Suitable for human-supervised collaboration where human reviews outputs continuously.

**Anti-Pattern**: "Set up Kubernetes cluster for agent deployment"
**AGET Pattern**: `git clone` → `wake up` → start working

---

### 6. Recursive Supervision Model

**Principle**: Every agent is a worker; supervision is a capability, not a type.

**Rationale**: Enables multi-level hierarchies and fractal growth patterns. Supervisors themselves are supervised by humans or other supervisors.

**In Practice**:
```
Human (supervises) → fleet-supervisor-AGET (supervises) → 10 worker agents
```

- Workers can be promoted to supervisors via configuration
- Supervisors have direct reports (explicit list)
- Same patterns apply at every level
- Clear accountability chains

**Architectural Implication**: No special "supervisor" runtime—just a worker agent with supervision capabilities enabled via configuration.

**Learning References**:
- L099: Recursive supervision model
- L099: Multi-agent process enforcement
- L100: File-based worker coordination

---

### 7. Version Progression Framework

**Principle**: Agents have compliance levels with migration protocols.

**Rationale**: As framework evolves, agents must be upgradeable in controlled manner. Version progression framework ensures:
- Backward compatibility
- Migration paths
- Contract testing
- Compliance validation

**In Practice**:
- v2.0 → v2.5.0 → v2.6.0 → v2.7.0 progression
- Each version has migration guide
- Contract tests validate compliance
- New agents created at current version floor (v2.7.0+)

**Version Semantics**:
```
v2.7.0
│ │ │
│ │ └─ Patch: Bug fixes, documentation
│ └─── Minor: New capabilities, non-breaking changes
└───── Major: Breaking changes, architecture shifts
```

**Example**: v2.7.0 adds portfolio governance
- New agents must include portfolio classification
- Existing agents migrate via protocol
- Contract tests validate portfolio field exists

---

## Design Decisions and Trade-offs

### Trade-off 1: Human-Supervised vs Fully Autonomous

**Decision**: Human-supervised collaboration
**Rationale**: Complex software engineering requires human judgment
**Trade-off**: Slower execution vs. higher quality and control
**When to reconsider**: If bounded, well-defined tasks dominate (then consider autonomous frameworks)

---

### Trade-off 2: Configuration Files vs API/Runtime

**Decision**: Configuration files (AGENTS.md)
**Rationale**: Version control, portability, auditability
**Trade-off**: Static configuration vs. dynamic runtime behavior
**When to reconsider**: If runtime behavior changes frequently based on external state

---

### Trade-off 3: Zero Infrastructure vs Observability

**Decision**: Zero infrastructure (filesystem + git)
**Rationale**: Operational simplicity, no hosting costs
**Trade-off**: No runtime telemetry vs. no operational burden
**When to reconsider**: If production monitoring critical (then integrate with AgentOps/ALM)

---

### Trade-off 4: Universal CLI Compatibility vs Tool-Specific Features

**Decision**: Universal compatibility (AGENTS.md standard)
**Rationale**: Avoid vendor lock-in, portability
**Trade-off**: Can't use tool-specific features vs. works everywhere
**When to reconsider**: If single tool dominates and offers critical unique features

---

## Architectural Constraints

### Constraint 1: Human Must Approve Substantial Changes

**Rationale**: Software engineering has high cost of errors (production incidents, data loss, security breaches). Human approval gates reduce risk.

**Implication**: Agent cannot execute multi-gate plan without explicit GO at each gate.

**Enforcement**: Gate discipline pattern (L042), supervisor critique (L099)

---

### Constraint 2: Configuration Must Be Version-Controlled

**Rationale**: Agent behavior changes over time. Without version control, reproducibility and auditability impossible.

**Implication**: All configuration files (AGENTS.md, version.json, specs) committed to git.

**Enforcement**: Contract tests validate configuration exists and is well-formed.

---

### Constraint 3: Learning Documents Are Immutable After Publish

**Rationale**: Learnings reference each other by L-number. If learning content changes, references break.

**Implication**: Learnings can be deprecated (marked obsolete) but not edited after publish.

**Exception**: Typo fixes, formatting improvements (content-preserving changes).

**Enforcement**: Social convention, git history preserves original.

---

## Guiding Questions for New Features

When considering new AGET features, ask:

1. **Does it preserve human control?**
   - If feature reduces human visibility or decision-making, reconsider

2. **Can it work via configuration files?**
   - If requires custom runtime or API, evaluate trade-off carefully

3. **Is it CLI-tool agnostic?**
   - If only works with one tool, is it worth vendor lock-in?

4. **Does it require infrastructure?**
   - If needs servers/databases, what's operational burden? Worth it?

5. **Can the pattern scale recursively?**
   - If applies to workers but not supervisors (or vice versa), is design flawed?

6. **How do we validate compliance?**
   - If no contract test possible, how do we ensure correctness?

7. **What learning does it generate?**
   - Will this feature produce learnings for other agents? Reusable patterns?

---

## Evolution Philosophy

### Principle: "Built by Use, Not by Speculation"

**Approach**: AGET patterns emerge from practical experience, not theoretical design.

**Process**:
1. **Encounter problem** in real agent work
2. **Solve problem** with incremental approach
3. **Document learning** (L-numbered document)
4. **Test pattern** with other agents
5. **Formalize pattern** if broadly useful
6. **Integrate into templates** for new agents

**Anti-Pattern**: "Design comprehensive framework upfront"
**AGET Pattern**: "Solve real problems, extract patterns, formalize gradually"

**Example**: L042 (Gate Discipline)
- Emerged from agent violations (executing without approval)
- Solved with explicit WAIT instruction
- Documented impact (2/10 → 9/10 process rating)
- Integrated into substantial change protocol
- Now foundational pattern in all agents

---

### Principle: "Evidence Over Opinion"

**Approach**: Changes justified by quantitative evidence, not preferences.

**Evidence Types**:
- **Time savings**: "Learning discovery: 2-5min → <30s" (L101)
- **Quality improvement**: "Process rating: 2/10 → 9/10" (L042)
- **Error reduction**: "Repository misconfiguration: 7.7% → ~0%" (L158)
- **User impact**: "Stakeholder comprehension: +80%" (L148)

**Anti-Pattern**: "I think we should add feature X because it feels right"
**AGET Pattern**: "Problem Y caused Z waste (quantified). Feature X reduces waste by W%. Here's evidence."

**Example**: L104 (Gate Sizing Heuristic)
- Problem: Over-gating (7 gates for internal-only work)
- Evidence: More time planning than executing (red flag)
- Solution: Decision framework (2-3 baseline + risk factors)
- Impact: Right-sized gates for task complexity

---

## Future Evolution Opportunities

### Opportunity 1: Federation Protocol

**Vision**: AGET supervisors coordinate across organizational boundaries.

**Approach**:
- Define "Agent Card" for AGET fleets
- Capability discovery protocol
- Privacy-preserving learning exchange
- Could adopt A2A protocol (Agent2Agent)

**Use Case**: Two organizations with AGET fleets share sanitized learnings.

**Status**: Research (v2.8+)

---

### Opportunity 2: Model Context Protocol (MCP) Integration

**Vision**: Standardize how AGETs access external data sources.

**Approach**:
- Make patterns/learnings discoverable via MCP
- Standardized tool access
- "USB-C for AGET" - plug into any compatible data source

**Use Case**: Agent queries pattern repository via MCP instead of direct file reads.

**Status**: Research (v2.8+)

---

### Opportunity 3: Learning Network

**Vision**: Public repository of sanitized L-numbered learnings.

**Approach**:
- Privacy-preserving pattern sharing across AGET users
- Curated learning library
- Community contributions
- Attribution and versioning

**Use Case**: User discovers L084 (evidence before implementation) in public learning network, adopts it for their fleet.

**Status**: Community interest (v3.0+)

---

## Key Insights

### 1. Human-AI Collaboration is Not Agent Autonomy

Traditional agent frameworks optimize for autonomous execution. AGET optimizes for human-AI partnership quality.

**Implication**: Different patterns, different metrics, different success criteria.

---

### 2. Configuration Beats Infrastructure

Zero-infrastructure approach (markdown + git) trades runtime observability for operational simplicity.

**Implication**: Suitable for teams where human supervision provides continuous feedback loop.

---

### 3. Universal Compatibility Beats Vendor Features

Avoiding vendor lock-in enables flexibility as CLI tool landscape evolves.

**Implication**: AGET's longevity tied to standard (AGENTS.md), not specific tool.

---

### 4. Organizational Memory Compounds Value

Learning system creates compounding knowledge base across agent fleet.

**Implication**: 10th agent benefits from patterns discovered by first 9 agents.

---

### 5. Recursive Patterns Enable Scale

Same patterns apply to workers, advisors, and supervisors.

**Implication**: AGET can scale from 10 → 100 → 1000 agents without architectural redesign.

---

## Related Documentation

- **[Core Patterns](./CORE_PATTERNS.md)** - Specific patterns implementing philosophy
- **[Getting Started](./GETTING_STARTED.md)** - Practical application for first agent
- **[Framework Homepage](./README.md)** - Overview and positioning

---

## Learning References

This philosophy document synthesizes insights from:
- L042: Gate execution discipline
- L051: Learning document structure
- L084: Evidence before implementation
- L099: Recursive supervision model
- L099: Multi-agent process enforcement
- L100: File-based worker coordination
- L104: Gate sizing heuristic
- L143: Framework landscape positioning
- L146: Configuration size management

---

*Design Philosophy v2.7.0 - Last updated: 2025-10-13*
