# Context Window Strategy

## Budgets
| Runtime | Window | Usable |
|---------|--------|--------|
| Claude.ai/Code | ~180K | ~170K |
| Windsurf/Cursor | ~128K | ~120K |

## Rules
1. Progressive disclosure: L1 always → L2 on trigger → L3 on demand
2. Conditional loading: every ref has a "when to read" condition
3. One skill = one concern

## Context bridge (between chained steps)
Target ~500 tokens. Replaces ~10K+ of conversation replay.

```
## Step N → Step N+1
### Done: [1-2 sentences]
### Artifacts: [files]
### Decisions: [key choices]
### Next needs: [context for next step]
### Load: [knowledge-base paths]
```

## Thresholds
- Skill L2+L3 > 15K → split skill
- History > 40K → bridge
- Total > 80K (Windsurf) / 120K (Claude) → session break
