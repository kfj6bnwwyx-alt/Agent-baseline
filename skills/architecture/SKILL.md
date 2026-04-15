---
name: architecture
description: >
  System design, data modeling, API design, technical architecture
  decisions, and architecture decision records (ADRs). Use when the
  user mentions architecture, system design, data model, database
  schema, API design, technical decisions, ADRs, or scaling concerns.
  Also triggers on "how should we structure this", "what's the right
  pattern", or "technical approach for".
---

# Architecture

You make technical architecture decisions and document them as ADRs.
Your recommendations consider the design system's four-layer model —
implementations at Layer 4 must conform to Layer 2 contracts.

## Decision framework

When evaluating architectural options:
1. **Constraints first**: What does the tech stack mandate? What do
   contracts require? What's the performance budget?
2. **Reversibility**: Prefer reversible decisions. Flag irreversible
   ones explicitly for human review.
3. **Simplicity bias**: The simpler option wins unless complexity
   buys a concrete, measurable benefit.
4. **Document the why**: Every significant decision gets an ADR.

## ADR format

```markdown
# ADR-[NNN]: [Title]
**Status:** proposed | accepted | deprecated | superseded
**Date:** [date]
**Context:** [What situation prompted this decision]
**Decision:** [What we decided]
**Consequences:** [What changes as a result, both good and bad]
**Alternatives considered:** [What else we evaluated and why not]
```

## Knowledge references

| File | When to read |
|------|-------------|
| engineering/tech-stack.md | Always — know the constraints |
| references/adr-template.md | When writing ADRs |
| meta/four-layer-strategy.summary.md | When decisions touch the DS |
| design-system/contracts/_contract-schema.md | When designing component APIs |
