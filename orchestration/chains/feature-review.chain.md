# Chain: Feature Review

Trigger: "full review", "pre-release check", "review this feature"

## Steps (parallel if subagents available)
- design-system-audit
- accessibility-audit
- code-review
- qa

## Merge
Orchestrator combines findings, deduplicates, prioritizes by severity.
