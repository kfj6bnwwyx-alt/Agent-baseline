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


## Process

### Step 1: Scope the audit
Determine what's being audited: single component, token set, or full system.
Load only the relevant contracts — never all contracts for a single-component audit.

### Step 2: Run checks per dimension
For each of the 7 contract dimensions, verify the implementation matches:
1. API: Props exist with correct types and defaults?
2. Visual: All token references resolve? No hardcoded values?
3. Accessibility: ARIA roles, keyboard, focus, screen reader?
4. Composition: Correct slot usage? Valid nesting?
5. Behavior: All states implemented? Transitions correct?
6. Rules: Any don't violations? Forbidden compositions used?
7. Platform: Correct imports, render elements, framework patterns?

### Step 3: Score and classify
- **Critical**: Breaks contract, a11y violation, blocked import. Must fix now.
- **High**: Token violation, missing state, performance regression. Fix this sprint.
- **Medium**: Naming inconsistency, missing test. Fix when touched.
- **Low**: Nitpick, optional improvement. Author's discretion.

### Step 4: Produce remediation roadmap
Order findings by severity, group by component, estimate effort per fix.

## Output format

```markdown
# Audit: [scope]
## Summary: [pass/warn/fail] — [N] findings across [N] components

## Findings

### [CRITICAL] Token hardcoding — Button.tsx:42
**Contract says:** `background: action.primary.bg`
**Actual:** `background: '#4338ca'`
**Fix:** Replace with `var(--action-primary-bg)` or token reference
**Effort:** 5 minutes

### [HIGH] Missing loading state — Dialog.tsx
**Contract says:** Dimension 5 requires `loading` state
**Actual:** No loading state implemented
**Fix:** Add loading prop, spinner, aria-busy
**Effort:** 2 hours

## Remediation roadmap
| Priority | Component | Finding | Effort |
|----------|-----------|---------|--------|
| 1 | Button | Token hardcoding | 5 min |
| 2 | Dialog | Missing loading | 2 hrs |
```

## Example: Token audit

Input: "Audit our color tokens for DTCG compliance"

Process:
1. Load `tokens/_schema.md` for naming conventions
2. Load all `*.tokens.json` files
3. Check: every token has `$value`, `$type`, and follows naming convention
4. Check: semantic tokens reference primitives (not hardcoded values)
5. Check: no orphaned tokens (defined but never referenced in contracts)

Output: Compliance report with specific file:line references for every violation.


## Knowledge references

| File | When to read |
|------|-------------|
| design-system/contracts/_contract-schema.md | Always — defines what valid contracts look like |
| design-system/contracts/_index.md | Always — catalog of all contracts |
| design-system/contracts/[name].contract.yaml | Read ONLY the contract for the component being audited |
| design-system/tokens/_schema.md | Token audits only |
| meta/four-layer-strategy.summary.md | System-level audits |
| meta/four-layer-strategy.md | Full system health audits only |



## Integration with Murphy's design-system-ops

When the design-system-ops plugin is installed, Murphy's audit skills
add capabilities beyond our process:

### Dual scoring
Murphy's audits separate two scores:
- **Thoroughness**: How complete was the audit? (Did it check everything?)
- **Compliance**: How compliant is the component? (Did it pass?)

A thorough audit with low compliance = "we found a lot of issues."
A shallow audit with high compliance = "it looks OK but we didn't check deeply."

### HTML dashboard generation
Murphy's system-health skill generates self-contained HTML dashboards
with health radar, severity distribution, priority matrix, and metric
cards. Open in any browser, no dependencies.

### Token audit with DTCG alignment
Murphy's token-audit checks naming, coverage, AND DTCG standard
alignment — producing a prioritized remediation roadmap.

### Combined workflow
1. Run our design-system-audit for contract-level checks (7 dimensions)
2. Run Murphy's audits for execution-level checks (token compliance, naming)
3. Merge findings into a single dashboard



## Delegation to Murphy's design-system-ops

When the design-system-ops plugin is installed, delegate execution:

| Audit type | Your skill does | Murphy's skill does |
|-----------|----------------|-------------------|
| Token audit | Define scope, load contracts | Run scan, produce dual score, remediation roadmap |
| Component audit | Load 7-dim contract, define pass criteria | Run compliance check, map to WCAG/DTCG |
| Naming audit | Define naming conventions from token schema | Scan codebase, flag inconsistencies |
| Drift detection | Define drift thresholds from governance | Scan for hardcoded values, wrong-tier refs |
| System health | Define health metrics from metrics-framework | Generate HTML dashboard with radar and cards |

### Combined workflow pattern
```
1. YOUR skill: Load contract, define what "compliant" means per 7 dimensions
2. MURPHY's skill: Execute the audit, produce scored findings
3. YOUR skill: Apply quality gate logic (pass/fail/loop per chain)
4. MURPHY's skill: Generate dashboard output
```

Your skill owns the architecture (what to check against).
Murphy's skill owns the execution (how to check and score).
