# Quality Gates

Quality gates are automatic checks that run between chain steps.
They determine whether to continue, loop back, or escalate to human.

## Gate types

### Contract compliance gate
**Runs after**: code-gen, component-update
**Tool**: design-system-audit agent
**Pass criteria**: Zero critical findings, zero high findings
**On fail**: Loop back to code-gen with findings (max 2 iterations)
**On second fail**: Escalate to human with full audit report

### Accessibility gate
**Runs after**: code-gen, a11y-remediation
**Tool**: accessibility-reviewer agent (+ Playwright if available)
**Pass criteria**: Zero critical a11y findings, all contract Dim 3 met
**On fail**: Loop back to code-gen with specific fixes needed
**On second fail**: Escalate with audit report

### Test gate (Superpowers integration)
**Runs after**: code-gen
**Tool**: Superpowers TDD enforcement
**Pass criteria**: All contract tests pass, all a11y tests pass
**On fail**: Code is rejected — tests must pass before proceeding
**On second fail**: N/A — Superpowers enforces this absolutely

### Pre-release gate
**Runs after**: full chain completion
**Tool**: Combined — audit + a11y + test + performance
**Pass criteria**: All sub-gates pass
**On fail**: Itemized report of what needs fixing, sorted by severity
**Escalation**: Always human review for major versions

## Gate configuration per chain

| Chain | Gates | Order |
|-------|-------|-------|
| new-component | contract → a11y → test → pre-release | Sequential |
| component-update | contract → test | Sequential |
| figma-to-code | contract → test | Sequential |
| a11y-remediation | a11y (before) → fix → a11y (after) | Loop |
| feature-review | contract + a11y + review (parallel) | Fan-out |
| system-health | all gates across all components | Batch |
| full-rebrand | token validation → contract → test (per session) | Multi-session |
