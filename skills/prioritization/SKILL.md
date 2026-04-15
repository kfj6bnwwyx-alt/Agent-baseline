---
name: prioritization
description: >
  Prioritize and sequence work: RICE scoring, ICE scoring, value vs
  complexity matrices, MoSCoW, backlog ranking, and roadmap sequencing.
  Use when the user says "prioritize these items", "rank this backlog",
  "RICE score", "what should we build first", "is this worth building",
  "sequence the roadmap", "help me decide between X and Y", or "what
  order should we tackle these". Also triggers on "tradeoff analysis",
  "effort vs impact", or "stack rank". Do NOT use for writing
  requirements (product-brief) or competitive analysis.
---

# Prioritization

You help make sequencing decisions using structured frameworks.
You present tradeoffs clearly — you don't make the final call
on subjective business value (that's the human's job).

## Frameworks

**RICE** (Reach × Impact × Confidence / Effort):
- Reach: how many users affected per quarter
- Impact: minimal (0.25) / low (0.5) / medium (1) / high (2) / massive (3)
- Confidence: percentage based on evidence quality
- Effort: person-months

**Value vs. Complexity**: 2×2 matrix. Quick wins (high value, low
complexity) first. Big bets (high value, high complexity) need
validation. Avoid low-value work regardless of complexity.

**Dependencies**: What unblocks other work? Foundation items
(tokens, contracts, core components) before consumers.

## Output format

```markdown
# Prioritization: [scope]
## Scored items
| Item | Reach | Impact | Confidence | Effort | Score |
## Recommended sequence
1. [item] — [why first]
## Tradeoffs to discuss
- [option A vs B with consequences of each]
```


## Detailed process

### Step 1: List all items
Gather every candidate for prioritization. Include a one-line
description and who requested it.

### Step 2: Choose framework
- RICE: best for comparing features with usage data
- Value vs. Complexity: best for quick visual sorting
- MoSCoW: best for sprint-level scoping with fixed deadline

### Step 3: Score each item
Apply the chosen framework. Be explicit about assumptions.
If confidence is low, say so — don't fake precision.

### Step 4: Sequence considering dependencies
What unblocks other work? Foundation items (tokens, core contracts)
before consumers. Platform items before features.

### Step 5: Present tradeoffs for human decision
You recommend, you don't decide. Present the data and the
tradeoffs. Flag where reasonable people could disagree.

## Output format

```markdown
# Prioritization: [scope]
## Framework: RICE

## Scored items
| # | Item | Reach | Impact | Confidence | Effort | Score | Rank |
|---|------|-------|--------|-----------|--------|-------|------|
| 1 | Dark mode support | 5000 | 2 | 80% | 3 | 2667 | 1 |
| 2 | DatePicker component | 2000 | 1 | 50% | 2 | 500 | 3 |
| 3 | Accessibility audit fixes | 5000 | 2 | 100% | 1 | 10000 | — |

Note: A11y audit fixes score highest but should be weighted
against regulatory risk, not just RICE score.

## Recommended sequence
1. **A11y audit fixes** — unblocks compliance, highest impact
2. **Dark mode** — high reach, enables token architecture improvement
3. **DatePicker** — lower confidence, validate need first

## Tradeoffs to discuss
- Dark mode requires token migration chain. Do we have capacity?
- DatePicker confidence is 50% — should we validate with research first?
- A11y fixes have no customer-visible feature delivery. Stakeholder buy-in?
```


## Knowledge references

| File | When to read |
|------|-------------|
| references/scoring-models.md | Framework details |
| product/roadmap.md | Current roadmap context |
| product/metrics-framework.md | How to measure impact |
