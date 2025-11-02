# Template Publishing Checklist

**Version**: 1.0.0
**Purpose**: Systematic verification for new template releases to ensure complete organization catalog integration

---

## Overview

When publishing a new AGET template to the aget-framework organization, complete ALL items in this checklist before declaring "publishing complete."

**Why this exists**: Gate 5 verification failure (template-consultant-aget) - declared complete with 3/5 organization docs updated (60% incomplete).

---

## Pre-Publishing

### 1. Template Repository Validation

- [ ] **Contract tests passing**: All tests pass (verify exact count matches documentation)
- [ ] **CI/CD configured**: `.github/workflows/ci.yml` exists and passing
- [ ] **Privacy validation**: Automated grep patterns for private references (zero violations)
- [ ] **Template structure**: Required files exist (`.aget/version.json`, `AGENTS.md`, `CLAUDE.md` symlink)
- [ ] **Documentation complete**: README, CAPABILITIES, COMPARISON_MATRIX, USAGE_GUIDE, MIGRATION_GUIDE (if applicable)
- [ ] **Version consistency**: `.aget/version.json` version matches release tag

**Validation command**:
```bash
# Run from template repository
pytest tests/ -v
gh run list --limit 1 | grep "completed.*success"
grep -ri "private-" README.md AGENTS.md docs/*.md
```

---

## Organization Catalog Integration

### 2. Enumerate All Profile Documentation Files

**Action**: List all markdown files in `.github/profile/` to create checklist

```bash
cd /tmp/aget-framework-profile
find profile -name "*.md" -type f | sort
```

**Expected files** (as of v2.7.0):
- `profile/README.md`
- `profile/GETTING_STARTED.md`
- `profile/TEMPLATE_SELECTOR.md`
- `profile/DESIGN_PHILOSOPHY.md`
- `profile/CORE_PATTERNS.md`

**Checklist created**: ✅ (5 files identified)

---

### 3. Check Each File Systematically

For EACH file in the profile, determine if template update is required:

#### README.md

**Purpose**: Organization homepage, first impression

**Search patterns**:
```bash
grep -n "template-worker\|template-advisor\|template-supervisor" profile/README.md
```

**Update locations** (if template is core/fleet role):
- [ ] **Core Templates table** (line ~37): Add new template row
  - Columns: Template name (with link), Foundation, Additional Capabilities, Status
  - Example: `| **[template-NAME-aget](URL)** | Worker + | Description | ✅ Public v2.7.0 |`
- [ ] **Foundation description** (line ~35): Update prose to mention new template
  - Example: "Advisor, consultant, and supervisor add specialized capabilities."
- [ ] **Quick Start decision tree** (line ~126): Add template to decision flow
  - Format: `Need X? → template-NAME-aget (worker + capability)`
- [ ] **Examples by Template table** (line ~100): Add example instances
  - Columns: Template, Generic Example, Personal Deployment
- [ ] **Notes section** (line ~112): Update capability notes if needed
  - Example: "Advisor and consultant agents are always `-aget`"

**Verification**:
```bash
# Count template references (should be 4 core + N specialized)
grep -c "template-" profile/README.md
# Verify new template appears in all sections
grep "template-NAME-aget" profile/README.md | wc -l
```

---

#### GETTING_STARTED.md

**Purpose**: Onboarding guide for new AGET users

**Search patterns**:
```bash
grep -n "template-worker\|template-advisor\|template-supervisor" profile/GETTING_STARTED.md
```

**Update locations** (if template is core/fleet role):
- [ ] **Decision tree diagram** (line ~43): Add template to visual decision flow
  - ASCII art tree with branches for each template type
  - Show when to choose new template vs existing options
- [ ] **Template Selection Guide table** (line ~76): Add new template row
  - Columns: Template, When to Use, Key Features, Complexity
  - Include contract test count, key differentiators
- [ ] **Common Use Cases section** (line ~83): Add use cases for new template
  - Bullet list of 3-5 specific use cases
  - Remove overlapping use cases from other templates if applicable
- [ ] **Optional fields example** (line ~213): Update persona/config examples
  - Show which configuration fields apply to new template
- [ ] **Template Deep Dive section** (line ~540): Add new subsection
  - Document core patterns, choosing criteria, key features
  - Include "when to use vs other templates" guidance
- [ ] **Success Criteria** (line ~591): Update contract test counts
  - Example: "(7 tests for worker, 30 for advisor, 55 for consultant, ...)"
- [ ] **Estimated time** (line ~599): Update time estimates
  - Example: "30 minutes for worker, 45 minutes for advisor/consultant, ..."

**Verification**:
```bash
# Verify template in decision tree
grep -A 20 "decision tree" profile/GETTING_STARTED.md | grep "template-NAME-aget"
# Verify template in table
grep "template-NAME-aget" profile/GETTING_STARTED.md | grep "When to Use"
# Verify deep dive section exists
grep "### .*NAME.*Deep Dive" profile/GETTING_STARTED.md
```

---

#### TEMPLATE_SELECTOR.md

