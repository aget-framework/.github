# AGET Framework

**Fleet Coordination for the CLI Coding Tools You Already Use**

Deploy AI coding agents with confidence. AGET provides specification-based governance, version control, and shared learning across Claude Code, Cursor, Aider, Windsurf—through an open standard. Zero infrastructure required.

**Solve**: Version drift, deployment breaks, compliance gaps, isolated agent learnings across your fleet.

[![Version](https://img.shields.io/badge/version-2.11.0-blue)](https://github.com/aget-framework/aget/releases/tag/v2.11.0)
[![License](https://img.shields.io/badge/license-MIT-green)](LICENSE)
[![Release Date](https://img.shields.io/badge/released-2025--12--24-lightgrey)](https://github.com/aget-framework/aget/releases/latest)

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
  "aget_version": "2.11.0",
  "instance_type": "AGET",
  "migration_history": [
    "v2.7.0 -> v2.8.0: 2025-11-01",
    "v2.8.0 -> v2.9.0: 2025-11-15",
    "v2.9.0 -> v2.10.0: 2025-12-13",
    "v2.10.0 -> v2.11.0: 2025-12-24"
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
  "aget_version": "2.11.0",
  "instance_type": "AGET",
  "domain": "legal_contract_analysis"
}
```

Version progression: v2.5 → v2.6 → v2.7 → v2.8 → v2.9 → v2.10 → v2.11
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

## Use Cases

### Legal Practice

**Principal**: Lawyer handling contract review
**Agents**: 5 specialized (analysis, research, drafting, compliance, case management)
**Outcome**: 3x caseload with maintained quality (10x faster contract analysis)
**Impact**: More accessible legal representation

### Healthcare

**Principal**: Doctor diagnosing complex cases
**Agents**: 3 specialized (records pre-processing, literature research, diagnosis suggestions)
**Outcome**: More patients seen, better diagnoses (pattern recognition from literature)
**Impact**: Improved patient care quality

### Software Development

**Principal**: Development team shipping code
**Agents**: 8 specialized (code review, testing, documentation, standards, debugging)
**Outcome**: Higher code quality, fewer bugs, better architecture
**Impact**: More reliable software

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

### v2.11 (Current) - Memory Architecture + Public Governance
**Released**: 2025-12-24

- ✅ Memory Architecture (L335): 6-layer information model
- ✅ L352 Traceability Pattern: Requirement-to-test traceability
- ✅ R-PUB-001 Public Release Completeness (8 requirements)
- ✅ Post-release validation automation
- ✅ Public framework governance (VERSIONING.md, RELEASES.md, UPGRADING.md)
- ✅ Configurable wake-up output
- ✅ Version migration protocol (R-REL-006)

### v2.10 - Capability Composition Architecture
**Released**: 2025-12-24 (retroactive)

- ✅ 6 agent type specifications
- ✅ Executive Advisor pattern (5W+H knowledge architecture)
- ✅ Domain Specialist pattern (structured outputs)
- ✅ Theoretical grounding protocol (L332)

### v2.9 - Information Storage Standardization
**Released**: 2025-11-24 (partial - advisor family only)

- ✅ Session location standard (`sessions/` at root)
- ✅ Session metadata standard (YAML frontmatter)
- ✅ Memory layer for advisors (`.memory/` structure)
- ✅ 5-layer knowledge architecture
- ✅ Fleet-wide migration complete (28 agents)

### v2.12 (Next) - Planned
- 📋 Template consistency verification
- 📋 Historical release backfill (v2.1-v2.9 for aget/)
- 📋 R-PUB-001 contract test coverage
- 📋 CONTRIBUTING.md and community infrastructure

### v3.0 (Future) - Multi-Agent Coordination
- 🔮 Agent discovery and routing
- 🔮 Task queue and delegation
- 🔮 Cross-agent collaboration patterns
- 🔮 Fleet-level analytics and metrics

---

## Community

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

MIT License - See [LICENSE](LICENSE) for details

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
