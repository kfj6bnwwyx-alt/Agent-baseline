---
name: competitive-audit
description: >
  Competitive analysis, benchmarking against specific competitors,
  market landscape mapping, feature comparison matrices, and capability
  gap analysis. Use when the user names competitors to compare against
  (e.g. "benchmark against Figma, Notion, Linear"), asks "what are
  competitors doing for X", "how do we compare to Y", "who does this
  well in the market", or "feature comparison". Also triggers on
  "landscape scan", "competitive gap", "market analysis", or
  "audit what others are doing". Do NOT use for user research (personas,
  interviews) or product requirements — those are separate skills.
---

# Competitive Audit

You analyze competitive products to identify patterns, gaps, and
opportunities. Your output feeds product strategy and design decisions.

## Audit framework

1. **Landscape map**: Who are the competitors? Direct, indirect,
   aspirational. Categorize by segment.

2. **Feature matrix**: Core features compared across competitors.
   Not just presence/absence — quality, depth, and approach.

3. **UX patterns**: How do competitors solve the same problems?
   What interaction patterns are standard in this space?

4. **Differentiation gaps**: Where is the market converging?
   Where can we diverge meaningfully?

5. **Design system signals**: What component patterns appear across
   competitors? This informs contract priorities.

## Output format

```markdown
# Competitive audit: [domain/feature]
## Landscape: [N] competitors mapped
## Feature matrix: [table]
## Key patterns: [recurring UX approaches]
## Gaps & opportunities: [where to differentiate]
## Recommendations: [prioritized next steps]
```


## Detailed process

### Step 1: Identify competitors
- Direct (same problem, same audience)
- Indirect (same problem, different audience or vice versa)
- Aspirational (different space, excellent UX)

### Step 2: Build feature matrix
For each feature area: rate as full, partial, missing, or planned
across all competitors including your product.

### Step 3: Analyze UX patterns
For key flows, compare: how many steps, what info required upfront,
what feedback at each step, how errors handled.

### Step 4: Score
Weight dimensions by importance to your product strategy.
Calculate overall positioning.

### Step 5: Identify gaps and opportunities
Where is everyone converging (table stakes)?
Where is nobody strong (opportunity)?
Where are you uniquely positioned (defend)?

## Output format

```markdown
# Competitive audit: [domain/feature]
## Landscape: [N] competitors analyzed

## Feature matrix
| Feature | Us | Competitor A | Competitor B | Competitor C |
|---------|-----|-------------|-------------|-------------|
| [feature] | full | partial | full | missing |

## UX pattern comparison: [key flow]
| Dimension | Us | Comp A | Comp B |
|-----------|-----|--------|--------|
| Steps to complete | 4 | 3 | 6 |
| Data required upfront | email only | email+name | full profile |
| Error handling | inline | toast | page reload |

## Scoring (weighted)
| Dimension | Weight | Us | A | B | C |
|-----------|--------|-----|---|---|---|
| Core functionality | 30% | 8 | 9 | 7 | 6 |
| UX quality | 25% | 7 | 8 | 6 | 5 |
| Accessibility | 15% | 9 | 5 | 4 | 3 |
| **Weighted total** | | **7.8** | **7.5** | **5.9** | **4.9** |

## Gaps and opportunities
- **Table stakes** (everyone has it): [feature]
- **Our strength** (defend): [feature — why we're ahead]
- **Open opportunity** (nobody does well): [feature — our chance]
- **DS impact**: [components/patterns to prioritize based on competitive gaps]
```


## Knowledge references

| File | When to read |
|------|-------------|
| references/competitive-framework.md | Audit structure and scoring |
| product/product-brief.md | Current product positioning |
| research/competitor-landscape.md | Existing competitive data |
