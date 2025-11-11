# AGET Core Patterns

**Proven patterns for effective human-AI collaborative coding**

This document describes the tactical patterns that make AGET agents effective collaborators. Each pattern emerged from real problems encountered during fleet management and has quantified impact metrics.

---

## Pattern Index

| Pattern | Problem Solved | Impact | Learning Ref |
|---------|----------------|--------|--------------|
| **[Gate Execution Discipline](#gate-execution-discipline-l042)** | Agents execute without approval | Process: 2/10 → 9/10 | L042 |
| **[Gate Sizing Heuristic](#gate-sizing-heuristic-l104)** | Over/under-planning gates | Right-sized gates | L104 |
| **[Evidence Before Implementation](#evidence-before-implementation-l084)** | Wasted work on unclear requirements | Hours saved | L084 |
| **[Recursive Supervision](#recursive-supervision-l099)** | Unclear supervision structure | Scalable hierarchy | L099 |
| **[Multi-Agent Process Enforcement](#multi-agent-process-enforcement-l099)** | Process violations by workers | Compliance 350% | L099 |
| **[File-Based Worker Coordination](#file-based-worker-coordination-l100)** | Ambiguous coordination | Explicit blocking | L100 |
| **[Learning Document Structure](#learning-document-structure-l051)** | Inconsistent learnings | Standardized format | L051 |

---

## Gate Execution Discipline (L042)

### Problem

Agents executing next gate without approval, leading to:
- "While we're at it, let's also..." scope creep
- User losing control of substantial changes
- Process violations (doing work not yet approved)

**Example**: Agent approved for Gate 3, immediately starts Gate 4 work without waiting for GO.

---

### Pattern

**Execute ONLY current gate deliverables**:
1. Execute approved gate's actions
2. Stop at gate boundary (don't continue)
3. Run validation checks
4. Present completion + decision point
5. **WAIT for explicit GO** before starting next gate
6. Don't assume continuation

**Critical**: "Let me proceed to Gate N+1" is asking permission, not assuming it.

---

### Implementation

**In AGENTS.md** (Substantial Change Protocol section):
```markdown
### Gate Execution Discipline (L42)
- Execute ONLY current gate deliverables (not next gate)
- Stop at gate boundary
- Run validation checks
- Present completion + decision point
- **WAIT for explicit GO** before starting next gate
- Don't assume continuation or optimize for speed over control
- Red flag: "While we're at it, let's also..." = likely next gate work
```

**In practice**:
```markdown
### Gate 3: Execution
✅ Gate 3 Complete
- File A updated (3 changes)
- File B created (42 lines)
- Tests passing (12/12)

**DECISION POINT**: Continue to Gate 4 (verification)?
[WAITING FOR USER RESPONSE]
```

---

### Anti-Patterns

❌ **"Execute Before Approval"**:
```
Agent: "I fixed the errors. Now executing Gate 4..."
[Proceeds without GO]
```

❌ **"Optimization Over Control"**:
```
Agent: "Since we're here, I'll also update related code..."
[Scope creep beyond current gate]
```

❌ **"Assumed Continuation"**:
```
Agent: "Gate 3 complete. Moving to Gate 4..."
[Doesn't wait for explicit approval]
```

---

### Success Criteria

✅ Agent stops at gate boundary
✅ Presents decision point explicitly
✅ Waits for user response before continuing
✅ No scope creep beyond current gate
✅ Process rating >8/10 (supervisor assessment)

---

### Impact

**Quantified**:
- Process violations: 2/10 → 9/10 rating (350% improvement)
- User control restored (GO/NOGO decisions effective)
- Reduced wasted work from misaligned execution

**Example**: Advisory critique after violation:
> "Advisory supervision only works if worker waits for GO before executing. Rating: 4/10 for process violation."

After correction:
> "Gate execution discipline followed correctly. Rating: 9/10 for compliance."

---

## Gate Sizing Heuristic (L104)

### Problem

Incorrect gate count for task complexity:
- **Over-gating**: 7 gates for internal-only work (more planning than execution)
- **Under-gating**: 2 gates for complex multi-agent migration (insufficient checkpoints)

**Example**: Internal documentation update with 7 gates spent more time on gates than writing.

---

### Pattern

**Match gate count to task complexity using decision framework**:

**Baseline**: 2-3 gates for any planned work

**Add gates based on risk factors**:
- **Reversibility**: Irreversible (+2), Partially reversible (+1), Fully reversible (+0)
- **Impact Scope**: System-wide/multi-agent (+2), External dependencies (+1), Internal-only (+0)
- **Complexity**: High (>10 files) (+2), Medium (5-10 files) (+1), Low (<5 files) (+0)

**Examples**:
- Internal docs: 2-3 gates (fully reversible, internal, low complexity)
- Feature work: 3-4 gates (reversible, single system, medium complexity)
- Architecture: 5-7 gates (partially reversible, external deps, high complexity)
- Fleet migration: 7-8 gates (partially reversible, multi-agent, high complexity)

---

### Implementation

**Decision Process**:
```markdown
Task: Update internal documentation

Risk Assessment:
- Reversibility: Fully reversible (git revert) → +0
- Impact Scope: Internal-only → +0
- Complexity: Low (<5 files) → +0

Gate Count: 2 + 0 = 2-3 gates ✅

Proposed Gates:
1. Analysis & Planning
2. Execution & Review
```

vs.

```markdown
Task: Multi-agent fleet migration

Risk Assessment:
- Reversibility: Partially reversible (some operations irreversible) → +1
- Impact Scope: Multi-agent (26 agents affected) → +2
- Complexity: High (>10 files per agent) → +2

Gate Count: 2 + 5 = 7-8 gates ✅

Proposed Gates:
1. Fleet Audit
2. Migration Plan
3. Batch 1 Migration
4. Repository Rename
5. Batch 2 Migration
6. Batch 3 Migration
7. Verification
```

---

### Anti-Patterns

❌ **Over-Gating** (Red Flags):
- "Internal-only but has 7 gates"
- Verification in middle (not start) of execution
- Gates that could combine (commit + push separate)
- More time planning than executing

❌ **Under-Gating** (Red Flags):
- "Fleet migration with 2 gates"
- No verification checkpoint
- Irreversible operations without pause
- High-risk changes without intermediate review

---

### Success Criteria

✅ Gate count proportional to risk
✅ Decision framework applied explicitly
✅ Red flags identified and addressed
✅ User can understand gate rationale
✅ Execution time >> planning time

---

### Impact

**Quantified**:
- Right-sized gates for 15+ multi-gate plans
- Reduced over-planning waste (7 gates → 3 gates for simple tasks)
- Ensured adequate checkpoints for high-risk work

**Pattern**: When in doubt, start with 3 gates (Analysis, Execution, Verification). Add gates only for specific risks you can name.

---

## Evidence Before Implementation (L084)

### Problem

Implementing features without confirming requirements, leading to:
- Wasted hours on wrong solution
- Over-engineering for unclear needs
- Misaligned deliverables

**Example**: Proposing 5 hours of demo features before confirming presentation format.

---

### Pattern

**Before committing to implementation work**:

1. **CONFIRM requirements** - Ask specific questions about actual needs
2. **EVALUATE scenarios** - Consider minimal viable implementation
3. **ESTIMATE work** - Calculate time for each scenario
4. **WAIT for clarity** - Don't assume requirements from vague requests

---

### Recognition Triggers

When you observe:
- Proposing multi-hour feature work
- User mentions "demo" or "presentation" without specifics
- Implementation assumptions made without evidence
- "Might need" or "could want" language in requirements

**STOP and ask**:
- What's the actual format? (Slides / Recorded / Live / Workshop)
- What are you demonstrating specifically?
- What proof is required? (Screenshots / Live execution / References)
- Who is the audience? (Technical / Executive / Public / Internal)

---

### Decision Framework

Present scenarios with time estimates:

```markdown
Scenario A (Minimal): X hours → [Specific deliverable]
Scenario B (Medium): Y hours → [Specific deliverable]
Scenario C (Maximum): Z hours → [Specific deliverable]

Which scenario fits actual requirements?
```

**Example** (Demo Preparation):
```markdown
Scenario A (Screenshots Only): 30 minutes
- Capture 5 key screenshots
- Add annotations
- Create slide deck

Scenario B (Recorded Demo): 2 hours
- Record screen capture
- Edit video
- Add narration

Scenario C (Live Interactive Demo): 5 hours
- Build demo environment
- Create sample data
- Prepare fallback scenarios
- Test edge cases

Which scenario fits Tuesday's demo format?
```

---

### Anti-Patterns

❌ **Assumption-Driven Implementation**:
```
User: "I have a demo Tuesday"
Agent: [Immediately plans 5-hour feature implementation]
```

✅ **Evidence-Driven Implementation**:
```
User: "I have a demo Tuesday"
Agent: "What format is the demo? What are you demonstrating specifically?"
[Waits for clarity before planning]
```

---

### Success Criteria

✅ Requirements confirmed before planning
✅ Multiple scenarios presented with estimates
✅ User chooses scenario explicitly
✅ Implementation matches actual needs
✅ No wasted work on misaligned features

---

### Impact

**Quantified**:
- Hours saved: Prevented 5-hour feature work when screenshots sufficient
- Alignment: Implementation matches actual requirements
- Strategic pause: Pause before implementation > premature building

**Pattern**: L082 (sufficient success) + L084 (diminishing returns) = Build only what's needed for requirements, avoid over-optimization without evidence.

---

## Recursive Supervision (L099)

### Problem

Unclear supervision structure as agent fleets grow. Questions arise:
- "Can supervisors be supervised?"
- "How do multi-level hierarchies work?"
- "Is 'supervisor' a different agent type?"

---

### Pattern

**Core Principle**: Every agent is a worker. Supervision is a capability, not a type.

**Recursive Structure**:
```
Human (supervises) → fleet-supervisor-AGET (supervises) → 10 worker agents
```

**Enables**:
- Multi-level hierarchies (supervisors of supervisors)
- Clear accountability chains (every agent knows its supervisor)
- Fractal growth patterns (same structure at every level)
- Dynamic reorganization (promote worker → supervisor via config)

---

### Implementation

**In version.json**:
```json
{
  "instance_type": "AGET",
  "domain": "supervision",
  "supervisor": "human-user-name",
  "direct_reports": [
    "github-automation-AGET",
    "deployment-automation-AGET",
    "analytics-reporter-aget"
  ]
}
```

**In AGENTS.md** (Supervisor section):
```markdown
## Direct Reports

This supervisor manages 10 agents:
- github-automation-AGET (action-taking)
- deployment-automation-AGET (action-taking)
- analytics-reporter-aget (information-only)
- [... 7 more agents ...]

Responsibilities:
- Assign work to appropriate agent
- Review agent outputs against specifications
- Enforce process standards (gate discipline)
- Escalate blockers to human supervisor
```

---

### Supervision Capabilities

**Process Enforcement**:
- Catch violations early (gate discipline, scope creep)
- Critique format: Quantitative rating (X/10) + specific violations + actionable path forward
- Example: "Process 2/10: No gate plan (violation), 914 lines without preview (violation)"

**Incremental Oversight**:
- Review at version completions, not just final output
- Provide go/no-go decisions at natural checkpoints
- Match review cadence to delivery cadence

**Intervention Timing**:
- **Intervene**: Process violations, scope creep, disproportionate time investment
- **Don't intervene**: Agent following approved gates, reasonable estimates

**Teaching Through Critique**:
- Specific violations with evidence
- Explain why it matters (impact, not just rules)
- Acknowledge improvement (2/10 → 9/10)

**Scope Management**:
- Help design experiments, estimate effort, recommend timing
- Not just approve/reject, but shape proposals into actionable plans

---

### Success Criteria

✅ Clear supervisor-worker relationships
✅ Every agent knows its supervisor
✅ Supervisor can be supervised (recursive)
✅ Promotion path (worker → supervisor)
✅ Same patterns apply at every level

---

### Impact

**Quantified**:
- Scalability: 10 agents → 100 agents → 1000 agents (fractal structure)
- Clarity: Accountability chains explicit
- Flexibility: Workers promoted to supervisors via config change

**Example**: fleet-supervisor-AGET coordinates 10 workers, itself supervised by human. If fleet grows to 50 agents, create 5 supervisors (10 agents each), supervised by meta-supervisor.

---

## Multi-Agent Process Enforcement (L099)

### Problem

Worker agents violating process standards (gate discipline, scope management) without correction, leading to:
- Wasted work
- User frustration
- Process degradation

---

### Pattern

**Supervisor applies practical patterns for enforcement**:

### 1. Process Enforcement

**Catch violations early**, enforce gate discipline:

**Critique Format**:
- Quantitative rating (X/10)
- Specific violations with evidence
- Actionable path forward

**Example Critique**:
```markdown
**Process Rating: 2/10**

Violations:
1. No gate plan presented (should have 3-5 gates)
2. 914 lines delivered without preview (substantial change protocol)
3. No decision point before execution

Required Corrections:
1. Create gate plan with clear boundaries
2. Present plan for approval before executing Gate 1
3. Stop at each gate for GO/NOGO decision

[If corrected → Rating: 9/10]
```

---

### 2. Incremental Oversight

**Match review cadence to delivery cadence**:
- Review at version completions, not just final output
- Provide go/no-go decisions at natural checkpoints

**Example**:
```
Worker: "Gate 3 complete. 5 files updated, tests passing."
Supervisor: "✅ Gate 3 approved. Proceed to Gate 4."
[Not: Wait until all 7 gates done, then review]
```

---

### 3. Intervention Timing

**Know when to stop vs when to let proceed**:

**Intervene When**:
- Process violations (gate discipline broken)
- Scope creep (beyond approved work)
- Disproportionate time investment (5 hours for unclear requirement)

**Don't Intervene When**:
- Agent following approved gates
- Reasonable estimates given
- On track with timeline

---

### 4. Teaching Through Critique

**Quality feedback drives behavior change**:

**Specific violations with evidence**:
```markdown
❌ Bad: "This doesn't follow our process"
✅ Good: "Missing gate plan (violation 1), executed without approval (violation 2)"
```

**Explain why it matters**:
```markdown
❌ Bad: "You violated L042"
✅ Good: "Gate discipline ensures user control. Without it, user loses ability to make GO/NOGO decisions (L042)."
```

**Acknowledge improvement**:
```markdown
After correction: "Process rating: 9/10. Gate discipline followed correctly. Significant improvement from initial 2/10."
```

---

### 5. Scope Management

**Help design experiments, estimate effort, recommend timing**:
- Not just approve/reject
- Shape proposals into actionable plans

**Example**:
```markdown
Worker: "Should I implement feature X?"

Supervisor: "Let's break this down:
- Scenario A (Screenshots): 30min
- Scenario B (Demo): 2h
- Scenario C (Full Feature): 5h

What's the actual requirement? [L084: Evidence before implementation]"
```

---

### Success Criteria

✅ Process violations identified and corrected
✅ Quantitative ratings provided (X/10)
✅ Specific actionable feedback given
✅ Improvement acknowledged (2/10 → 9/10)
✅ Workers learn patterns over time

---

### Impact

**Quantified**:
- Process compliance: 2/10 → 9/10 (350% improvement)
- Gate discipline violations reduced
- Teaching effectiveness: Workers apply patterns independently after critique

**Example**: Worker violated gate discipline (2/10 rating), received critique with specific corrections, applied corrections (9/10 rating), now follows pattern autonomously.

---

## File-Based Worker Coordination (L100)

### Problem

Conversational coordination is ambiguous:
- Workers can't distinguish "waiting for answer" from "free to proceed"
- "Ask but don't wait" pattern emerges
- Process violations due to ambiguity

**Example**: Worker asks question, supervisor provides guidance, worker proceeds immediately without explicit GO.

---

### Pattern

**File-based coordination with explicit blocking states**:

### Structure

**Checkpoint File** (four sections filled sequentially):
```markdown
# Checkpoint: Gate N

## 1. Worker Checkpoint Request
[Worker describes options, proposes approach]

**Status**: PAUSED
**Blocked On**: supervisor_decision
**Worker Action**: WAIT

---

## 2. Supervisor Decision
[Supervisor provides guidance, success criteria]

**Decision**: APPROVED
**Success Criteria**:
- [ ] Criterion 1
- [ ] Criterion 2
- [ ] Criterion 3

**Worker Action**: EXECUTE

---

## 3. Worker Execution Report
[Worker reports completion, evidence of success]

**Status**: COMPLETED
**Completed At**: 2025-10-13
**Worker Action**: REPORT

---

## 4. Supervisor Review
[Supervisor reviews against success criteria]

**Gate Status**: APPROVED
**Process Rating**: 9/10
**Next Gate**: GO
```

---

### Enforcement Mechanisms

**Status Field** → Explicit state:
- PAUSED (waiting for decision)
- IN_PROGRESS (actively working)
- COMPLETED (work done, awaiting review)

**Blocked_On Field** → Names blocker:
- supervisor_decision
- resource_availability
- external_dependency
- user_clarification

**Worker Action Field** → Unambiguous instruction:
- WAIT (do not proceed)
- EXECUTE (proceed with work)
- REPORT (report completion)

**Success Criteria Checklist** → Defines "done":
```markdown
**Success Criteria**:
- [ ] File X updated with Y changes
- [ ] Tests pass (Z/Z)
- [ ] Documentation generated
- [ ] Commit includes learning reference
```

**Git Commits** → Synchronization points:
- Worker commits checkpoint request
- Supervisor commits decision
- Worker commits execution report
- Supervisor commits review
- Cannot proceed without committing (forces synchronization)

---

### When to Use

Apply file-based coordination when:
- Multi-gate projects with supervisor-worker collaboration
- Gates requiring go/no-go decisions
- Work where scope/approach needs approval
- Situations with previous process violations

---

### Quick Start (for Supervisors)

**Pattern Flow**:
1. Worker reaches gate decision point → Creates checkpoint request
2. Worker writes status, blocked_on, worker action → Commits → **STOPS**
3. Supervisor reads request → Provides decision with success criteria → Commits
4. Worker reads decision → Executes → Reports completion → Commits → **STOPS**
5. Supervisor reviews against success criteria → Approves/rejects → Commits

---

### Success Criteria

✅ Explicit blocking states (WAIT/EXECUTE/REPORT)
✅ Unambiguous worker actions
✅ Success criteria defined before execution
✅ Git commits enforce synchronization
✅ Process violations eliminated

---

### Impact

**Quantified**:
- Process compliance: 2/10 → 9/10 (350% improvement)
- Ambiguity eliminated (WAIT is unambiguous)
- Violations reduced (can't proceed without committing)

**Example**: Gate 3 violation (conversational coordination) → Gate 4 compliance (file-based coordination) = 350% process improvement.

---

## Learning Document Structure (L051)

### Problem

Inconsistent learning document formats made it difficult to:
- Find specific information (where's the protocol?)
- Extract patterns (what's the anti-pattern?)
- Measure impact (what's the before/after?)

---

### Pattern

**Hierarchical structure with required sections**:

### Structure

**Heading Hierarchy**:
- `#` (H1): Document title only - format `# L##: Title`
- `##` (H2): Major sections
- `###` (H3): Subsections within major sections

**Required Sections**:
- **Problem**: Concrete waste/pain with quantification
- **Learning**: Actionable protocols listed FIRST (answers "what should I do?")

**Optional Sections** (include when relevant):
- **Protocol**: Step-by-step copy-paste commands
- **Helper Tools**: Usage examples with expected output
- **Integration Points**: Where/when to apply learning
- **Anti-Patterns**: What NOT to do (❌/✅ examples)
- **Impact**: Before/after metrics
- **Related Learnings**: Links to related L## documents

---

### Example Template

```markdown
# L##: Title

## Problem
[Concrete waste/pain with quantification]
Example: "Manual grep takes 2-5min per search"

## Learning
[Actionable protocols listed FIRST]

### Standard Locations
- Location 1: Purpose
- Location 2: Purpose

### Protocol (Step-by-Step)
1. Step 1
2. Step 2
3. Step 3

### Helper Tools
**Tool 1**:
```bash
command example
```

## Anti-Patterns
❌ **Bad Practice**: Description
✅ **Good Practice**: Description

## Impact
**Before**: Metric 1
**After**: Metric 2
**Improvement**: X% or Y time saved

## Related Learnings
- L042: Related pattern 1
- L084: Related pattern 2
```

---

### Success Criteria

✅ Problem section with quantified waste
✅ Learning section with protocols FIRST
✅ Anti-patterns with ❌/✅ examples
✅ Impact section with before/after metrics
✅ Related learnings cross-referenced

---

### Impact

**Quantified**:
- Consistency: 100% of L100+ learnings follow structure
- Discoverability: Find protocols in <5s (not 2min)
- Reusability: Copy-paste protocols directly

**Pattern**: Answer "what should I do?" immediately, then provide context (why) and evidence (impact).

---

## Pattern Integration

These patterns work together as a system:

```
Gate Sizing (L104)
    ↓ determines number of gates
Gate Execution Discipline (L042)
    ↓ enforces WAIT at boundaries
File-Based Coordination (L100)
    ↓ provides explicit blocking states
Multi-Agent Process Enforcement (L099)
    ↓ catches violations, provides critique
Evidence Before Implementation (L084)
    ↓ prevents wasted work upfront
Learning Document Structure (L051)
    ↓ documents patterns for reuse
Recursive Supervision (L099)
    ↓ enables scale to 100+ agents
```

**Result**: Coherent system for human-supervised collaborative coding at scale.

---

## Related Documentation

- **[Design Philosophy](./DESIGN_PHILOSOPHY.md)** - Principles underlying these patterns
- **[Getting Started](./GETTING_STARTED.md)** - Applying patterns to first agent
- **[Framework Homepage](./README.md)** - Overview and positioning

---

## Learning References

This pattern document synthesizes:
- L042: Gate execution discipline
- L051: Learning document structure
- L084: Evidence before implementation
- L099: Recursive supervision model
- L099: Multi-agent process enforcement
- L100: File-based worker coordination
- L104: Gate sizing heuristic

Full learning documents available in `.aget/evolution/` of any AGET agent repository.

---

*Core Patterns v2.8.0 - Last updated: 2025-11-10*
