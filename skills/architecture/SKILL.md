---
name: architecture
description: >
  Technical architecture decisions, ADRs (architecture decision
  records), system structure, data modeling, database schema choices,
  API endpoint design, and technology selection. Use when the user
  asks "should we use web components or framework-specific", "write
  an ADR for", "what's the right technical approach", "data model for",
  "API structure for", "choose between Radix vs building custom", or
  any question about how to technically structure a system. Also
  triggers on "tech decision", "system diagram", or "schema". Do NOT
  use for implementing code (code-gen) or reviewing code (code-review).
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


## Detailed process

### Step 1: Clarify the decision
What exactly needs deciding? What are the constraints?
Load tech-stack.md for existing decisions and blocked approaches.

### Step 2: Enumerate options
List 2-4 realistic options. For each:
- What does it look like?
- What are the consequences (positive, negative, neutral)?
- What's the reversibility (easy to change later, or locked in)?
- What's the cost (implementation effort, ongoing maintenance)?

### Step 3: Evaluate against criteria
- Does it work within the tech stack constraints?
- Does it conform to the four-layer architecture?
- Is it the simplest option that meets the requirements?
- What's the impact on existing consumers?

### Step 4: Recommend and document
Pick the best option. Document as an ADR.
Flag if the decision needs broader review before accepting.

## Output format

```markdown
# ADR-[NNN]: [Title]

**Status:** proposed
**Date:** [date]
**Context:**
We need to [decision needed] because [situation].
Currently [how it works now]. This is causing [problem].

**Decision:**
Use [chosen approach] because [primary reason].

**Consequences:**

### Positive
- [benefit with explanation]

### Negative  
- [tradeoff with explanation]
- [mitigation for this tradeoff]

### Neutral
- [side effect]

**Alternatives considered:**

### [Option B]
[What it is, why we didn't pick it — be specific about the downside]

### [Option C]
[What it is, why we didn't pick it]
```

## Example: Component library architecture

Input: "Should we use web components or framework-specific components?"

```markdown
# ADR-001: Component implementation strategy

**Status:** proposed
**Context:**
We need to support React, Angular, and SwiftUI from a single design system.
Layer 2 contracts are framework-agnostic. The question is Layer 4 approach.

**Decision:**
Use framework-specific adapters (one package per framework) conforming to
Layer 2 contracts. Not web components.

**Consequences:**
### Positive
- Each framework gets idiomatic components (React hooks, Angular DI, SwiftUI modifiers)
- No web component shadow DOM styling complexity
- Smaller bundle per consumer (only their framework)

### Negative
- Must maintain N implementations instead of 1
- Risk of drift between implementations (mitigated by contract tests)

### Alternatives considered:
### Web components
Rejected: shadow DOM makes theming with design tokens difficult.
Angular and React wrappers around web components add bundle weight
and lose framework idioms. The maintenance savings don't materialize
because you still need framework-specific wrappers.
```


## Knowledge references

| File | When to read |
|------|-------------|
| engineering/tech-stack.md | Always — know the constraints |
| references/adr-template.md | When writing ADRs |
| meta/four-layer-strategy.summary.md | When decisions touch the DS |
| design-system/contracts/_contract-schema.md | When designing component APIs |
