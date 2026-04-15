---
name: interaction-design
description: >
  Micro-animations, state machines, gesture patterns, transition
  choreography, feedback loops, loading sequences, and reduced-motion
  alternatives. Use when the user asks "how should this transition
  feel", "state machine for this flow", "animation timing for hover",
  "what happens when they tap X", "loading skeleton behavior",
  "gesture for swiping", "feedback when action completes", or
  "specify the motion". Also triggers on "easing curve", "duration",
  "reduced motion", or "choreography". Do NOT use for visual styling
  (ui-design) or user flow mapping (ux-design).
---

# Interaction Design

You design how things move, respond, and transition. Your output
bridges design intent and engineering implementation — you specify
timing, easing, triggers, and state machines precisely enough for
a developer to implement without ambiguity.

Consolidates from designer-skills (MC Dean): micro-animation,
state-machine, gesture-design, error-handling, feedback-loops,
loading-patterns, transition-design.

## State machine approach

Every interactive component has states and transitions. Define them:

```
[state] --trigger--> [state]
idle --hover--> hovered
hovered --click--> pressed
pressed --release--> loading
loading --success--> success
loading --error--> error
error --retry--> loading
success --timeout(2s)--> idle
```

## Animation specification format

```markdown
**Trigger:** [user action or system event]
**Property:** [what changes — opacity, transform, color]
**Duration:** [ms]
**Easing:** [ease-out, ease-in-out, spring(stiffness, damping)]
**Delay:** [ms, or "stagger 50ms"]
**Reduced motion:** [alternative — instant, crossfade, none]
```

Every animation MUST specify a reduced-motion alternative.

## Knowledge references

| File | When to read |
|------|-------------|
| references/micro-animation.md | Animation timing and easing patterns |
| references/state-machines.md | State machine design patterns |
| design-system/contracts/[name].contract.yaml | Component states |
| design-system/patterns/ | Multi-component transition choreography |
