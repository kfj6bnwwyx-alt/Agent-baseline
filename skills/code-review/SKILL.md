---
name: code-review
description: >
  Review existing code for quality, contract compliance, token
  discipline, blocked package violations, and performance issues.
  Use when the user says "review this code", "check this PR",
  "is this following our standards", "find anti-patterns in this",
  "this has hardcoded values", "refactor this", "clean up this
  component", or "what's wrong with this implementation". Also
  triggers on "code quality", "PR feedback", or "linting issues".
  Do NOT use for writing new code (code-gen) or writing tests
  (testing).
---

# Code Review

You review code for correctness, maintainability, performance, and
design system compliance. You are constructive — flag issues with
severity, explain why it matters, and suggest the fix.

## Review layers (check in order)

1. **Contract compliance**: Does the component implement its contract?
   Correct props, types, defaults, token usage, a11y requirements.

2. **Token discipline**: Are all visual values using design tokens?
   Flag any hardcoded colors, spacing, font sizes, radii, shadows.

3. **Blocked packages**: Anything imported from blocked libraries?
   Check against tech stack's blocked list.

4. **Code standards**: Naming, file structure, exports, TypeScript
   strictness, test co-location.

5. **Performance**: Bundle size, unnecessary re-renders, missing
   memoization, expensive operations in render paths.

6. **Anti-patterns**: Framework-specific common mistakes.

## Output format

```markdown
# Code review: [file or PR]
## Summary: [pass/needs-work/block] — [N] findings
## Findings
### [critical|high|medium|low] — [title]
**File:** `path` line [N]
**Issue:** [what and why]
**Fix:** [code suggestion]
**Rule:** [standard or contract violated]
## What's good
[Call out things done well]
```

## Severity
- **Critical**: Contract break, a11y violation, security, blocked import
- **High**: Token violation, missing states, perf regression
- **Medium**: Style inconsistency, naming, missing tests
- **Low**: Nitpick, optional optimization


## Detailed process

### Step 1: Load context
Read the component's contract and the relevant code standards.
Check tech-stack.md for blocked packages.

### Step 2: Check each review layer

**Layer 1 — Contract compliance:**
- Do props match the contract types and defaults?
- Are all contract-specified states implemented?
- Do token mappings match the contract's Dimension 2?
- Are a11y requirements from Dimension 3 met?

**Layer 2 — Token discipline:**
- Search for hardcoded hex colors, pixel values, font names
- Every visual value should trace to a token reference
- Flag any value that should be a token but isn't

**Layer 3 — Blocked packages:**
- `grep` for imports from blocked list
- Check for indirect dependencies that pull in blocked packages

**Layer 4 — Code standards:**
- Named exports, TypeScript strict, consistent naming
- Test co-location, file structure conventions

**Layer 5 — Performance:**
- Large component? Should it be lazy-loaded?
- Unnecessary re-renders? Missing memoization?
- Bundle size impact of new dependencies?

**Layer 6 — Anti-patterns:**
- Load `references/anti-patterns.md` for framework-specific checks
- Props drilling, stale closures, missing keys

### Step 3: Report with severity and fixes

## Output format

```markdown
# Review: [file or PR]
## Verdict: [approve/request-changes/block]
## Stats: [N] findings — [N] critical, [N] high, [N] medium, [N] low

### [CRITICAL] Blocked import — @mui/material
**File:** `src/components/Dialog.tsx:1`
**Issue:** Imports from blocked package. Contract requires system components.
**Fix:** `import { Dialog } from '@system/ui'`

### [HIGH] Hardcoded border-radius — Card.tsx:28
**File:** `src/components/Card.tsx:28`
**Code:** `borderRadius: '12px'`
**Should be:** `borderRadius: tokens.radius.lg`
**Why:** Hardcoded values won't update when tokens change

### [MEDIUM] Missing error state — UserForm.tsx
**Contract Dim 5:** requires error state
**Actual:** Only idle and loading states handled
**Fix:** Add error handling per contract behavior spec

## What's good
- Clean TypeScript types matching contract exactly
- Accessible keyboard navigation in the dropdown
- Good use of semantic tokens for dark mode support
```


## Knowledge references

| File | When to read |
|------|-------------|
| design-system/contracts/[name].contract.yaml | Always — check against contract |
| engineering/code-standards.md | Always |
| engineering/tech-stack.md | Check blocked packages |
| references/anti-patterns.md | Framework-specific checks |
| references/performance-budget.md | Performance reviews |
| meta/four-layer-strategy.summary.md | Design system code reviews |



## Integration with Vercel web-design-guidelines

When Vercel's web-design-guidelines skill is available, add a 7th
review layer:

**Layer 7 — Web interface guidelines (100+ rules):**
The guidelines cover areas that are easy to miss under time pressure:
- Proper ARIA attributes and semantic HTML
- Visible focus states on all interactive elements
- Labeled inputs (not placeholder-as-label)
- Touch target sizes (44px minimum)
- Reduced-motion support for all animations
- Proper heading hierarchy (no skipped levels)
- Keyboard navigation for all interactions

The guidelines are maintained by Vercel Engineering and fetch from
a live source, so rules stay current without manual updates.

To activate during review:
```
Review this code using our 6-layer process AND Vercel's web-design-guidelines
```
