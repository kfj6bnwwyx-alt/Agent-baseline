---
name: product-brief
description: >
  Write PRDs, requirements documents, user stories with acceptance
  criteria, feature specifications, and epic definitions. Use when
  the user says "write a PRD", "define requirements", "acceptance
  criteria for", "scope this feature", "user stories for", "epic
  definition", or "what should we build and why". Also triggers on
  "product spec", "feature definition", or "requirements document".
  Do NOT use for implementation (code-gen), visual design (ui-design),
  or competitive analysis (competitive-audit).
---

# Product Brief

You write structured product requirements that designers can design
against and engineers can build against. Your output is the starting
point for design and engineering chains.

## Requirements structure

### Problem statement
What problem are we solving? Who has it? How do we know it's real?
Cite research (user-research skill output) or data. Never assume.

### Success metrics
Measurable outcomes with baselines and targets. If you can't measure
it, you can't ship it. Reference metrics-framework.md for patterns.

### User stories
Format: As a [role], I want [capability] so that [outcome].
Each story has acceptance criteria: testable, binary pass/fail statements
that the qa skill will validate against.

### Scope definition
Explicit in-scope and out-of-scope lists. "Out of scope" is as important
as "in scope" — it prevents scope creep and aligns expectations.

### Design system impact
Every feature spec must declare:
- New components needed (triggers new-component chain)
- Existing components modified (triggers component-update chain)
- New patterns needed (triggers pattern creation in Layer 2b)
- Token changes (triggers token-migration chain)

This section bridges product to the four-layer architecture.

### Technical considerations
Dependencies, constraints, risks, and open questions.
Flag decisions that need architecture skill ADRs.


## Detailed process

### Step 1: Define the problem
What problem are we solving? Who has it? Cite evidence (research, data,
support tickets). Never assume — if evidence is missing, flag it.

### Step 2: Set success metrics
Use the metrics framework. Each metric needs:
- Current baseline (or "unknown — measurement needed")
- Target value
- How it's measured
- When it's measured

### Step 3: Write user stories
Format: As a [role], I want [capability] so that [outcome].
Each story gets acceptance criteria: testable, binary statements.

### Step 4: Scope explicitly
In-scope and out-of-scope lists. Be specific about what's excluded.

### Step 5: Assess design system impact
This is critical — every feature spec must declare:
- New components needed → triggers new-component chain
- Existing components modified → triggers component-update chain
- New patterns needed → triggers pattern creation
- Token changes → triggers token-migration chain

## Output format

```markdown
# PRD: [Feature name]

## Problem
[Who has this problem, evidence it's real, impact of not solving]

## Success metrics
| Metric | Baseline | Target | Measurement |
|--------|----------|--------|-------------|
| Task completion rate | 62% | >85% | Analytics |
| Support tickets/week | 15 | <5 | Zendesk |

## User stories
### US-1: [title]
As a [role], I want [capability] so that [outcome].
**Acceptance criteria:**
- [ ] [Testable criterion]
- [ ] [Testable criterion]

## Scope
### In scope
- [specific feature/behavior]
### Out of scope
- [specific exclusion and why]

## Design system impact
- New components: DatePicker (no existing contract)
- Modified components: none
- New patterns: date-range-selection (composes DatePicker + Button)
- Token changes: none

## Technical considerations
- [Dependency, constraint, risk, or open question]
```

## Example

Input: "Write the PRD for adding dark mode support"

Key sections that make this specific:
- Design system impact: Token changes (all semantic tokens need dark values), no new components
- Triggers: token-migration chain for updating all token files
- Acceptance criteria: "All semantic tokens resolve to appropriate dark values", "No hardcoded colors in any component"


## Knowledge references

| File | When to read |
|------|-------------|
| product/product-brief.md | Always — current product context |
| product/metrics-framework.md | Defining success metrics |
| references/prd-template.md | Template for new PRDs |
| research/personas/ | User context for stories |
| design-system/contracts/_index.md | Checking DS impact |
