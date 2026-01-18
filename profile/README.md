# AGET Framework

**Fleet Coordination for the CLI Coding Tools You Already Use**

Deploy AI coding agents with confidence. AGET provides specification-based governance, version control, and shared learning across Claude Code, Cursor, Aider, Windsurf—through an open standard. Zero infrastructure required.

**Solve**: Version drift, deployment breaks, compliance gaps, isolated agent learnings across your fleet.

[![Version](https://img.shields.io/badge/version-3.4.0-blue)](https://github.com/aget-framework/aget/releases/tag/v3.4.0)
[![License](https://img.shields.io/badge/license-Apache%202.0-blue)](LICENSE)
[![Release Date](https://img.shields.io/badge/released-2026--01--18-lightgrey)](https://github.com/aget-framework/aget/releases/latest)

---

## What is AGET?

AGET coordinates multiple specialized AI coding agents across CLI tools—with human supervision, shared learning, and version progression. Think of it as fleet management for your AI coding team.

### How It Works

- **Universal CLI Compatibility** - Works with Claude Code, Cursor, Aider, Windsurf
- **Version Control** - Track agent versions, manage upgrades, ensure compliance
- **Shared Learning** - Propagate insights across your fleet (`.aget/evolution/`)
- **Lifecycle Governance** - Gated releases, contract testing, deployment verification
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

**Ambiguity Detection** - Intelligence layer identifies unclear requirements

**Validation Framework** - Every specification includes formal validation tests

**Result**: Deploy with confidence—formal specs → validated implementations → verified deployments.

See [template-spec-engineer-aget](https://github.com/aget-framework/template-spec-engineer-aget) for specification engineering capabilities.

### Who It's For

- **Organizations** managing 5+ AI coding agents (version control, compliance)
- **Power Users** coordinating specialized agents (legal, healthcare, code analysis)
- **Development Teams** adopting AI agents with governance requirements

---

## Quick Start

### 1. Choose Your Template

| Template | Use Case | Capability |
|----------|----------|------------|
| [**template-worker-aget**](https://github.com/aget-framework/template-worker-aget) | General-purpose tasks | Flexible (can be AGET or aget) |
| [**template-advisor-aget**](https://github.com/aget-framework/template-advisor-aget) | Persona-based guidance | Advisory with internal state |
| [**template-consultant-aget**](https://github.com/aget-framework/template-consultant-aget) | Strategic analysis | Consultant persona |
| [**template-developer-aget**](https://github.com/aget-framework/template-developer-aget) | Code quality, debugging | Multi-repo analysis |
| [**template-spec-engineer-aget**](https://github.com/aget-framework/template-spec-engineer-aget) | Formal specifications | Requirements engineering |

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
# In Claude Code, Cursor, Aider, or Windsurf
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
Better Principal Outcomes  ← More cases handled, better diagnoses, fewer bugs
    ↑
Principal Success          ← Lawyers, doctors, developers deliver better work
    ↑
Agent Success              ← Effective augmentation with deployment confidence
    ↑
Framework Quality          ← AGET ensures governance, learning, compliance
```

**Goal**: Not just "manage agents" but enable principal success through agent effectiveness and deployment confidence.

### Ecosystem Approach

AGET doesn't replace your CLI tools—it coordinates them. Works alongside Claude Code, Cursor, Aider, Windsurf to bring fleet-level capabilities: version control, shared learning, lifecycle governance.

**Complementary, not competitive**: AGET + CLI Tools work together to enable your agents.

### Open Innovation

**AGENTS.md** open standard means anyone can adopt, extend, or integrate. **Shared learning repository** means collective intelligence grows together. No vendor lock-in, no proprietary formats—just universal CLI compatibility and portable knowledge.

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
  "agent_name": "my-legal-assistant",
  "aget_version": "3.4.0",
  "instance_type": "AGET",
  "template": "worker",
  "migration_history": [
    "v2.9.0 -> v2.10.0: 2025-12-13",
    "v2.10.0 -> v2.11.0: 2025-12-24",
    "v2.11.0 -> v2.12.0: 2025-12-25",
    "v2.12.0 -> v3.0.0: 2025-12-28",
    "v3.0.0 -> v3.1.0: 2026-01-04"
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
  name: "my-legal-assistant"
  type: "advisor"
  domain: "legal_contract_analysis"
  capabilities:
    - contract_analysis
    - legal_research
    - compliance_checking
```

No vendor lock-in: Same configuration file works with Claude Code, Cursor, Aider, Windsurf. Agent portability preserved.

### Fleet Coordination Model

```
┌─────────────────────────────────────────────────────────┐
│ PRINCIPALS                                              │
│ (Lawyers, Doctors, Developers)                          │
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
        │ • Learning│   │ • Cursor     │
        │ • Specs   │   │ • Aider      │
        │ • Govern  │   │ • Windsurf   │
        └───────────┘   └──────────────┘
              ↑                 ↑
        AGENTS.md         Universal CLI
        (open std)        Compatibility
```

**Complementary architecture**: AGET provides governance layer. CLI tools provide execution environment. Together they enable confident multi-agent deployment.

---

## Key Features

### Version Control

Track agent identity, manage upgrades, ensure compliance:
```json
// .aget/version.json
{
  "agent_name": "my-legal-assistant",
  "aget_version": "3.4.0",
  "instance_type": "AGET",
  "template": "worker",
  "domain": "legal_contract_analysis"
}
```

Version progression: v2.5 → v2.6 → v2.7 → v2.8 → v2.9 → v2.10 → v2.11 → v2.12 → v3.0.0 → v3.1.0 → v3.2.0 → v3.2.1 → v3.3.0 → v3.4.0
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
- ✅ Claude Code
- ✅ Cursor
- ✅ Aider
- ✅ Windsurf
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

### Organizational Memory

**Pain**: "Knowledge walks out when people leave"

Your best developer leaves. So does everything they taught the AI—it's trapped in their chat history, not your organization's knowledge base.

AGET's evolution tracking captures decisions, learnings, and context as permanent organizational memory. 590+ learning documents across our fleet, accessible to any session.

[See it in action: Learning architecture](https://github.com/aget-framework/aget/blob/main/docs/LAYER_ARCHITECTURE.md)

### Tool Portability

**Pain**: "I'm locked into one tool"

Cursor today, Claude Code tomorrow, Windsurf next month. Your agent configuration shouldn't be hostage to vendor choice.

AGET works across all major CLI coding tools with a single AGENTS.md configuration. No vendor lock-in.

**Supported**: Claude Code, Cursor, Aider, Windsurf

[See the standard: AGENTS.md](https://github.com/aget-framework/template-worker-aget/blob/main/AGENTS.md)

### Audit Trail

**Pain**: "I can't explain what the AI decided"

Compliance asks: "Why did the AI make that choice?" You have no answer—just an endless chat transcript.

AGET's gated workflows and evolution tracking create an auditable trail of decisions, rationale, and outcomes. Every significant decision documented with PROJECT_PLAN pattern.

[See it in action: Governance patterns](https://github.com/aget-framework/aget/tree/main/docs)

---

## Patterns We're Building

These patterns are industry-validated. We're building AGET templates to support them.

| Pattern | Status | Template |
|---------|--------|----------|
| Research Fleet | Designing | template-research-advisor-aget |
| Consulting Practice | Roadmap | template-practice-advisor-aget |
| Compliance Teams | Roadmap | template-compliance-worker-aget |

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

### v3.4.0 (Current) - Session Skills Maturity + Governance Formalization
**Released**: 2026-01-18

- ✅ **Session Protocol Enhancements**: Re-entrancy guard, calendar awareness, sanity gate
- ✅ **Cross-CLI Validation**: Tested on Claude Code, Codex CLI, Gemini CLI
- ✅ **Governance Formalization**: Release, behavioral, and artifact governance patterns
- ✅ **Spec-First Documentation**: AGET_IDENTITY_SPEC.yaml, AGET_POSITIONING_SPEC.yaml
- ✅ **New SOPs**: L-doc creation, Enhancement Request, PROJECT_PLAN archival
- ✅ **Template Infrastructure**: sops/ with SOP_escalation.md in all 12 templates (R-TEMPLATE-001)
- ✅ **codemeta.json + CITATION.cff**: Standard software metadata

### v3.5.0 (Next) - Core Entity Vocabulary
- 📋 Core entity definitions (Person, Document, Task)
- 📋 Entity inheritance mechanism
- 📋 validate_entity_inheritance.py
- 📋 ENTITY_EXTENSION_GUIDE.md

### v3.6.0 (Planned) - Vocabulary Intelligence
- 📋 Auto-link term suggestions
- 📋 Term hover previews
- 📋 Knowledge graph visualization
- 📋 Vocabulary reverse index (backlinks)

### v3.7.0 (Conceptual) - Advanced Validators
- 📋 Remaining P2/P3 validators
- 📋 Full validator coverage for all specs
- 📋 Automated spec compliance checking

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
- **Universal CLI Compatibility** - Works across Cursor, Aider, Windsurf
- **Open Standards** - AGENTS.md specification
- **Community Contributors** - Thank you for making AGET better

---

**AGET Framework** - Deploy AI agents with confidence

*Fleet coordination for the CLI coding tools you already use*

---

**Maintained by** [@gmelli](https://github.com/gmelli) • [gabormelli.com](http://www.gabormelli.com/RKB/Gabor_Melli)
