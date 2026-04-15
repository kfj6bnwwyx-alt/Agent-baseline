# Pattern Schema

Patterns are multi-component compositions. They reference component
contracts by name and add composition-level rules that no single
component owns.

## Structure

```yaml
pattern: pattern-name                    # kebab-case identifier
description: "One-line purpose"
status: draft | stable | deprecated

# Which contracts this pattern composes
uses:
  - ComponentA
  - ComponentB(variant: specific)        # Can specify variant

# How the components relate
composition:
  trigger: "What initiates this pattern"
  flow:
    - "Step 1: what happens"
    - "Step 2: what happens"
  layout:
    direction: vertical | horizontal
    alignment: start | center | end
    spacing: spacing.token.reference

# State machine for the pattern (not individual components)
behavior:
  states: [state1, state2, state3]
  transitions:
    state1 → state2: "trigger"
    state2 → state3: "trigger"
  focus:
    on-open: "which element receives focus"
    on-close: "where focus returns"

# Accessibility for the composition
accessibility:
  role: "composite role if needed (e.g., alertdialog)"
  keyboard:
    escape: "pattern-level keyboard behavior"
  announcements: "what screen readers announce for the pattern"

# Composition-level rules (beyond individual component rules)
rules:
  do:
    - "Composition guidance"
  dont:
    - "Composition anti-patterns"

# Platform-specific notes for implementing this pattern
platform-notes:
  web-react: "Implementation approach"
  ios-swiftui: "Implementation approach"
```

## Relationship to contracts

Patterns REFERENCE contracts, they don't duplicate them.
- `uses: [Dialog, Button]` means: look up Dialog.contract.yaml and
  Button.contract.yaml for the component-level specs
- Pattern adds: HOW these components work TOGETHER
- If a pattern needs a component that doesn't have a contract yet,
  flag it — the contract should be created first

## When to create a pattern

Create a pattern when:
- 2+ components are used together repeatedly
- The composition has rules that don't belong to either component
- Multiple teams implement the same flow differently
- A composition has accessibility requirements beyond individual components

Don't create a pattern when:
- A single component handles the use case
- The composition is one-off (just document it in the feature spec)
- The components don't have contracts yet (create contracts first)
