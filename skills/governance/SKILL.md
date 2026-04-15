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


## Detailed process (varies by governance domain)

### Contribution workflow
1. Receive proposal (component, pattern, or token request)
2. Check _index.md — does something similar exist?
3. If new: require contract-first development (L2 before L4)
4. Review contract with consuming teams
5. Approve → assign to sprint → track through chains

### Deprecation workflow
1. Mark contract status as "deprecated" in _index.md
2. Add `@deprecated` JSDoc to code with migration path
3. Remove from Layer 3 context files (AI stops suggesting it)
4. Set sunset date (minimum 4 weeks)
5. Generate codemod if possible (via code-gen)
6. Hard remove after all consumers migrated

### Drift response
1. Receive audit findings (from design-system-audit)
2. Triage by severity against drift-thresholds.md
3. Critical: assign to current sprint
4. High: assign to next sprint
5. Medium: add to backlog, fix when component is touched
6. Low: track, batch fix quarterly

### Health reporting
1. Aggregate audit results across all components
2. Calculate: token coverage %, contract coverage %, drift velocity
3. Compare against targets in metrics-framework.md
4. Generate dashboard with trends

## Output format

```markdown
# Governance report: [domain]

## Contribution — [component name]
**Status:** approved/deferred/redirected/rejected
**Rationale:** [why]
**Next steps:**
1. [Write contract by [date]]
2. [Review with [team] by [date]]
3. [Implement against contract by [date]]

## Health dashboard
| Metric | Current | Target | Trend |
|--------|---------|--------|-------|
| Token coverage | 87% | >95% | ↑ +3% from last month |
| Contract coverage | 65% | >80% | ↑ +5% from last month |
| Drift velocity | 8/sprint | <5 | ↓ improving |
| A11y compliance | 94% | 100% | → stable |
| Context file freshness | 3 days | <7 days | ✓ |
```

## Example: Deprecating a component

Input: "Deprecate the old Card component in favor of SurfaceCard"

```markdown
# Deprecation: Card → SurfaceCard
**Announced:** [date]
**Sunset:** [date + 6 weeks]
**Migration guide:** [link]
**Codemod available:** Yes — `npx @system/codemod card-to-surface-card`
**Consuming teams notified:** [list]
**Context files updated:** Card removed from import maps
**Contract _index.md:** Card status → deprecated, replacement → SurfaceCard
```


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
