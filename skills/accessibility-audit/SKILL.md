---
name: accessibility-audit
description: >
  WCAG 2.2 AA accessibility auditing, ARIA pattern validation,
  keyboard navigation testing, screen reader optimization, cognitive
  accessibility assessment, and inclusive design evaluation. Use when
  the user asks "is this accessible", "WCAG audit", "check ARIA
  attributes", "keyboard navigation for this component", "screen
  reader testing", "contrast ratio check", "cognitive load assessment",
  or "inclusive design review". Also triggers on "a11y", "assistive
  technology", or "focus management". Do NOT use for visual layout
  decisions (ui-design) or writing content (content-strategy).
---

# Accessibility Audit

You audit designs and implementations for WCAG 2.2 AA compliance and
provide remediation guidance.

Incorporates: designer-skills a11y patterns, inclusive-design-skills
(MC Dean) for cognitive accessibility, adaptive interfaces, and
inclusive research methods.


## Detailed process

### Step 1: Load the contract
Read the component's Dimension 3 (Accessibility) for the specific
requirements. This is the primary spec — WCAG supplements it.

### Step 2: Automated checks
If code is available, run or recommend:
- axe-core for ARIA, labels, landmarks, semantics
- Contrast ratio checks (4.5:1 normal text, 3:1 large/UI)
- Focus order validation
- Missing alt text scan

### Step 3: Manual verification
Things automation misses:
- Does the screen reader experience make sense narratively?
- Is keyboard navigation logical (not just possible)?
- Are state changes announced at the right time?
- Does reduced motion work (not just disabled)?
- Can you complete the task with keyboard alone?

### Step 4: Cognitive accessibility
From inclusive-design-skills:
- Is the language plain enough? (target 8th grade)
- Is there too much on screen? (cognitive load)
- Are there sensible defaults? (reduce required decisions)
- Is the flow predictable? (no surprise context changes)

### Step 5: Report with severity
Weight severity by impact: a complete blocker for one person
outweighs mild annoyance for many.

## Output format

```markdown
# Accessibility audit: [component/flow]
## Result: [pass/conditional pass/fail]
## WCAG level: targeting AA

### [CRITICAL] Missing keyboard access — Dropdown.tsx
**WCAG:** 2.1.1 Keyboard
**Contract Dim 3 says:** keyboard.arrow-keys: navigates options
**Actual:** Arrow keys do nothing, only mouse works
**Impact:** Keyboard-only users cannot use this component at all
**Fix:** Add onKeyDown handler for ArrowUp/ArrowDown/Enter/Escape
**Test:** Tab to dropdown, press ArrowDown — options should cycle

### [HIGH] Contrast failure — Label on warning background
**WCAG:** 1.4.3 Contrast Minimum
**Ratio:** 2.8:1 (needs 4.5:1)
**Fix:** Use `text.on-warning` token instead of `text.secondary`

### [MEDIUM] Missing announce on async load
**WCAG:** 4.1.3 Status Messages
**Contract Dim 3 says:** screen-reader.loading: "announces Loading"
**Actual:** Loading state is visual only
**Fix:** Add aria-live="polite" region with "Loading..." text
```

## Example: Form audit

Input: "Is this registration form accessible?"

Check against form-related WCAG criteria:
1. Every input has a visible `<label>` with `htmlFor` (not placeholder-only)
2. Required fields marked with `aria-required` and visible indicator
3. Error messages linked via `aria-describedby`
4. Error messages say what's wrong AND how to fix it
5. Form doesn't clear on error (preserve user input)
6. Submit button has descriptive label ("Create account" not "Submit")
7. Tab order follows visual order
8. Success/error outcomes announced to screen readers


## Knowledge references

| File | When to read |
|------|-------------|
| accessibility/wcag-checklist.summary.md | Quick checks, non-deep audits |
| accessibility/wcag-checklist.md | Full audits only |
| accessibility/aria-patterns.md | When reviewing ARIA usage |
| accessibility/cognitive-load.md | Cognitive a11y concerns |
| accessibility/plain-language.md | Content accessibility |
| design-system/contracts/[name].contract.yaml | Checking component a11y reqs |
