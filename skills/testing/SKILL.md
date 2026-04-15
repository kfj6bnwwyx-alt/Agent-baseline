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


## Detailed process

### Step 1: Load the contract
The contract IS the test spec. Every dimension is a test category.

### Step 2: Write contract tests (highest priority)
For each prop in Dimension 1:
- Default value renders correctly
- Each enum value renders a distinct variant
- Required props produce errors when missing
- Optional props work with and without values

### Step 3: Write accessibility tests
From Dimension 3:
- Correct ARIA role applied
- Keyboard interactions work (Enter, Space, Tab, Escape, Arrows)
- Focus management follows spec (focus trap, focus return)
- Screen reader announcements fire on state changes

### Step 4: Write interaction tests
From Dimension 5:
- Each state transition works with correct trigger
- Loading state disables interaction
- Error state shows correct feedback
- Animations respect prefers-reduced-motion

### Step 5: Write composition tests
From Dimension 4:
- Valid children render correctly
- Invalid children are handled gracefully
- Nesting within approved parents works

## Output format

```typescript
// Button.test.tsx
import { render, screen } from '@testing-library/react';
import userEvent from '@testing-library/user-event';
import { Button } from './Button';

describe('Button — Contract compliance', () => {
  // Dimension 1: API
  it('renders primary variant by default', () => {
    render(<Button>Click</Button>);
    expect(screen.getByRole('button')).toHaveClass('variant-primary');
  });

  it.each(['primary', 'secondary', 'ghost', 'destructive'] as const)(
    'renders %s variant',
    (variant) => {
      render(<Button variant={variant}>Click</Button>);
      expect(screen.getByRole('button')).toBeVisible();
    }
  );

  // Dimension 3: Accessibility  
  it('has minimum 44px touch target', () => {
    render(<Button>Click</Button>);
    const btn = screen.getByRole('button');
    expect(btn.offsetHeight).toBeGreaterThanOrEqual(44);
  });

  it('uses aria-disabled instead of disabled attribute', () => {
    render(<Button disabled>Click</Button>);
    expect(screen.getByRole('button')).toHaveAttribute('aria-disabled', 'true');
    expect(screen.getByRole('button')).not.toHaveAttribute('disabled');
  });

  // Dimension 5: Behavior
  it('shows loading indicator and disables interaction', async () => {
    const onClick = vi.fn();
    render(<Button loading onClick={onClick}>Click</Button>);
    await userEvent.click(screen.getByRole('button'));
    expect(onClick).not.toHaveBeenCalled();
    expect(screen.getByRole('button')).toHaveAttribute('aria-busy', 'true');
  });
});
```


## Knowledge references

| File | When to read |
|------|-------------|
| design-system/contracts/[name].contract.yaml | Always — test against the contract |
| references/test-templates.md | Test structure patterns |
| engineering/code-standards.md | Test naming and file conventions |
