# AGET Framework

**Persistent Domain Intelligence for the CLI Coding Tools You Already Use**

Build AI agents that accumulate domain expertise serving your decisions. AGET provides session continuity, shared memory architecture, and governance patterns across Claude Code, Codex CLI, Gemini CLI—through an open standard. Zero infrastructure required.

**Solve**: Lost context between sessions, knowledge that resets daily, agents that can't learn from each other, deployment confidence across your fleet.

[![Version](https://img.shields.io/badge/version-3.7.0-blue)](https://github.com/aget-framework/aget/releases/tag/v3.7.0)
[![License](https://img.shields.io/badge/license-Apache%202.0-blue)](LICENSE)
[![Release Date](https://img.shields.io/badge/released-2026--03--01-lightgrey)](https://github.com/aget-framework/aget/releases/latest)

---

## What is AGET?

AGET enables AI agents that build persistent domain knowledge serving human decisions—with session continuity, shared learning, and governed autonomy across CLI tools. Think of it as the knowledge layer for your AI team.

### How It Works

- **Persistent Domain Knowledge** - Agents accumulate expertise that compounds across sessions
- **Session Continuity** - Pick up where you left off with structured memory architecture
- **Shared Learning** - Propagate insights across your fleet (`.aget/evolution/`)
- **Lifecycle Governance** - Gated releases, contract testing, deployment verification
- **Universal CLI Compatibility** - Works with Claude Code, Codex CLI, Gemini CLI
- **Open Standard** - AGENTS.md enables ecosystem innovation

### Specification-First Development

AGET brings formal requirements engineering to agent fleet management:

**EARS Patterns** - Write unambiguous specifications:
- **Ubiquitous**: "The system SHALL always..."
- **Event-driven**: "WHEN [trigger] the system SHALL..."
- **State-driven**: "WHILE [condition] the system SHALL..."
- **Optional**: "WHERE [feature enabled] the system SHALL..."
- **Conditional**: "IF [condition] THEN the system SHALL..."

**Contract Testing** - Validate deployments before production (7-30 tests per agent)

**Validation Framework** - Every specification includes formal validation tests

**Result**: Deploy with confidence—formal specs → validated implementations → verified deployments.

See [template-spec-engineer-aget](https://github.com/aget-framework/template-spec-engineer-aget) for specification engineering capabilities.

### Who It's For

- **Individual Practitioners** building persistent AI expertise in a specific domain
- **Power Users** coordinating specialized agents across domains
- **AI Tool Builders** wanting a governance layer for agent deployments

---

## Quick Start

### 1. Choose Your Template

**12 Archetypes** — Each with specialized skills and ontology (v3.5.0+, updated v3.7.0):

| Template | Archetype | Key Skills | Primary Use Case |
|----------|-----------|------------|------------------|
| [**template-supervisor-aget**](https://github.com/aget-framework/template-supervisor-aget) | supervisor | broadcast-fleet, review-agent, escalate-issue, create-aget | Fleet coordination (**recommended start**) |
| [**template-worker-aget**](https://github.com/aget-framework/template-worker-aget) | worker | execute-task, report-progress | Task execution, foundation |
| [**template-developer-aget**](https://github.com/aget-framework/template-developer-aget) | developer | run-tests, lint-code, review-pr | Code development |
| [**template-advisor-aget**](https://github.com/aget-framework/template-advisor-aget) | advisor | assess-risk, recommend-action | Persona-based guidance |
| [**template-consultant-aget**](https://github.com/aget-framework/template-consultant-aget) | consultant | assess-client, propose-engagement | Strategic engagements |
| [**template-analyst-aget**](https://github.com/aget-framework/template-analyst-aget) | analyst | analyze-data, generate-report | Data analysis |
| [**template-architect-aget**](https://github.com/aget-framework/template-architect-aget) | architect | design-architecture, assess-tradeoffs | System design |
| [**template-researcher-aget**](https://github.com/aget-framework/template-researcher-aget) | researcher | search-literature, document-finding | Research workflows |
| [**template-operator-aget**](https://github.com/aget-framework/template-operator-aget) | operator | handle-incident, run-playbook | Operations/DevOps |
| [**template-executive-aget**](https://github.com/aget-framework/template-executive-aget) | executive | make-decision, review-budget | Executive advisory |
| [**template-reviewer-aget**](https://github.com/aget-framework/template-reviewer-aget) | reviewer | review-artifact, provide-feedback | Quality review |
| [**template-spec-engineer-aget**](https://github.com/aget-framework/template-spec-engineer-aget) | spec-engineer | validate-spec, generate-requirement | Requirements engineering |

**All templates include**: 15 universal skills (wake-up, wind-down, check-health, study-up, record-lesson, etc.) + archetype-specific skills above.

#### Ontology-Driven Design (v3.5.0)

Each archetype includes a **formal ontology** defining domain vocabulary:

```
Vocabulary → Specification → Implementation
```

| Archetype | Concepts | Clusters | Example Terms |
|-----------|----------|----------|---------------|
| Developer | 10 | 4 | Codebase, TestSuite, PullRequest, LintRule |
| Supervisor | 8 | 3 | Fleet, Agent, Escalation, Broadcast |
| Advisor | 6 | 2 | Risk, Recommendation, Persona |
| Architect | 7 | 3 | Architecture, Component, Tradeoff |

**Benefits**: Precision (formal vocabulary prevents ambiguity), Consistency (same concepts across instances), Extensibility (add domain-specific terms).

See [`ontology/ONTOLOGY_{archetype}.yaml`](https://github.com/aget-framework/template-developer-aget/blob/main/ontology/ONTOLOGY_developer.yaml) in any template.

### 2. Create Your Agent

```bash
# Clone template
gh repo clone aget-framework/template-worker-aget my-agent-name
cd my-agent-name

# Configure identity
vim .aget/version.json  # Set agent_name, domain, instance_type

# Verify deployment
python3 -m pytest tests/ -v  # Contract tests must pass
```

### 3. Start Using

```bash
# In Claude Code, Codex CLI, Gemini CLI, or other supported tools
claude code my-agent-name/

# Agent uses AGENTS.md configuration automatically
# No additional setup required (universal CLI compatibility)
```

---

## Why AGET?

### Mission-Driven

Enable your agents to succeed at making their principals successful.

Success cascades from framework quality to agent effectiveness to principal outcomes:

```
Better Principal Outcomes  ← Faster decisions, deeper analysis, fewer knowledge gaps
    ↑
Principal Success          ← Practitioners deliver better work with accumulated domain expertise
    ↑
Agent Success              ← Effective augmentation with persistent knowledge and deployment confidence
    ↑
Framework Quality          ← AGET ensures governance, learning, compliance
```

**Goal**: Not just "manage agents" but enable principal success through accumulated domain intelligence and deployment confidence.

### Ecosystem Approach

AGET doesn't replace your CLI tools—it coordinates them. Works alongside Claude Code, Codex CLI, Gemini CLI to bring fleet-level capabilities: version control, shared learning, lifecycle governance.

**Complementary, not competitive**: AGET + CLI Tools work together to enable your agents.

### Open Innovation

**AGENTS.md** open standard means anyone can adopt, extend, or integrate. No vendor lock-in, no proprietary formats—just universal CLI compatibility and portable knowledge.

---

## Architecture & Technical Foundation

### 5-Layer Knowledge Architecture

Separates framework knowledge (portable) from domain knowledge (specific):

| Layer | Location | Purpose | Example Content |
|-------|----------|---------|-----------------|
| **Framework** | `.aget/` | Process patterns, learnings | `.aget/evolution/L*.md` (portable to any domain) |
| **Agent Type** | Template | Role-specific capabilities | Advisor personas, worker task patterns |
| **Instance** | `.aget/version.json` | Agent identity, config | `agent_name`, `aget_version`, `domain` |
| **Memory** | `.memory/` | Engagement state (advisors) | `.memory/clients/{id}/` relationship history |
| **Domain** | Root | Principal's work product | `sessions/*.md`, `knowledge/*.md` |

**Design principle**: Framework knowledge (`.aget/`) is portable across domains. Domain knowledge (root) is principal-owned and specific.

### Specification-Based Governance

Every agent, feature, and release is formally specified and validated:

**Specification Format**:
```yaml
# .aget/specs/EXAMPLE_SPEC_v1.0.yaml
requirements:
  R1_capability_check:
    statement: "Agent SHALL validate version.json on startup"
    validation:
      test: "Contract test test_version_file_exists()"
      threshold: "PASS required for deployment"
```

**Contract Testing**:
- 7-30 pytest-based tests per agent
- Validates: Identity, configuration, capabilities, compliance
- Runs: Pre-commit, pre-deployment, CI/CD
- Example: `pytest tests/test_contract.py -v`

**Version Compliance**:
```json
// .aget/version.json
{
  "agent_name": "my-research-agent",
  "aget_version": "3.7.0",
  "instance_type": "AGET",
  "template": "researcher",
  "migration_history": [
    "v2.9.0 -> v2.10.0: 2025-12-13",
    "v2.10.0 -> v2.11.0: 2025-12-24",
    "v2.11.0 -> v2.12.0: 2025-12-25",
    "v2.12.0 -> v3.0.0: 2025-12-28",
    "v3.0.0 -> v3.1.0: 2026-01-04",
    "v3.5.0 -> v3.6.0: 2026-02-21",
    "v3.6.0 -> v3.7.0: 2026-03-01"
  ]
}
```

Migration history tracked, compliance validated via contract tests.

### Universal CLI Compatibility (AGENTS.md Standard)

Open standard configuration works across all CLI coding tools:

```markdown
# AGENTS.md
version: "1.0"
agent:
  name: "my-research-agent"
  type: "researcher"
  domain: "market_analysis"
  capabilities:
    - search_literature
    - document_finding
    - analyze_data
```

No vendor lock-in: Same configuration file works with Claude Code, Codex CLI, Gemini CLI. Agent portability preserved.

### Fleet Coordination Model

```
┌─────────────────────────────────────────────────────────┐
│ PRINCIPALS                                              │
│ (Domain Practitioners)                                  │
└─────────────────────────────────────────────────────────┘
                        ↑
┌─────────────────────────────────────────────────────────┐
│ AI CODING AGENTS                                        │
│ (Workers, Advisors, Supervisors, Consultants)           │
└─────────────────────────────────────────────────────────┘
                ↑               ↑
        ┌───────────┐   ┌──────────────┐
        │   AGET    │   │  CLI TOOLS   │
        │           │←→│              │
        │ • Version │   │ • Claude Code│
        │ • Learning│   │ • Codex CLI  │
        │ • Specs   │   │ • Gemini CLI │
        │ • Govern  │   │              │
        └───────────┘   └──────────────┘
              ↑                 ↑
        AGENTS.md         Universal CLI
        (open std)        Compatibility
```

**Complementary architecture**: AGET provides governance layer. CLI tools provide execution environment. Together they enable confident multi-agent deployment.

### Agent Hierarchy

AGET templates form a deliberate authority hierarchy — agents have different levels of autonomy and accountability:

```
Supervisor  ─── Fleet coordination, escalation, cross-agent learning
    ↑
Advisor     ─── Read-only guidance (5 personas: teacher, mentor, consultant, guru, coach)
    ↑
Worker      ─── Task execution, the foundation archetype for all agents
```

**10 specialized archetypes** extend this hierarchy with domain-specific capabilities (developer, analyst, architect, researcher, operator, executive, reviewer, spec-engineer, consultant). Each inherits from worker and can operate alongside advisors or under supervisor coordination.

The **[supervisor template](https://github.com/aget-framework/template-supervisor-aget)** manages fleet-level operations: agent review, learning propagation, issue escalation, and cross-agent coordination. **Recommended starting point** — start with a supervisor, then use it to create your fleet agents.

---

## Key Features

### Version Control

Track agent identity, manage upgrades, ensure compliance:
```json
// .aget/version.json
{
  "agent_name": "my-research-agent",
  "aget_version": "3.7.0",
  "instance_type": "AGET",
  "template": "researcher",
  "domain": "market_analysis"
}
```

Version progression: v2.5 → v2.6 → v2.7 → v2.8 → v2.9 → v2.10 → v2.11 → v2.12 → v3.0.0 → v3.1.0 → v3.2.0 → v3.2.1 → v3.3.0 → v3.4.0 → v3.5.0 → v3.6.0 → **v3.7.0**
Migration history tracked, contract tests enforce compliance.

### Shared Learning

Propagate insights across your fleet:
```markdown
# .aget/evolution/L315_pattern_discovered.md
## Problem: Agents duplicated work (no shared context)
## Learning: Centralize learnings in .aget/evolution/
## Protocol: Pattern deployment across fleet
```

Collective intelligence: Fleet gets smarter together, not individually.

### Lifecycle Governance

Gated releases with human supervision:
- Incremental go/no-go decision points
- Contract testing (deployment verification)
- Evidence-based planning
- Honest gap recording (prediction accuracy is metric)

### Universal CLI Compatibility

AGENTS.md configuration works across:
- ✅ Claude Code (primary)
- ✅ Codex CLI (supported)
- ✅ Gemini CLI (supported)
- ⚠️ Cursor, Aider (experimental)
- ✅ Any CLI tool supporting configuration files

No tool lock-in. No vendor-specific formats. Just open standards.

---

## What AGET Solves

### Session Continuity

**Pain**: "I explain the same context every session"

Your AI agent forgets everything between sessions. You waste the first 10 minutes re-explaining project history, decisions made, and work in progress.

AGET's lifecycle protocols preserve context across sessions automatically. Wake-up loads previous state; wind-down captures decisions for next session.

[See it in action: Session protocols](https://github.com/aget-framework/aget/blob/main/docs/TEMPLATE_STRUCTURE_GUIDE.md)

### Multi-Agent Coordination

**Pain**: "My agents don't know about each other"

You have 5 agents across 5 projects. They duplicate work, contradict each other, and can't share what they've learned.

AGET's fleet management coordinates agents with supervisor/worker patterns, shared configuration, and learning propagation across your entire agent fleet.

[See it in action: Fleet templates](https://github.com/aget-framework/template-worker-aget)

### Accumulated Expertise

**Pain**: "My AI doesn't get smarter over time"

You've been working with AI tools for months. They've helped solve hundreds of problems. But they haven't learned anything — no patterns captured, no lessons retained, no expertise compounding.

AGET's evolution tracking captures decisions, learnings, and patterns as permanent, searchable knowledge. Your agent gets more effective with every session.

[See it in action: Learning architecture](https://github.com/aget-framework/aget/blob/main/docs/LAYER_ARCHITECTURE.md)

### Tool Portability

**Pain**: "I'm locked into one tool"

Cursor today, Claude Code tomorrow, Windsurf next month. Your agent configuration shouldn't be hostage to vendor choice.

AGET works across all major CLI coding tools with a single AGENTS.md configuration. No vendor lock-in.

**Supported**: Claude Code, Codex CLI, Gemini CLI

[See the standard: AGENTS.md](https://github.com/aget-framework/template-worker-aget/blob/main/AGENTS.md)

### Audit Trail

**Pain**: "I can't explain what the AI decided"

Compliance asks: "Why did the AI make that choice?" You have no answer—just an endless chat transcript.

AGET's gated workflows and evolution tracking create an auditable trail of decisions, rationale, and outcomes. Every significant decision documented with PROJECT_PLAN pattern.

[See it in action: Governance patterns](https://github.com/aget-framework/aget/tree/main/docs)

---

## Documentation

- **[Versioning Guide](https://github.com/aget-framework/aget/blob/main/docs/VERSIONING.md)** - Version system and compatibility
- **[Upgrade Guide](https://github.com/aget-framework/aget/blob/main/docs/UPGRADING.md)** - Safe upgrade procedures
- **[Releases](https://github.com/aget-framework/aget/blob/main/docs/RELEASES.md)** - Release process and quality standards
- **[Version History](https://github.com/aget-framework/aget/blob/main/docs/VERSION_HISTORY.md)** - Complete release timeline
- **[Template Structure Guide](https://github.com/aget-framework/aget/blob/main/docs/TEMPLATE_STRUCTURE_GUIDE.md)** - Understanding agent templates
- **[Layer Architecture](https://github.com/aget-framework/aget/blob/main/docs/LAYER_ARCHITECTURE.md)** - 5-layer knowledge architecture

---

## Differentiators

### vs Agent Runtimes (LangChain, MetaGPT)

**AGET**: Human-supervised coordination (not autonomous)
**Them**: Autonomous execution runtimes
**Difference**: AGET brings governance and learning to CLI tools you already use

### vs ALM Platforms (AgentOps, Salesforce ALM)

**AGET**: Lightweight, zero-infrastructure (markdown + git)
**Them**: Cloud platforms, observability infrastructure
**Difference**: AGET works locally with no servers, no overhead

### vs Raw CLI Tools (Claude Code, Cursor alone)

**AGET**: Fleet coordination, shared learning, version control
**Them**: Single-agent, no versioning, no cross-agent learning
**Difference**: AGET enables coordination across tools and agents

---

## Roadmap

### v3.7.0 (Current) - Quality Reconciliation
**Released**: 2026-03-01

- ✅ **Skill Count Reconciliation**: Spec/README/deployed aligned at 15 universal skills
- ✅ **Post-Release Validation**: post_release_validation.py 12/12 checks passing
- ✅ **Content Integrity Validators**: .py version string validator + V-tests
- ✅ **SOP Lifecycle Governance**: AGET_SOP_SPEC v1.2.0 (CAP-SOP-006, 8 requirements)
- ✅ **Evidence-Based Positioning**: POSITIONING_SPEC v1.2.0, IDENTITY_SPEC v1.2.0 (L610)
- ✅ **Verb Vocabulary Reconciliation**: 25 compliant verbs, aget-studyup → aget-study-up
- ✅ **Governance Doc Refresh**: CHARTER, MISSION, SCOPE_BOUNDARIES updated
- ✅ **README Conformance**: All 13 repo READMEs verified
- ✅ **Specification Enhancement**: /aget-enhance-spec skill (SOP + SKILL-041)

### v3.6.0 - Infrastructure Maturation
**Released**: 2026-02-21

- ✅ **Release Observability**: 5 scripts — validation_logger, run_gate, release_snapshot, propagation_audit, health_logger
- ✅ **Content Integrity**: 6 dimensions of claim-vs-reality drift fixed across all repos
- ✅ **Canonical Scripts v2.0.0**: C3+C1 hybrid architecture (config-driven + hook-based extensions)
- ✅ **Universal Skills**: 14 skills (added aget-studyup)
- ✅ **Vocabulary Precision**: 4 compliance behavioral terms (VOCABULARY_SPEC v1.16.0)
- ✅ **Platform Claims**: Claude Code, Codex CLI, Gemini CLI (Cursor/Aider → Experimental)
- ✅ **Conformance Tool v1.3.0**: 12/12 templates CONFORMANT at deep depth

### v3.5.0 - Archetype Customization
**Released**: 2026-02-14

- ✅ **Archetype Ontologies**: 12 ONTOLOGY_{archetype}.yaml files with 87 domain concepts
- ✅ **Archetype Skills**: 26 archetype-specific skills (2-3 per archetype)
- ✅ **Universal Skills**: 13 skills shared across all templates
- ✅ **Skill Specifications**: EARS-compliant specs for all 39 skills
- ✅ **Ontology-Driven**: Vocabulary → Specification → Instance pattern (L486)

### v3.4.0 - Session Skills Maturity + Governance Formalization
**Released**: 2026-01-18

- ✅ **Session Protocol Enhancements**: Re-entrancy guard, calendar awareness, sanity gate
- ✅ **Cross-CLI Validation**: Tested on Claude Code, Codex CLI, Gemini CLI
- ✅ **Governance Formalization**: Release, behavioral, and artifact governance patterns
- ✅ **Spec-First Documentation**: AGET_IDENTITY_SPEC.yaml, AGET_POSITIONING_SPEC.yaml
- ✅ **New SOPs**: L-doc creation, Enhancement Request, PROJECT_PLAN archival
- ✅ **Template Infrastructure**: sops/ with SOP_escalation.md in all 12 templates (R-TEMPLATE-001)
- ✅ **codemeta.json + CITATION.cff**: Standard software metadata

### v3.3.0 - Shell Integration + Executable Knowledge Ontology
**Released**: 2026-01-10

- ✅ **Shell Orchestration**: aget.zsh, profiles.zsh (5 CLI backends)
- ✅ **SKOS-Compliant Vocabularies**: All 12 templates have ontologies (R-REL-015)
- ✅ **Ontology-Driven Creation** (L481, L482): Specs drive instances, not follow them
- ✅ **AGET_EXECUTABLE_KNOWLEDGE_SPEC.md**: Executable knowledge framework
- ✅ **AGET_EVOLUTION_SPEC.md**: Evolution entry standardization
- ✅ **18 New L-docs**: L451-L503 learnings documented

### v3.2.1 - Version Inventory Coherence
**Released**: 2026-01-04

- ✅ **L444 Remediation**: Version consistency across all version-bearing files
- ✅ **Coherence Testing**: New V-tests for AGENTS.md, manifest.yaml verification
- ✅ **SOP Update**: Gate 7 V-tests for version inventory coherence

### v3.2.0 - Specification Architecture
**Released**: 2026-01-04

- ✅ **7 New Specifications**: Testing, Release, Documentation, Organization, Error, Security, Project Plan
- ✅ **Naming Conventions Expansion**: 4 → 10 categories (Categories F-J)
- ✅ **Specification Index System**: INDEX.md (30 specs) + REQUIREMENTS_MATRIX.md (78 CAP requirements)
- ✅ **6 New Validators**: License, Agent Structure, Release Gate, L-doc Index, SOP, Homepage
- ✅ **Standardized Spec Headers**: YAML frontmatter with version, status, dependencies
- ✅ **Learnings**: L439, L440, L443

### v3.1.0 - Protocol Enforcement Through Infrastructure
**Released**: 2026-01-04

- ✅ **Cross-CLI Infrastructure**: Agent-agnostic scripts with --json output
- ✅ **Complete Session Lifecycle**: wake up → sanity check → wind down
- ✅ **Verification Architecture**: Source-verified constants, enforcement testing
- ✅ **L-doc Format v2**: Cross-agent discovery, adoption tracking
- ✅ **Fleet Validation Tooling**: validate_fleet.py, version_sync.py
- ✅ **Workflow Automation**: L-doc to GitHub Issue, cascade to SOP

### v3.0.0 - 5D Composition Architecture
**Released**: 2025-12-28

- ✅ **5D Directory Structure**: persona/, memory/, reasoning/, skills/, context/
- ✅ **Instance Type System**: aget (advisory), AGET (action-taking), template
- ✅ **Template field**: Replaces deprecated roles array
- ✅ All 6 templates migrated to v3.0 architecture
- ✅ 731 contract tests passing across framework
- ✅ Breaking changes: roles removed, manifest_version 3.0

### v2.12.0 - Capability Architecture Completion
**Released**: 2025-12-25

- ✅ Complete capability composition system (5 specs, 3 validators, 80 tests)
- ✅ Template manifest system for agent composition (manifest.yaml)
- ✅ Fleet migration enablement (6 pilots validated)
- ✅ Governance exemplar enforcement (L367)

### v2.11.0 - Memory Architecture + Public Governance
**Released**: 2025-12-24

- ✅ Memory Architecture (L335): 6-layer information model
- ✅ L352 Traceability Pattern: Requirement-to-test traceability
- ✅ R-PUB-001 Public Release Completeness (8 requirements)
- ✅ Version migration protocol (R-REL-006)

### v2.10.0 - Capability Composition Architecture
**Released**: 2025-12-13

- ✅ 6 agent type specifications
- ✅ Executive Advisor pattern (5W+H knowledge architecture)
- ✅ Theoretical grounding protocol (L332)

---

## Community

- **Roadmap**: [View planned enhancements](https://github.com/aget-framework/aget/issues)
- **GitHub Issues**: [File bugs, request features](https://github.com/aget-framework/aget/issues)
- **GitHub Releases**: [View releases, changelogs](https://github.com/aget-framework/aget/releases)

---

## Principles

### Abundance Mindset

- CLI tools are ecosystem partners (not competitors)
- Open standards enable collective innovation (not ownership advantage)
- Success measured by agent effectiveness (not market capture)
- Positive direction leads (affirmative framing, not negative contrast)

### Human-Supervised

- Agents augment human capability (not replace)
- Human judgment remains central (gated releases, incremental go/no-go)
- Learning investment valued (extract systematic insights)

### Evidence-Based

- Decisions grounded in data (not assumptions)
- Learnings extracted systematically (L-series evolution documents)
- Honest gap recording (prediction accuracy is metric)

---

## License

Apache 2.0 License - See [LICENSE](LICENSE) for details

---

## Team

| Role | Member |
|------|--------|
| Creator & Lead Maintainer | [@gmelli](https://github.com/gmelli) |

See [MAINTAINERS.md](https://github.com/aget-framework/aget/blob/main/MAINTAINERS.md) for governance details.

---

## Acknowledgments

Built with:
- **Claude Code** (Anthropic) - AI coding assistant
- **Universal CLI Compatibility** - Works across Claude Code, Codex CLI, Gemini CLI
- **Open Standards** - AGENTS.md specification
- **Community Contributors** - Thank you for making AGET better

---

**AGET Framework** - Persistent domain intelligence for governed agentic work

*Build AI agents that accumulate domain expertise serving your decisions*

---

**Maintained by** [@gmelli](https://github.com/gmelli) • [gabormelli.com](http://www.gabormelli.com/RKB/Gabor_Melli)
