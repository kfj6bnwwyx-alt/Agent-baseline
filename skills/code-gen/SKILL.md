---
name: code-gen
description: >
  Generate production code: component implementations, platform
  adapter code, and feature builds that conform to Layer 2 contracts.
  Use when the user says "implement this component in React",
  "generate the SwiftUI adapter", "build this from its contract",
  "create the Angular version", "write the component code", or
  any request to produce working code from a spec. Also triggers on
  "scaffold", "boilerplate", or framework-specific requests like
  "React version of" or "SwiftUI version of". Do NOT use for
  reviewing existing code (code-review) or writing tests (testing).
---

# Code Generation

You generate production-quality code that conforms to the design system.
Every component you produce consumes tokens from Layer 1 and implements
the API surface defined in Layer 2 contracts.

## Before writing any code

1. Load the relevant component contract(s)
2. Load the platform adapter guide for the target framework
3. Load the strategy summary (know which layer you're implementing)
4. Check blocked packages — never import anything on the blocked list

## Output standards

- All components consume design tokens (never hardcode values)
- Props match the contract exactly (types, defaults, required)
- Include error and loading states when contract specifies them
- Accessible by default per contract accessibility section
- Co-located test file with coverage of all variants


## Detailed process

### Step 1: Load the contract
Read the full 7-dimension contract for the component being built.
This is the spec you implement against — not a rough guide.

### Step 2: Load platform context
Read the platform adapter guide for the target framework.
Check tech-stack.md for blocked packages and conventions.

### Step 3: Scaffold the files
Create the file structure per platform convention:
```
[ComponentName]/
  [ComponentName].tsx         # Component implementation
  [ComponentName].test.tsx    # Contract + interaction tests
  [ComponentName].stories.tsx # Storybook stories (optional)
  index.ts                    # Named export
```

### Step 4: Implement all 7 dimensions
1. **API**: Define props interface matching contract exactly
2. **Visual**: Map every token reference to CSS/style values
3. **A11y**: Implement ARIA, keyboard, focus, screen reader
4. **Composition**: Slots, forwarded refs, accepted children
5. **Behavior**: All states, transitions, animation per spec
6. **Rules**: Enforce do/don't (prop validation, warnings)
7. **Platform**: Framework-specific patterns (ref forwarding, SSR, etc.)

### Step 5: Write co-located tests
Contract tests for every variant, state, and a11y requirement.

## Output format

Every generated component includes:

```typescript
// Button.tsx
import { tokens } from '@system/tokens';

interface ButtonProps {
  /** Visual treatment per contract Dimension 1 */
  variant?: 'primary' | 'secondary' | 'ghost' | 'destructive';
  /** Size per contract Dimension 1 */
  size?: 'sm' | 'md' | 'lg';
  /** Disables interaction per contract Dimension 5 */
  disabled?: boolean;
  /** Shows loading indicator per contract Dimension 5 */
  loading?: boolean;
  children: React.ReactNode;
}

export const Button = React.forwardRef<HTMLButtonElement, ButtonProps>(
  ({ variant = 'primary', size = 'md', disabled, loading, children, ...props }, ref) => {
    return (
      <button
        ref={ref}
        // Dimension 3: accessibility
        aria-disabled={disabled || loading || undefined}
        aria-busy={loading || undefined}
        // Dimension 2: visual tokens
        className={styles({ variant, size, disabled, loading })}
        // Dimension 5: behavior
        onClick={disabled || loading ? undefined : props.onClick}
        {...props}
      >
        {loading ? <Spinner /> : children}
      </button>
    );
  }
);
```

## Example: Generating from Button contract

Input: "Implement the Button component in React from its contract"

1. Load `button.contract.yaml`
2. Extract: 4 variants, 3 sizes, loading + disabled states
3. Generate typed props interface from Dimension 1
4. Map tokens from Dimension 2 to CSS custom properties
5. Implement keyboard handling from Dimension 3
6. Support children slot from Dimension 4
7. Implement all state transitions from Dimension 5
8. Add prop validation warnings for Dimension 6 rules
9. Forward ref per Dimension 7 platform notes
10. Write contract tests covering all variants and states


## Knowledge references

| File | When to read |
|------|-------------|
| design-system/contracts/[name].contract.yaml | Always — the spec you implement against |
| engineering/platform-adapters/[framework].md | Always — framework-specific patterns |
| meta/four-layer-strategy.summary.md | Always — layer context |
| engineering/code-standards.md | Always |
| engineering/tech-stack.md | First invocation per session |



## Integration with Superpowers TDD

When Superpowers is installed, code generation follows TDD enforcement:

### Modified process
1. Load the component contract (unchanged)
2. **Write failing tests FIRST** from the contract
   - Contract tests: each variant, each prop, each default
   - A11y tests: keyboard, ARIA, focus, screen reader
   - Interaction tests: state transitions from Dimension 5
3. Run tests — verify they fail (RED)
4. Implement the component to make tests pass (GREEN)
5. Refactor for code quality (REFACTOR)
6. Run design-system-audit quality gate

Superpowers enforces this order — it will reject code written before
tests exist. This ensures every component has contract coverage from
the start, not tests added after the fact.

### Two-stage review (from Superpowers)
After implementation:
1. **Spec compliance review**: Does the code match the contract?
2. **Code quality review**: Is the code clean, performant, idiomatic?

Both must pass before the component is considered complete.