**Purpose**: Detailed template comparison and decision guidance

**Search patterns**:
```bash
grep -n "template-worker\|template-advisor\|template-supervisor" profile/TEMPLATE_SELECTOR.md
```

**Update locations** (if template is core/fleet role):
- [ ] **Architecture diagram** (line varies): Update visual to show N templates
  - ASCII art or description showing template relationships
- [ ] **Decision tree** (line varies): Add template to decision flow
  - Multi-level decision tree with template selection criteria
- [ ] **Comparison matrix table** (line varies): Add new template column
  - Rows: Features (contract tests, write permissions, personas, etc.)
  - Columns: Each template
  - Fill in all feature rows for new template
- [ ] **Individual template section**: Add dedicated section
  - Repository link
  - Quick description
  - When to use (vs other templates)
  - Key features and patterns
  - Extraction story (if applicable)
- [ ] **Role-based recommendations** (line varies): Add template to role guidance
  - Map user roles (e.g., "consultant/strategist") to template
- [ ] **Decision examples** (line varies): Add template-specific scenarios
  - Concrete examples: "If you need X, use template-NAME-aget"
- [ ] **Common questions** (line varies): Add template-specific FAQs
  - "When to use NAME vs OTHER?" answers

**Verification**:
```bash
# Count template columns in comparison matrix
grep -A 50 "Comparison Matrix" profile/TEMPLATE_SELECTOR.md | grep "template-" | wc -l
# Verify dedicated section exists
grep "## .*template-NAME-aget" profile/TEMPLATE_SELECTOR.md
```

---

#### DESIGN_PHILOSOPHY.md

**Purpose**: Framework principles and design rationale

**Search patterns**:
```bash
grep -n "template-worker\|template-advisor\|template-supervisor" profile/DESIGN_PHILOSOPHY.md
```

**Typical updates**: **NONE** (philosophy is template-agnostic)

**Check for**:
- [ ] Template-specific examples that need updating (rarely)
- [ ] Abstract template references (usually fine as-is)
- [ ] Enumerated template lists (update if present)

**Verification**:
```bash
# Check if file mentions templates specifically
grep "template-" profile/DESIGN_PHILOSOPHY.md | grep -v "template system\|template-based"
# If output is empty or generic references only → no updates needed
```

---

#### CORE_PATTERNS.md

**Purpose**: Tactical patterns for effective collaboration

**Search patterns**:
```bash
grep -n "template-worker\|template-advisor\|template-supervisor" profile/CORE_PATTERNS.md
```

**Typical updates**: **NONE** (patterns apply to all templates)

**Check for**:
- [ ] Pattern examples using specific templates (update if necessary)
- [ ] Contract test counts in examples (update if changed)
- [ ] Template-specific pattern applications (rare)

**Verification**:
```bash
# Check if file mentions templates specifically
grep "template-" profile/CORE_PATTERNS.md | grep -v "template pattern\|template structure"
# If output is empty or generic references only → no updates needed
```

---

## Cross-Reference Validation

### 4. Verify Template Appears in All Required Locations

**Run comprehensive grep across all files**:
```bash
cd /tmp/aget-framework-profile
for file in profile/*.md; do
  echo "=== $(basename $file) ==="
  grep -n "template-NAME-aget" "$file" || echo "  (not found)"
done
```

**Expected results** (for core templates):
- README.md: 4+ matches (table, examples, decision tree, notes)
- GETTING_STARTED.md: 6+ matches (tree, table, use cases, deep dive, criteria)
- TEMPLATE_SELECTOR.md: 8+ matches (architecture, tree, matrix, section, examples)
- DESIGN_PHILOSOPHY.md: 0-1 matches (usually none)
- CORE_PATTERNS.md: 0-1 matches (usually none)

**For specialized templates**: Expect fewer matches (may only appear in TEMPLATE_SELECTOR.md)

---

### 5. Verify Navigation Links Work

**Check for broken cross-references**:
```bash
# Find all internal links to new template
grep -r "\[.*template-NAME-aget.*\]" profile/*.md

# Find all section references
grep -r "#.*template-NAME" profile/*.md
```

