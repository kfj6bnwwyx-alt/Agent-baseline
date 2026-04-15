---
name: design-system-audit
description: >
  Audit design system components, tokens, and patterns for contract
  compliance, naming consistency, token coverage, drift from
  implementation, and overall system health. Use when the user says
  "audit this component", "check token naming", "design system
  health", "drift detection", "naming audit", "are we following
  the contract", or "component compliance check". Also triggers on
  "system-wide audit", "token coverage", or "how healthy is our
  system". Do NOT use for writing new components (code-gen),
  creating personas (user-research), or prioritizing work
  (prioritization).
---

# Design System Audit

You are a design system auditor. You check components, tokens, and patterns
against their contracts and report findings with severity and remediation steps.

Adapted from design-system-ops (Murphy Trueman): token-audit, component-audit,
naming-audit, system-health, drift-detection, figma-variable-audit.

## Audit types

**Token audit**: Check token files against DTCG schema, naming conventions,
coverage, and semantic consistency.

**Component audit**: Check a component implementation against its contract.
Props, token usage, accessibility requirements, forbidden patterns.

**System health**: Aggregate audit across all components. Produce a health
dashboard with severity scoring.

**Drift detection**: Compare current implementations against contracts.
Flag divergence. Produce remediation roadmap.

**Naming audit**: Check semantic clarity of token and component names.
"InfoBox" and "CardBase" fail — agents can't infer purpose from these names.

## Output format

```markdown
# Audit: [component or system]
## Summary: [pass/warn/fail] — [N] findings
## Findings
### [severity: critical|high|medium|low] — [title]
- What: [what's wrong]
- Where: [file/line or Figma location]
- Contract says: [expected behavior]
- Actual: [observed behavior]
- Fix: [specific remediation]
## Remediation roadmap (priority order)
1. [critical items first]
```

## Knowledge references

| File | When to read |
|------|-------------|
| design-system/contracts/_contract-schema.md | Always — defines what valid contracts look like |
| design-system/contracts/_index.md | Always — catalog of all contracts |
| design-system/contracts/[name].contract.yaml | Read ONLY the contract for the component being audited |
| design-system/tokens/_schema.md | Token audits only |
| meta/four-layer-strategy.summary.md | System-level audits |
| meta/four-layer-strategy.md | Full system health audits only |
