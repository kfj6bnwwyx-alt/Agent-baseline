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

## Knowledge references

| File | When to read |
|------|-------------|
| product/product-brief.md | Always — current product context |
| product/metrics-framework.md | Defining success metrics |
| references/prd-template.md | Template for new PRDs |
| research/personas/ | User context for stories |
| design-system/contracts/_index.md | Checking DS impact |
