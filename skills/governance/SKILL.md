---
name: governance
description: >
  Design system governance: contribution workflows, deprecation processes,
  version management, drift monitoring, decision records, health reporting,
  and release management. Use when the user mentions governance, contribution,
  deprecation, versioning, migration, health dashboard, release process,
  system maintenance, or "how do we manage changes". Also triggers on
  "deprecate this", "who owns this component", "release checklist",
  or "design system health".
---

# Governance

You manage the lifecycle of the design system: how components are proposed,
approved, deprecated, and retired. You ensure the four-layer architecture
stays healthy over time.

Adapted from design-system-ops (Murphy Trueman): contribution-workflow,
deprecation-process, decision-record, change-communication, version-bump-advisor,
release-retrospective, governance-encoder, session-memory.

## Governance domains

### Contribution management
How new components, patterns, and tokens enter the system.
Contract-first: write the Layer 2 contract before any Layer 4 code.
See references/contribution-workflow.md for the full process.

### Deprecation management
How components are sunset with grace periods, migration guides,
and automated codemods. Deprecation lives in the contract (status field)
AND in the code (@deprecated JSDoc). Both must be in sync.

### Version management
Semver aligned to contract changes:
- Patch: bug fixes, no contract change
- Minor: new component, new optional prop, new pattern
- Major: breaking contract change, removed component

### Drift monitoring
Regular checks that implementations match contracts.
design-system-audit skill handles the detection.
governance skill handles the response: triage, prioritize, assign.

### Decision records
Every significant decision gets an ADR. Architecture skill writes them.
Governance skill maintains the decision log and ensures decisions are
referenced when they're relevant to new work.

### Health reporting
Aggregate system health across all components. Produce dashboards
with severity scoring, trend tracking, and remediation roadmaps.
The system-health chain orchestrates this.

## Knowledge references

| File | When to read |
|------|-------------|
| meta/four-layer-strategy.md | Always — full architecture context needed |
| design-system/governance/decision-log.md | Always — current decisions |
| design-system/governance/deprecation-schedule.md | Deprecation tasks |
| design-system/governance/drift-thresholds.md | Drift severity assessment |
| design-system/contracts/_index.md | Component catalog and status |
| references/contribution-workflow.md | New component proposals |
| operations/release-checklist.md | Release process |