**Validate**:
- [ ] All links to template repository work (https://github.com/aget-framework/template-NAME-aget)
- [ ] All internal anchor links work (e.g., `#consultant-template`)
- [ ] Cross-references between files are consistent

---

## Final Verification

### 6. Search for Template Mentions Across All Files

**Automated search**:
```bash
cd /tmp/aget-framework-profile
# Search for any template list that might be incomplete
grep -n "template-worker.*template-advisor.*template-supervisor" profile/*.md

# Expected: Find references that now include template-NAME-aget
# If found without new template → UPDATE NEEDED
```

**Manual review questions**:
- [ ] Are there any tables/lists showing "3 templates" that should show "4 templates"?
- [ ] Are there any decision trees missing the new template branch?
- [ ] Are there any "when to choose" sections that don't mention new template?
- [ ] Are there any examples using old template that should use new template?

---

### 7. Changelog/What's New (If Applicable)

**Check for**:
- [ ] `profile/CHANGELOG.md` (if exists): Add new template entry
- [ ] `profile/WHATS_NEW.md` (if exists): Document new template
- [ ] Organization release notes (if applicable)

---

### 8. Commit and PR Validation

**Before creating PR**:
```bash
cd /tmp/aget-framework-profile
git status  # Review all changed files
git diff    # Review all changes line-by-line
```

**PR checklist**:
- [ ] PR title: "catalog: Add template-NAME-aget to organization profile"
- [ ] PR body: Includes extraction story or creation rationale
- [ ] PR body: Lists all files changed with reason
- [ ] PR body: References template repository URL
- [ ] PR body: Includes contract test count and key features
- [ ] All file changes reviewed individually
- [ ] No unintended changes (e.g., formatting-only diffs)

**PR body template**:
```markdown
## Summary
Add template-NAME-aget to organization catalog.

## Template Details
- **Repository**: https://github.com/aget-framework/template-NAME-aget
- **Contract Tests**: N tests (all passing)
- **Key Features**: Feature 1, Feature 2, Feature 3
- **Extraction Story**: Extracted from X based on Y% usage / Created for Z purpose

## Files Changed
1. **README.md** (+N lines)
   - Added to Core Templates table
   - Updated decision tree
   - Added examples
2. **GETTING_STARTED.md** (+N lines)
   - Added to Template Selection Guide
   - Updated decision tree
   - Added use cases section
   - Added deep dive section
3. **TEMPLATE_SELECTOR.md** (+N lines)
   - Added to comparison matrix
   - Added dedicated template section
   - Updated decision examples

## Verification
- [x] All profile/*.md files checked
- [x] Template appears in all required locations
- [x] Cross-references validated
- [x] No broken links
- [x] No private references leaked
```

---

## Post-Publishing

### 9. Verify PR Merged and Live

**After PR merge**:
```bash
# Verify changes are live
gh api repos/aget-framework/.github/contents/profile/README.md | jq -r '.content' | base64 -d | grep "template-NAME-aget"

# Expected: New template appears in live profile
```

**Validation**:
- [ ] Visit https://github.com/aget-framework and verify new template visible
- [ ] Check README.md on GitHub web UI (not just local)
- [ ] Verify decision tree renders correctly (ASCII art intact)
- [ ] Check all links work in web UI

---

### 10. Update This Checklist (If Gaps Found)

**If verification failure occurred**:
- [ ] Document what was missed in this checklist
- [ ] Add new validation steps to prevent recurrence
- [ ] Update "Expected files" list if organization structure changed
- [ ] Increment checklist version number

**Continuous improvement**: This checklist should evolve based on actual publishing experiences.

---

## Quick Reference

### Minimal Checklist (Core Templates)

For quick verification during Gate 5:

1. ✅ Template repository: tests passing, CI green, docs complete
2. ✅ README.md: Core Templates table, decision tree, examples
3. ✅ GETTING_STARTED.md: Decision tree, table, use cases, deep dive
4. ✅ TEMPLATE_SELECTOR.md: Matrix, section, examples
5. ✅ DESIGN_PHILOSOPHY.md: Check (usually no changes)
6. ✅ CORE_PATTERNS.md: Check (usually no changes)
7. ✅ Cross-references: Grep all files for template mentions
8. ✅ PR created: Complete body, all changes reviewed
9. ✅ PR merged: Live verification on GitHub
10. ✅ Announce: Notify team/community

**Total time estimate**: 2-3 hours for complete verification

---

## Automation Opportunities

### Future Enhancements

**Automated verification script** (`.github/scripts/verify_template_catalog.sh`):
```bash
#!/bin/bash
# Usage: ./verify_template_catalog.sh template-NAME-aget

TEMPLATE=$1

echo "Verifying $TEMPLATE in organization catalog..."

# Check README.md
grep -q "$TEMPLATE" profile/README.md && echo "✅ README.md" || echo "❌ README.md MISSING"

# Check GETTING_STARTED.md
grep -q "$TEMPLATE" profile/GETTING_STARTED.md && echo "✅ GETTING_STARTED.md" || echo "❌ GETTING_STARTED.md MISSING"

# Check TEMPLATE_SELECTOR.md
COUNT=$(grep -c "$TEMPLATE" profile/TEMPLATE_SELECTOR.md)
[ "$COUNT" -ge 5 ] && echo "✅ TEMPLATE_SELECTOR.md ($COUNT mentions)" || echo "❌ TEMPLATE_SELECTOR.md (only $COUNT mentions)"

# Verify links work
if grep -q "https://github.com/aget-framework/$TEMPLATE" profile/*.md; then
  echo "✅ Repository link exists"
else
  echo "❌ No repository link found"
fi

echo ""
echo "Manual verification still required for:"
echo "  - Decision tree ASCII art rendering"
echo "  - Table formatting correctness"
echo "  - Use case descriptions accuracy"
```

---

**Checklist Version**: 1.0.0
**Created**: 2025-11-01
**Last Updated**: 2025-11-01
**Next Review**: After next template publication
