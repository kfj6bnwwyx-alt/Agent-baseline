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


## Detailed process

### Step 1: Load acceptance criteria
From the product brief or user story. Each criterion is binary: pass or fail.

### Step 2: Contract compliance check
Load the component contract. Verify each dimension:
- Are all props working as specified?
- Do all states exist and transition correctly?
- Is the component accessible per Dimension 3?

### Step 3: Edge case discovery
Systematically test:
- **Empty data**: What happens with no content?
- **Maximum data**: Longest possible text, most items, largest file
- **Rapid action**: Double-click, rapid submit, spam the button
- **Slow connection**: 3G simulation, timeout behavior
- **Interrupted flow**: Close tab mid-action, lose connection, back button
- **Browser variations**: Chrome, Firefox, Safari, mobile browsers
- **RTL text**: Does layout flip correctly for Arabic/Hebrew?
- **Screen sizes**: 320px to 2560px+ viewport width

### Step 4: Regression check
What else could this change break?
Check components that compose with the changed component.
Run existing test suite and flag new failures.

### Step 5: Ship/no-ship recommendation

## Output format

```markdown
# QA Report: [feature/component]
## Recommendation: [ship/fix-and-reship/block]

## Acceptance criteria
| # | Criterion | Result | Evidence |
|---|-----------|--------|----------|
| 1 | User can submit the form | PASS | Tested Chrome, Firefox, Safari |
| 2 | Error shown for invalid email | PASS | Shows inline error with fix guidance |
| 3 | Loading state during submission | FAIL | No loading indicator shown |

## Edge cases found
### Double-submit sends duplicate requests
**Severity:** High
**Steps:** Click submit twice quickly
**Expected:** Second click ignored during loading
**Actual:** Two API requests sent
**Fix:** Disable submit during loading state (contract Dim 5 requires this)

## Regression check
- [x] Existing form tests pass
- [x] Dialog composition unaffected
- [ ] Toast notification after submit — not tested (no test exists)
```


## Knowledge references

| File | When to read |
|------|-------------|
| references/bug-report-template.md | Bug reporting |
| design-system/contracts/[name].contract.yaml | Contract validation |
| product/product-brief.md | Acceptance criteria source |
