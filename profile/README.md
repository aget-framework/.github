# AGET Framework

**Configuration & Lifecycle Management System for CLI-Based Human-AI Collaborative Coding**

AGET enables organizations to manage fleets of specialized AI coding agents with version control, shared learning, and lifecycle governance—without infrastructure overhead.

---

## What is AGET?

AGET occupies a unique niche in the agent framework landscape:

- **Not** an autonomous agent runtime (LangChain, MetaGPT, AutoGPT)
- **Not** a production ALM platform (AgentOps, Salesforce ALM)
- **Instead**: Human-supervised fleet management with organizational memory and version progression

### Differentiators

✅ **Universal CLI Compatibility** - Works across Claude Code, Cursor, Aider, Windsurf
✅ **Contract Testing** - Version compliance validation (v2.7.0)
✅ **Shared Learning Repository** - `.aget/evolution/` for organizational memory
✅ **Lightweight** - Zero-infrastructure (markdown + git)
✅ **Human-Centric Governance** - Gated releases, evidence-based planning

---

## Templates

Choose the template that matches your agent's role:

| Template | Use Case | Capability | Status |
|----------|----------|------------|--------|
| **[template-worker-aget](https://github.com/aget-framework/template-worker-aget)** | General-purpose tasks | Flexible (AGET or aget) | ✅ Public |
| **[template-advisor-aget](https://github.com/aget-framework/template-advisor-aget)** | Advisory with internal state | Persona-based guidance | ✅ Public |
| **[template-supervisor-aget](https://github.com/aget-framework/template-supervisor-aget)** | Fleet coordination | Multi-agent orchestration | 🔒 Private (v2.7) |

**Naming Convention**:
- `-AGET` suffix = Action-taking agent (can modify systems)
- `-aget` suffix = Information-only agent (read-only)

**Examples**:
```
my-github-AGET              # Action-taking: Creates PRs, merges code
my-spotify-analyst-aget     # Information-only: Reports analytics
my-supervisor-AGET          # Coordinator: Manages agent fleet
```

The suffix convention provides visual capability signaling—like `sudo` or `rm -rf`, the capitalized AGET warns of powerful operations.

---

## Quick Start (5 Steps)

### 1. Choose Your Template

Use the **template decision tree**:

```
Need to manage multiple agents? → template-supervisor-aget
Need advisory role with personas? → template-advisor-aget
General-purpose agent? → template-worker-aget
```

See [Getting Started Guide](./GETTING_STARTED.md) for detailed decision tree.

### 2. Clone Template

```bash
# Worker example
gh repo clone aget-framework/template-worker-aget my-custom-aget
cd my-custom-aget
```

### 3. Update Identity

Edit `.aget/version.json`:
```json
{
  "aget_version": "2.7.0",
  "agent_name": "my-custom-aget",
  "instance_type": "AGET",
  "domain": "your-domain"
}
```

**Important**: Verify `CLAUDE.md` symlink after cloning:
```bash
ls -lh CLAUDE.md  # Should show: lrwxr-xr-x ... -> AGENTS.md
readlink CLAUDE.md  # Should return: AGENTS.md

# If not symlink, fix it:
rm CLAUDE.md && ln -s AGENTS.md CLAUDE.md
```

### 4. Run Contract Tests

```bash
python3 -m pytest tests/ -v
```

All agents must pass contract tests before first commit.

### 5. First Session

```bash
# Wake up your agent
# In Claude Code or your preferred CLI tool:
wake up

# Start working
# ... collaborate on tasks ...

# Save session
wind down
```

---

## Documentation

### Framework Guides
- **[Getting Started](./GETTING_STARTED.md)** - Create your first agent (step-by-step)
- **[Design Philosophy](./DESIGN_PHILOSOPHY.md)** - Human-supervised collaboration principles
- **[Core Patterns](./CORE_PATTERNS.md)** - Gate discipline, recursive supervision, file-based coordination

### Specifications
- **[SPEC_FORMAT_v1.1.md](https://github.com/aget-framework/template-worker-aget/blob/main/.aget/docs/SPEC_FORMAT_v1.1.md)** - EARS patterns and controlled vocabulary
- **[LEARNING_DOCUMENT_SPEC_v1.0](https://github.com/aget-framework/template-worker-aget/blob/main/.aget/specs/LEARNING_DOCUMENT_SPEC_v1.0.yaml)** - Organizational memory structure

### Resources
- **Learning System** - `.aget/evolution/` contains L-numbered pattern discoveries
- **Migration Guides** - Version progression protocols in individual repositories
- **Issue Templates** - Severity-based routing and SLA expectations

---

## Framework Philosophy

**Human-Supervised Collaboration**: AGET keeps humans in control with GO/NOGO gates for substantial changes.

**Configuration Over Code**: Agents configured via `AGENTS.md` markdown files, not custom runtimes.

**Evidence-Based Evolution**: Organizational memory system (`.aget/evolution/`) captures "why" decisions were made.

**Universal CLI Compatibility**: Works across competing platforms—no vendor lock-in.

See [Design Philosophy](./DESIGN_PHILOSOPHY.md) for complete principles.

---

## Version Compliance

**Current Version**: v2.7.0 "Portfolio Governance"

**New Agent Policy**: All new agents must be created at **v2.7.0 or higher**.

**v2.7.0 Baseline**:
- Portfolio governance (CCB/LEGALON/Main classification)
- Multi-tier issue routing (Tier 1/2/3)
- Learning discovery system (133 learnings indexed)
- Security hooks (pre-commit checks for private leaks)
- HTML specification generation (YAML → styled HTML)

**Migration Protocols**: Each version includes migration guides for existing agents.

---

## Who Should Use AGET?

### ✅ Good Fit

- **Organizations managing 5+ specialized coding agents**
- **Teams needing version control for agent capabilities**
- **Projects requiring organizational memory across agents**
- **Users wanting universal CLI compatibility (not vendor-locked)**
- **Teams with human supervisors coordinating agent work**

### ❌ Not a Fit

- **Single autonomous agent deployments** (use LangChain/MetaGPT)
- **Production runtime monitoring** (use AgentOps/Salesforce ALM)
- **Agent-to-agent autonomous coordination** (use CrewAI/LangGraph)
- **Single-project configuration** (use AGENTS.md without AGET framework)

---

## Positioning in Framework Landscape

AGET solves the problem:

> "How do organizations manage dozens of specialized AI coding assistants with version control, shared learning, and lifecycle governance?"

**No existing framework addresses this exact space**—most assume either:
- Single autonomous agent (ALM systems)
- Agent-to-agent autonomous coordination (meta-frameworks)
- Single-project configuration (CLI tools)

**AGET's sweet spot**: Human-supervised fleets of specialized CLI agents with organizational memory and version progression.

See [L143: Framework Landscape Positioning](https://github.com/aget-framework/template-worker-aget/blob/main/.aget/evolution/L143_aget_framework_landscape_positioning.md) for complete analysis.

---

## Contributing

Framework is in active development (v2.7.0). Contribution guidelines coming in v2.8+.

**Current Focus**:
- Template refinement (worker, advisor, supervisor)
- Documentation expansion
- Fleet migration patterns
- Security and privacy enhancements

**Feedback Welcome**: File issues in relevant repositories with appropriate labels.

---

## License

Apache 2.0 (individual repositories may vary - check each repo)

---

## Support

- **Issues**: File in relevant repository (template-specific or aget-framework/.github)
- **Discussions**: GitHub Discussions (coming soon)
- **Security**: See [SECURITY.md](./SECURITY.md) for responsible disclosure

---

*AGET Framework v2.7.0 - Configuration & Lifecycle Management for Human-AI Collaborative Coding*
