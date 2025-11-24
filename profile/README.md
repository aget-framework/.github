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
✅ **Contract Testing** - Version compliance validation (v2.8.0)
✅ **Shared Learning Repository** - `.aget/evolution/` for organizational memory
✅ **Lightweight** - Zero-infrastructure (markdown + git)
✅ **Human-Centric Governance** - Gated releases, evidence-based planning

---

## Templates

**AGET templates provide configuration and lifecycle management for CLI-based coding agents.**

### Core Templates (Fleet Roles)

Choose a core template based on your agent's role in the fleet:

**All core templates build on the worker foundation.** Advisor, consultant, and supervisor add specialized capabilities.

| Template | Foundation | Additional Capabilities | Status |
|----------|------------|------------------------|--------|
| **[template-worker-aget](https://github.com/aget-framework/template-worker-aget)** | ✅ **CORE** | General-purpose (flexible capability) | ✅ Public v2.9.0 |
| **[template-advisor-aget](https://github.com/aget-framework/template-advisor-aget)** | Worker + | Persona system, advisory-only mode | ✅ Public v2.9.0 |
| **[template-consultant-aget](https://github.com/aget-framework/template-consultant-aget)** | Worker + | Solutions-focused proactive advisory | ✅ Public v2.9.0 |
| **[template-supervisor-aget](https://github.com/aget-framework/template-supervisor-aget)** | Worker + | Fleet coordination, process enforcement | ✅ Public v2.9.0 |

**Need help choosing?** See **[Template Selector](./TEMPLATE_SELECTOR.md)** for decision tree and detailed comparison.

### Specialized Templates (Task-Specific)

Choose a specialized template for specific technical tasks:

| Template | Purpose | Methodology | Status |
|----------|---------|-------------|--------|
| **[template-spec-engineer-aget](https://github.com/aget-framework/template-spec-engineer-aget)** | Reverse engineer Python code into formal EARS specifications | Semantic extraction via coding agent (functions → scripts → modules → applications) | ✅ Public v2.9.0 |
| **[template-developer-aget](https://github.com/aget-framework/template-developer-aget)** | Code quality analysis and standards compliance advisor | Multi-repository code analysis (quality metrics, standards checking, debugging assistance, spec consistency) | ✅ Public v2.9.0 |
| **[template-document-processor-AGET](https://github.com/aget-framework/template-document-processor-AGET)** | Create document processing agents with LLM pipelines and security protocols | Multi-provider LLM support, validation pipelines, security protocols, caching, and observability | ✅ Public v2.9.0 |

**Specification Engineering Use Cases**:
- **Extract** specifications from existing Python code (AGET tools, scripts, modules, applications)
- **Maintain** specifications as primary artifacts (ongoing evolution)
- **Document** legacy code with formal requirements

**Quality benchmarks**: 75-85% for scripts (100-500 lines), 60-70% for full applications (2000+ lines)

**Progression path**: Start with functions (validate methodology), scale to scripts (primary focus), then modules and applications

**Code Analysis Use Cases**:
- **Assess** code quality across repositories (complexity, maintainability, technical debt)
- **Verify** coding standards compliance (PEP-8, custom standards)
- **Assist** with debugging (error pattern recognition, fix strategies)
- **Validate** spec-to-code consistency (YAML/Markdown specifications)

**Quality benchmarks**: 9.2/10 average pattern quality across 5 real-world validation tasks

**Validation status**: Production-ready with 21 contract tests passing, critical bug fixed during validation

**Document Processing Use Cases**:
- **Build** document processing agents with LLM assistance (OpenAI, Anthropic, Google)
- **Implement** batch operations with validation pipelines and approval gates
- **Enforce** security protocols (prompt injection prevention, content filtering)
- **Optimize** performance with caching, metrics, and task decomposition

**Quality benchmarks**: 30/30 contract tests passing, Apache 2.0 licensed, privacy-safe

**Time savings**: 60-70% reduction in new agent setup (3-5 hours → 1-2 hours)

---

## Naming Convention

**Capability Suffix** (case-sensitive):
- `-AGET` suffix = Action-taking agent (can modify systems)
- `-aget` suffix = Information-only agent (read-only)

**Visibility Prefix**:
- `private-*` prefix = Personal deployment (not for sharing)

The suffix convention provides visual capability signaling—like `sudo` or `rm -rf`, the capitalized AGET warns of powerful operations.

### Examples by Template

| Template | Generic Example | Personal Deployment |
|----------|----------------|---------------------|
| **template-worker-aget** | `github-automation-AGET` | `private-github-AGET` |
| | `analytics-reporter-aget` | `private-analytics-aget` |
| **template-advisor-aget** | `code-review-advisor-aget` | `private-code-advisor-aget` |
| **template-consultant-aget** | `architecture-consultant-aget` | `private-consultant-aget` |
| **template-supervisor-aget** | `fleet-supervisor-AGET` | `private-supervisor-AGET` |
| **template-spec-engineer-aget** | `spec-engineer-aget` | `private-spec-engineer-aget` |
| **template-developer-aget** | `code-analyzer-aget` | `private-code-analyzer-aget` |
| **template-document-processor-AGET** | `pdf-processor-AGET` | `private-doc-processor-AGET` |
| | `invoice-extractor-AGET` | `private-invoice-AGET` |

**Notes**:
- Worker agents can be either `-AGET` (action-taking) or `-aget` (information-only)
- Advisor and consultant agents are always `-aget` (advisory-only, no external modifications)
- Supervisor agents are always `-AGET` (fleet coordination requires action-taking)
- Specialized templates have fixed capability based on their purpose

---

## Quick Start (5 Steps)

### 1. Choose Your Template

**All templates build on worker foundation.** Use the **template decision tree**:

```
Need fleet coordination? → template-supervisor-aget (worker + fleet)
Need consultant advisory? → template-consultant-aget (worker + consultant patterns)
Need advisory persona? → template-advisor-aget (worker + persona)
General-purpose? → template-worker-aget (core foundation)
```

See **[Template Selector](./TEMPLATE_SELECTOR.md)** for detailed decision tree, capability matrix, and upgrade paths.

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
  "aget_version": "2.8.0",
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
- **[Template Selector](./TEMPLATE_SELECTOR.md)** - Choose the right template (decision tree, comparison matrix)
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

**Current Version**: v2.9.0 "Information Storage Standardization"

**New Agent Policy**: All new agents must be created at **v2.9.0 or higher**.

**v2.9.0 Baseline**:
- 5-layer architecture (Framework, Agent Type, Instance, Memory, Domain)
- Session Metadata Standard v1.0 (formal session documentation)
- Information storage standardization (sessions/, knowledge/, workspace/, .memory/)
- 6 production migration tools (100% success rate across 28-agent fleet)
- Comprehensive documentation (175KB: migration guides, specs, tools reference)
- Backward compatible with v2.8 (non-breaking architecture extension)

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

Framework is in active development (v2.8.0). Contribution guidelines coming in v2.9+.

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

*AGET Framework v2.9.0 - Configuration & Lifecycle Management for Human-AI Collaborative Coding*
