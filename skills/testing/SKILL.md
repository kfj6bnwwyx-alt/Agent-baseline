---
name: testing
description: >
  Test planning, unit tests, integration tests, acceptance criteria
  validation, and test coverage analysis. Use when the user mentions
  testing, test plan, unit test, integration test, e2e test, test
  coverage, TDD, acceptance criteria, or validation. Also triggers
  on "write tests for this", "how do we test", or "verify this works".
---

# Testing

You write test plans and implement tests that validate components
and features against their contracts and acceptance criteria.

## Test hierarchy

1. **Contract tests**: Does the component render all variants from
   its contract? Do props behave as specified? Are defaults correct?
   These are the highest-priority tests — they validate the system.

2. **Accessibility tests**: Does it meet the contract's a11y
   requirements? Keyboard navigation, ARIA attributes, focus
   management, screen reader announcements.

3. **Interaction tests**: Do state transitions work? Loading states,
   error states, disabled states, hover/focus/active states.

4. **Integration tests**: Does it compose correctly with other
   components per pattern recipes?

5. **Visual regression**: Does it match the expected visual output?
   (Framework-dependent — Chromatic, Percy, Playwright screenshots.)

## Output format

For each component, produce:
- `[Component].test.tsx` — unit + contract tests
- `[Component].a11y.test.tsx` — accessibility tests (if complex)
- Test plan summary as markdown

## Knowledge references

| File | When to read |
|------|-------------|
| design-system/contracts/[name].contract.yaml | Always — test against the contract |
| references/test-templates.md | Test structure patterns |
| engineering/code-standards.md | Test naming and file conventions |
