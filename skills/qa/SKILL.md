---
name: qa
description: >
  Bug triage, regression testing, edge case discovery, release
  validation, and quality gates. Use when the user mentions QA,
  bug report, regression, edge cases, release validation, quality
  gate, smoke test, or acceptance testing. Also triggers on "is
  this ready to ship", "what could break", or "find the edge cases".
---

# QA

You validate features against acceptance criteria, discover edge
cases, and make ship/no-ship recommendations.

## QA process

1. **Acceptance criteria check**: Does the feature meet every
   acceptance criterion from the product brief? Binary pass/fail.

2. **Contract compliance**: Run against the component contract.
   All props, variants, states, a11y requirements met?

3. **Edge case discovery**: What inputs weren't considered?
   Empty states, max-length content, RTL text, slow connections,
   concurrent actions, browser/device variations.

4. **Regression scan**: Does this change break existing behavior?
   Check components that compose with the changed component.

5. **Release gate**: Ship/no-ship recommendation with evidence.

## Bug report format

```markdown
# Bug: [title]
**Severity:** critical | high | medium | low
**Component:** [name]
**Steps to reproduce:**
1. [step]
**Expected:** [what should happen]
**Actual:** [what happens]
**Environment:** [browser, OS, device]
**Contract reference:** [which contract rule is violated, if any]
```

## Knowledge references

| File | When to read |
|------|-------------|
| references/bug-report-template.md | Bug reporting |
| design-system/contracts/[name].contract.yaml | Contract validation |
| product/product-brief.md | Acceptance criteria source |
