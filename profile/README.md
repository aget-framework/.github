# AGET Framework

**Persistent Domain Intelligence for the CLI Coding Tools You Already Use**

Build AI agents that accumulate domain expertise serving your decisions. AGET provides session continuity, shared memory architecture, and governance patterns across Claude Code, Codex CLI, Gemini CLI—through an open standard. Zero infrastructure required.

**Solve**: Lost context between sessions, knowledge that resets daily, agents that can't learn from each other, deployment confidence across your fleet.

[![Version](https://img.shields.io/badge/version-3.17.0-blue)](https://github.com/aget-framework/aget/releases/tag/v3.17.0)
[![License](https://img.shields.io/badge/license-Apache%202.0-blue)](LICENSE)
[![Release Date](https://img.shields.io/badge/released-2026--05--09-lightgrey)](https://github.com/aget-framework/aget/releases/latest)

---

## What is AGET?

AGET enables AI agents that build persistent domain knowledge serving human decisions—with session continuity, shared learning, and governed autonomy across CLI tools. Think of it as the knowledge layer for your AI team.

### How It Works

- **Persistent Domain Knowledge** - Agents accumulate expertise that compounds across sessions
- **Session Continuity** - Pick up where you left off with structured memory architecture
- **Shared Learning** - Propagate insights across your fleet (`.aget/evolution/`)
- **Lifecycle Governance** - Gated releases, contract testing, deployment verification
- **Requirements-Driven** - Human-level requirements ground testable specifications
- **Universal CLI Compatibility** - Works with Claude Code, Codex CLI, Gemini CLI
- **Open Standard** - AGENTS.md enables ecosystem innovation
- **Hook-Ready** - Platform-native lifecycle automation via .claude/hooks/

### Specification-First Development

AGET brings formal requirements engineering to agent fleet management.
Requirements define principal intent; specifications define testable contracts (two-level model).

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

### 1. Get Your Supervisor

```bash
# Clone the supervisor template
git clone https://github.com/aget-framework/template-supervisor-aget my-supervisor
cd my-supervisor
```

### 2. Open in Your CLI Tool

Open the `my-supervisor/` directory in **Claude Code**, **Codex CLI**, or **Gemini CLI**. Then tell your agent:

```
wake up
```

Your supervisor initializes — it knows its identity, loads its knowledge base, and is ready to work. No configuration needed.

### 3. Create Your First Agent

Ask your supervisor to create the agent you need most:

```
/aget-create-aget developer my-dev-agent
```

The supervisor handles everything: picks the right template, configures identity, deploys skills. You now have a two-agent fleet — a supervisor and a developer.

### 4. Grow Your Fleet

Add more agents as needs emerge. **13 archetypes** available — each with specialized skills and formal ontology:

| Template | Primary Use Case |
|----------|------------------|
| [supervisor](https://github.com/aget-framework/template-supervisor-aget) | Fleet coordination (**you started here**) |
| [developer](https://github.com/aget-framework/template-developer-aget) | Code development |
| [analyst](https://github.com/aget-framework/template-analyst-aget) | Data analysis |
| [researcher](https://github.com/aget-framework/template-researcher-aget) | Research workflows |
| [architect](https://github.com/aget-framework/template-architect-aget) | System design |
| [advisor](https://github.com/aget-framework/template-advisor-aget) | Persona-based guidance |
| [consultant](https://github.com/aget-framework/template-consultant-aget) | Strategic engagements |
| [operator](https://github.com/aget-framework/template-operator-aget) | Operations/DevOps |
| [reviewer](https://github.com/aget-framework/template-reviewer-aget) | Quality review |
| [spec-engineer](https://github.com/aget-framework/template-spec-engineer-aget) | Requirements engineering |
| [executive](https://github.com/aget-framework/template-executive-aget) | Executive advisory |
| [worker](https://github.com/aget-framework/template-worker-aget) | General task execution |
| [document-processor](https://github.com/aget-framework/template-document-processor-AGET) | Document pipelines |

All templates include 31 universal skills (session management, health checks, knowledge capture, governance, release quality triad, and more) plus archetype-specific skills.

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
  "aget_version": "3.17.0",
  "instance_type": "AGET",
  "template": "researcher",
  "migration_history": [
    "v2.9.0 -> v2.10.0: 2025-12-13",
    "v2.10.0 -> v2.11.0: 2025-12-24",
    "v2.11.0 -> v2.12.0: 2025-12-25",
    "v2.12.0 -> v3.0.0: 2025-12-28",
    "v3.0.0 -> v3.1.0: 2026-01-04",
    "v3.5.0 -> v3.6.0: 2026-02-21",
    "v3.6.0 -> v3.7.0: 2026-03-02",
    "v3.7.0 -> v3.8.0: 2026-03-08",
    "v3.8.0 -> v3.9.0: 2026-03-15",
    "v3.9.0 -> v3.10.0: 2026-03-21",
    "v3.10.0 -> v3.11.0: 2026-03-28",
    "v3.11.0 -> v3.11.1: 2026-04-04",
    "v3.14.1 -> v3.15.0: 2026-04-25",
    "v3.15.0 -> v3.16.0: 2026-05-02",
    "v3.16.0 -> v3.17.0: 2026-05-09"
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
  "aget_version": "3.17.0",
  "instance_type": "AGET",
  "template": "researcher",
  "domain": "market_analysis"
}
```

Version progression: v2.5 → v2.6 → v2.7 → v2.8 → v2.9 → v2.10 → v2.11 → v2.12 → v3.0.0 → v3.1.0 → v3.2.0 → v3.2.1 → v3.3.0 → v3.4.0 → v3.5.0 → v3.6.0 → v3.7.0 → v3.8.0 → v3.9.0 → v3.10.0 → v3.11.0 → v3.11.1 → v3.12.0 → v3.13.0 → v3.14.0 → v3.14.1 → v3.15.0 → v3.16.0 → **v3.17.0**
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

### v3.17.0 (Current) - Theme C3: Canonical Coherence + Structural Self-Conformance

**Released**: 2026-05-09

- ✅ **`framework-manager` agent archetype** (T1.7, Q4=A.2): Coined to close the self-classification gap for agents whose role is canonically managing the framework's public repos. 6-site multi-site equality propagation (`identity.json` + `version.json` + `CHARTER` + `SCOPE_BOUNDARIES` + `AGENTS.md` + ontology C610 FrameworkManagerArchetype). Theoretical basis: Stewardship Theory of Management (Davis, Schoorman & Donaldson 1997).
- ✅ **CAP-REL-030 + CAP-REL-031 IMPLEMENTED** (T1.1 + T1.2): Closes v3.16 sleeping CAPs (Post-Release CHANGELOG Validator + Post-Release Tag Validator). Empirical run against v3.16.0 reference: 14/14 PASS. CAP-REL-032 + CAP-REL-033 grace-extended to v3.18.0 (Q1=B; R-DEP-011 rationale in `governance/POLICY_deprecation.md` Active Grace Extensions).
- ✅ **Sibling-quadruple spec authoring** (Tier 2, calibrated rigor): T2.18 `SOP_scope_lock_ceremony.md` v1.0.0 LANDED (codifies the very 4-gate ceremony executed at v3.16+v3.17 lock events — Theme C3 self-conformance demonstrated structurally); T2.19 `AGET_SKILL_LIFECYCLE_SPEC` v1.0.0 LANDED with full V-test authoring (Q-G1.5-2=B principal Decide rejected v3.16 SPEC-LANDED-IMPL-DEFERRED precedent — NO sleeping CAPs at V-test layer); T2.20 `AGET_FLEET_UPGRADE_SPEC` v0.1.0 DRAFT (calibrated demote per L103); T2.23 `AGET_TASK_ROUTING_SPEC` v0.1.0 DRAFT (calibrated demote).
- ✅ **`scripts/health_check.py` substance-aware evolution check** (T1.8, gh#1211): Closes L656 check-by-shape vs check-by-substance gap. Thresholds: WARN at non_ldoc_count > 2× l_doc_count; CRITICAL at non_ldoc_count > 10× l_doc_count OR byte_size > 100 MB.
- ✅ **`SOP_release_process.md` v1.32 → v1.45** (T1.5 + T1.6): H-RHSC-001 G3+G4 SOP wiring; V-G7.x broadened from presence-style to multi-condition correctness; explicit RELEASE_REPOS array (closes case-sensitive bash glob silently skipping `template-document-processor-AGET`).
- ✅ **V-test scope-of-validation as second axis of correctness** (Theme C3 empirical ratification): v3.16's #1 lesson (correctness-not-presence) extended with a second axis — declared scope of a V-test must equal the actual canonical-artifact universe. Three in-cycle V-test recurrences (T1.7, G2, G4) plus two post-publication recurrences (org-profile, AGET_DELTA chronic-17) ratify the pattern.

### v3.16.0 - Framework-Discipline Cluster Closure + Wave-1A Spec Contracts + /aget-go Production

**Released**: 2026-05-02

- ✅ **`/aget-go` (SKILL-048 v1.0.0)**: Healthy Friction primitive promoted to production — the framework's first explicit middle ground between Advisory (no friction) and Strict (hard block). Mandatory verification of the principle triad (spec+verify-first, coherence-next, evidence-driven). Authorization-only by design — does not execute the authorized work, preserving Two-Level Model separation (L742).
- ✅ **Wave-1A post-release spec contracts** (CAP-REL-030/031/032/033): Post-Release CHANGELOG / Tag / Badge-Parity / Contract-Test validators specified. Shipped as **SPEC-LANDED; IMPLEMENTATION DEFERRED v3.17** with R-DEP-010 grace-period annotation per ADR-007 (No Test Theater) — honest spec-truthfulness over aspirational "LANDED."
- ✅ **Knowledge-tier isolation skeleton** (CAP-SEC-007): Four-tier trust model contract (T0 confidential / T1 internal / T2 shared / T3 external) and `.agetignore` skeleton at canonical `aget/` root. Theoretical basis: Least Privilege, Bell-LaPadula, Mandatory Access Control. Hook implementation deferred v3.17.
- ✅ **Framework-discipline cluster closure** (L908+L909+L910+L912+L913+L914+L916): Seven-member cluster representing surfaces where narrative-discipline outpaced structural-discipline. Each member made detectable and structurally fixed (or carrying explicit v3.17 commitment).
- ✅ **Universal-skill mandate recalibration** (CAP-TPL-016-04): 32 → 29 universal skills. Three release-triad skills graduated from universal baseline to release-execution archetype catalog (CAP-TPL-016-07).

### v3.15.0 - Two-Level Model Coherence + Security Hardening + Weekly Cadence Formalization

**Released**: 2026-04-25

- ✅ **`/aget-enhance-health` (SKILL-049 v1.0.0)**: 7-phase health remediation — canonical `check → enhance` pipeline. Deployed to all 13 templates.
- ✅ **AGET_SECURITY_SPEC v0.2**: First dedicated security spec — 8 CAP-SEC contracts (boundary enforcement, input validation, information disclosure, dependency integrity, authority overstep, scope creep, output contamination, autonomous action bounds).
- ✅ **AGET_BUDGET_GRAMMAR_SPEC v0.2**: Budget grammar formalized — 4 CAP-BGG contracts.
- ✅ **CAP-REL-029**: Pre-release gate checklist as testable EARS requirement.
- ✅ **POL-REL-001**: Weekly Saturday release policy formalized from 6-release empirical record (v3.10–v3.15).
- ✅ **ADR-022**: Breaking-change policy ratified — codifies Q3=(b) interpretation.
- ✅ **`verification/validate_archetype_skills.py`**: Promoted to canonical `aget/verification/` — mechanically enforces universal-skill mandate (CAP-TPL-016-04).
- ⚠️ **Breaking: BC-001** — v3.14 dual-read shim removed; code reading `aget_`-prefixed field names from `version.json` (which don't exist) now breaks. See [BREAKING_CHANGES_v3.15.md](https://github.com/aget-framework/aget/blob/main/docs/BREAKING_CHANGES_v3.15.md).
- ⚠️ **Breaking: BC-002** — `--fix` flag removed from skill surfaces. Replacement: `/aget-enhance-health`.

### v3.14.1 - #979 Installer Partial-Propagation Hotfix

**Released**: 2026-04-18

- ✅ **Surgical 4-repo bump**: aget/ core + advisor/developer/spec-engineer templates. `installer/install.py` now references `scripts/health_check.py` (was stale `housekeeping_protocol.py` from partial #979 propagation in v3.11.1). Restores CI green on the 3 affected templates. Other 10 templates remain at v3.14.0.
- ✅ **No breaking changes. No new deprecations.**

### v3.14.0 - v3.13 Loop Closure + Scope-Lock Discipline

**Released**: 2026-04-18

- ✅ **CAP-REL-028 Upstream Deployment Feedback spec** (REQ-REL-F-009): Formalizes the feedback channel from fleet agents back to framework when deployment reveals gaps (L827). Closes the deployment→framework feedback loop.
- ✅ **DEPLOYMENT_SPEC_v3.13.0.yaml + v3.14.1.yaml**: Template baselines + reconciliation steps for fleet upgrade. Pairs with SOP Phase 2.5 deployment artifact sync.
- ✅ **Skill Telemetry Logger** (`log_skill_invocation.py`): Structured JSONL entries when skills are invoked — substrate for principal-facing skill-usage analytics.
- ✅ **Single-Verb Exception Registry** (CAP-SNAME-001-06): Permits `aget-{verb}` form for approved single-verb skills (`aget-ask`, `aget-name`).
- ✅ **AGET_TEMPLATE_SPEC** universal skills 15 → 31; supervisor skills 18 → 37.
- ✅ **Session Script Deprecations**: 4 session scripts deprecated per POL-DEP-001 (2 minor-version grace per R-DEP-011); removal v3.16.0.

### v3.13.0 - Operational Maturation & Fleet Automation

**Released**: 2026-04-12

- ✅ **Release Gate Validator**: `validate_release_gate.py` — structural exit-code enforcement across 7 validators (L784 fix)
- ✅ **Fleet Upgrade Script**: `fleet_upgrade.py` — single-script migration reduces 25-40 prompts to ≤5
- ✅ **Release Delivery Triad**: Builder/Spec Auditor/Critic perspectives v0.2.0 — three-perspective quality at every gate
- ✅ **8 New Skills** (24→31): promote-issue, describe-session, propose-actions, create-rubric, check-initiative, process-observation, open-session, check-facts
- ✅ **Skill Telemetry**: Mandatory Requirements section + invocation logging infrastructure
- ✅ **Health Check Orchestration**: 3-tier spec (Quick/Standard/Full) resolving L787 divergence
- ✅ **Governed Discourse Boundary**: Formal/informal artifact classification + high-impact term remediation

### v3.12.0 - Developer Surface & Governance Maturation
**Released**: 2026-04-04

- ✅ Issue Governance v2.1.0, Homepage Rewrite, Epistemic Parameterization
- ✅ First Deprecation Cycle, Release State Management

### v3.11.1 - Script Rename Stabilization
**Released**: 2026-04-04

- Renamed `aget_housekeeping_protocol.py` → `health_check.py`
- Renamed `study_up.py` → `study_topic.py`
- New: `tag_release.py`

### v3.11.0 - Skill Conformance, Requirements & Hooks
**Released**: 2026-03-28

- ✅ **Requirements Layer**: Human-level requirements directory (`requirements/`) with REQUIREMENTS_FORMAT.md and REQ-REL exemplar — first formal requirements artifact per L742 two-level model
- ✅ **Hook Adoption**: `.claude/hooks/` scaffolded across all 12 templates with HOOK_ADOPTION_GUIDE — ADR-008 Generator level infrastructure
- ✅ **Skill Conformance**: 17 skill instructions remediated for L736 conformance — assert-before-verify anti-pattern eliminated
- ✅ **Archetype Governance**: `governance_intensity` field in all 12 template AGENTS.md (Rigorous/Standard/Lightweight)
- ✅ **Release Quality**: Pre-push hook, study_up.py fix, "sanity→health" terminology, homepage roadmap, phantom cleanup
- ✅ **Requirements-Spec Traceability**: AGET_RELEASE_SPEC v1.11.0 — first bidirectional requirements ↔ spec grounding

### v3.10.0 - Structural Enforcement
**Released**: 2026-03-21

- ✅ **3-Layer Structural Enforcement**: MUST-invoke directives for `/aget-create-project` and `/aget-file-issue`; gate completion requires plan update + commit; skill completion signals
- ✅ **Dual-Repo Sync Governance**: SOP Phase -0.5 governs private→public content sync with validators and SYNC_MANIFEST tracking
- ✅ **Skill Naming Reconciliation**: 3 renames across 14 repos — `capture` verb retired from Learning family, unified under `record` + `study`
- ✅ **SKILL_SPEC_TEMPLATE.yaml**: Deployed to all 12 templates
- ✅ **Template Hygiene**: VERSION, setup.py classifier, SECURITY.md updates

### Earlier Releases (v2.10.0 – v3.9.0)

Inline release entries for v2.10.0 through v3.9.0 have been relocated to keep this homepage focused on the most-recent cycle (Fork C Hybrid, 2026-05-16). Full history remains canonically available:

- 📦 **Per-version Release pages**: [github.com/aget-framework/aget/releases](https://github.com/aget-framework/aget/releases) — canonical body per version
- 📂 **Consolidated archive**: [`release-notes/archive/HOMEPAGE_INLINE_RELEASES_v2.10_to_v3.9.md`](https://github.com/aget-framework/aget/blob/main/release-notes/archive/HOMEPAGE_INLINE_RELEASES_v2.10_to_v3.9.md) — original inline format
- 📋 **Full changelog**: [CHANGELOG.md](https://github.com/aget-framework/aget/blob/main/CHANGELOG.md) — Keep-a-Changelog style

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

### Structural Aesthetics

- Beauty signals health; ugliness signals problems worth investigating
- Not all ugliness is failure — some is the cost of evolution
- Naming, structure, and ceremony should feel inevitable (not forced)
- Artifacts should invite engagement (not just pass validation)

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
