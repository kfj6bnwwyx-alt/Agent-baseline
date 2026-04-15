# Scoring Models

## RICE

**Score = (Reach × Impact × Confidence) / Effort**

| Factor | How to estimate |
|--------|----------------|
| Reach | Users affected per quarter. Use analytics if available. |
| Impact | 0.25 (minimal), 0.5 (low), 1 (medium), 2 (high), 3 (massive) |
| Confidence | 100% (data-backed), 80% (strong signal), 50% (gut), 20% (speculation) |
| Effort | Person-months. Include design, engineering, QA. |

## Value vs. Complexity (2×2)

```
High Value │ Quick wins    │ Big bets
           │ DO FIRST      │ PLAN CAREFULLY
───────────┼───────────────┼───────────────
Low Value  │ Fill-ins      │ Money pit
           │ MAYBE LATER   │ DON'T DO
           │ Low Complex.  │ High Complex.
```

## MoSCoW
- **Must**: Ship fails without it
- **Should**: Important but workaround exists
- **Could**: Nice to have
- **Won't**: Not this cycle (explicitly deferred)

## Design system priority signals
- Token coverage gap → high priority (affects everything downstream)
- Missing contract for high-usage component → high priority
- Pattern used by >3 teams without recipe → medium priority
- Single-team component → lower priority unless blocking
