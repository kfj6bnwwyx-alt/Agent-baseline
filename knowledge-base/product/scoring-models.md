# Scoring Models

## RICE
**Score = (Reach x Impact x Confidence) / Effort**

| Factor | Scale | Notes |
|--------|-------|-------|
| Reach | Users/quarter | Use analytics data |
| Impact | 0.25 / 0.5 / 1 / 2 / 3 | Minimal to massive |
| Confidence | 20% / 50% / 80% / 100% | Speculation to data-backed |
| Effort | Person-months | Include all disciplines |

## Value vs. Complexity (2x2)
- High value + low complexity = **Do first** (quick wins)
- High value + high complexity = **Plan carefully** (big bets)
- Low value + low complexity = **Maybe later** (fill-ins)
- Low value + high complexity = **Don't do** (money pit)

## Design system priority signals
- Token coverage gap → high (affects everything downstream)
- Missing contract for high-usage component → high
- Pattern used by >3 teams without recipe → medium
- Single-team component → lower unless blocking
- Accessibility gap → always high regardless of usage
