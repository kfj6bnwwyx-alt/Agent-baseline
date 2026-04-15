---
name: code-review
description: >
  Review code for quality, consistency, and design system compliance.
  Use when the user mentions code review, PR review, pull request,
  refactoring, anti-patterns, code quality, linting, or asks to check
  code against standards. Also triggers on "review this", "is this
  code good", "what's wrong with this", or "clean this up". Do NOT
  use for writing new code — that's code-gen.
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

## Knowledge references

| File | When to read |
|------|-------------|
| design-system/contracts/[name].contract.yaml | Always — check against contract |
| engineering/code-standards.md | Always |
| engineering/tech-stack.md | Check blocked packages |
| references/anti-patterns.md | Framework-specific checks |
| references/performance-budget.md | Performance reviews |
| meta/four-layer-strategy.summary.md | Design system code reviews |
