# AGET Framework

**Fleet Coordination for the CLI Coding Tools You Already Use**

Enable your AI agents to make the universe more beautiful. AGET brings version control, shared learning, and lifecycle governance to Claude Code, Cursor, Aider, Windsurf, and more—through an open standard. Zero infrastructure required.

[![Version](https://img.shields.io/badge/version-2.9.0-blue)](https://github.com/gmelli/private-supervisor-AGET/releases/tag/v2.9.0)
[![License](https://img.shields.io/badge/license-MIT-green)](LICENSE)

---

## What is AGET?

AGET coordinates multiple specialized AI coding agents across CLI tools—with human supervision, shared learning, and version progression. Think of it as fleet management for your AI coding team.

### How It Works

- **Universal CLI Compatibility** - Works with Claude Code, Cursor, Aider, Windsurf
- **Version Control** - Track agent versions, manage upgrades, ensure compliance
- **Shared Learning** - Propagate insights across your fleet (.aget/evolution/)
- **Lifecycle Governance** - Gated releases, contract testing, deployment verification
- **Open Standard** - AGENTS.md enables ecosystem innovation

### Who It's For

- **Organizations** managing 5+ AI coding agents (version control, compliance)
- **Power Users** coordinating specialized agents (legal, healthcare, code analysis)
- **Development Teams** adopting AI agents with governance requirements

---

## Why AGET?

### Mission-Driven

Enable your agents to succeed at making their principals successful at making the universe more beautiful.

Success cascades through four levels:
```
Universe More Beautiful  ← Fairer outcomes, better quality
    ↑
Principal Success        ← Lawyers, doctors, developers deliver better work
    ↑
Agent Success            ← Effective augmentation with deployment confidence
    ↑
Framework Quality        ← AGET ensures coordination, learning, governance
```

### Ecosystem Approach

AGET doesn't replace your CLI tools—it coordinates them. Works alongside Claude Code, Cursor, Aider, Windsurf to bring fleet-level capabilities: version control, shared learning, lifecycle governance.

**Complementary, not competitive**: AGET + CLI Tools work together to enable your agents.

### Open Innovation

**AGENTS.md** open standard means anyone can adopt, extend, or integrate. **Shared learning repository** means collective intelligence grows together. No vendor lock-in, no proprietary formats—just universal CLI compatibility and portable knowledge.

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

## Key Features

### Version Control

Track agent identity, manage upgrades, ensure compliance:
```yaml
# .aget/version.json
{
  "agent_name": "my-legal-assistant",
  "aget_version": "2.9.0",
  "instance_type": "AGET",
  "domain": "legal_contract_analysis"
}
```

Version progression: v2.5 → v2.6 → v2.7 → v2.8 → v2.9
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

## Documentation

- **[Getting Started Guide](docs/GETTING_STARTED.md)** - Create your first agent
- **[AGENTS.md Specification](docs/AGENTS_MD_SPEC.md)** - Universal configuration format
- **[Migration Guide](docs/MIGRATION_GUIDE.md)** - Upgrade between versions
- **[Template Comparison](docs/TEMPLATE_COMPARISON.md)** - Choose the right template
- **[Framework Vision](https://github.com/gmelli/private-supervisor-AGET/blob/main/.aget/specs/FRAMEWORK_VISION_v1.0.yaml)** - Mission, principles, positioning

---

## Architecture

### 5-Layer Knowledge Model

AGET uses a hierarchical knowledge architecture to separate concerns:

| Layer | Location | Purpose | Portability |
|-------|----------|---------|-------------|
| **Framework** | `.aget/` | Process knowledge, patterns | ✅ Portable (clone to new domain) |
| **Agent Type** | Template | Role-specific capabilities | ✅ Inherited at creation |
| **Instance** | `.aget/version.json` | Agent identity, configuration | Per-agent |
| **Memory** | `.memory/` | Engagement state (advisors only) | Relationship-specific |
| **Domain** | Root `sessions/`, `knowledge/` | Principal's work product | Principal-owned |

**Principle**: Framework knowledge (how to work) stays in `.aget/`. Domain knowledge (what you know) stays at root.

### Fleet Coordination

```
┌─────────────────────────────────────────────────────────┐
│ MISSION: Make Universe Beautiful                        │
│          (through principal success)                    │
└─────────────────────────────────────────────────────────┘
                        ↑
┌─────────────────────────────────────────────────────────┐
│ AI CODING AGENTS                                        │
│ (Workers, Advisors, Supervisors, Consultants)           │
└─────────────────────────────────────────────────────────┘
                ↑               ↑
        ┌───────────┐   ┌──────────────┐
        │   AGET    │   │  CLI TOOLS   │
        │ (Coords)  │←→│ Claude Code  │
        │           │   │ Cursor       │
        │ Version   │   │ Aider        │
        │ Learning  │   │ Windsurf     │
        │ Lifecycle │   │              │
        └───────────┘   └──────────────┘
              ↑                 ↑
        Open Standard     Universal CLI
        (AGENTS.md)       Compatibility
```

AGET + CLI Tools = **Complementary** (not competitive)

---

## Use Cases

### Legal Practice

**Principal**: Lawyer handling contract review
**Agents**: 5 specialized (analysis, research, drafting, compliance, case management)
**Outcome**: 3x caseload with maintained quality (10x faster contract analysis)
**Universe Beautiful**: More accessible legal representation

### Healthcare

**Principal**: Doctor diagnosing complex cases
**Agents**: 3 specialized (records pre-processing, literature research, diagnosis suggestions)
**Outcome**: More patients seen, better diagnoses (pattern recognition from literature)
**Universe Beautiful**: Improved patient care quality

### Software Development

**Principal**: Development team shipping code
**Agents**: 8 specialized (code review, testing, documentation, standards, debugging)
**Outcome**: Higher code quality, fewer bugs, better architecture
**Universe Beautiful**: More reliable software

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

### v2.9 (Current) - Information Storage Standardization
- ✅ Session location standard (`sessions/` at root)
- ✅ Session metadata standard (YAML frontmatter)
- ✅ Memory layer for advisors (`.memory/` structure)
- ✅ 5-layer knowledge architecture
- ✅ Fleet-wide migration complete (28 agents)

### v2.10 (Next) - Public Documentation & Ecosystem Growth
- 📋 Expand template documentation (examples, migration guides)
- 📋 Public migration resources (v2.8 → v2.9 → v2.10 path)
- 📋 Enhanced .memory/ examples for advisor templates
- 📋 Template selector guide (choose right template for use case)

### v3.0 (Future) - Multi-Agent Coordination
- 🔮 Agent discovery and routing
- 🔮 Task queue and delegation
- 🔮 Cross-agent collaboration patterns
- 🔮 Fleet-level analytics and metrics

---

## Community

- **GitHub Issues**: [File bugs, request features](https://github.com/gmelli/aget-aget/issues)
- **Discussions**: [Ask questions, share patterns](https://github.com/orgs/aget-framework/discussions)
- **Contributing**: [Contribution guidelines](CONTRIBUTING.md)

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

**AGET Framework** - Enable your AI agents to make the universe more beautiful

*Fleet coordination for the CLI coding tools you already use*
