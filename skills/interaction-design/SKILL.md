---
name: interaction-design
description: >
  Micro-animations, state machines, gesture design, transitions,
  feedback loops, error recovery flows, and loading patterns. Use
  when the user mentions interaction, animation, transition, state
  machine, gesture, feedback, loading state, error handling UX,
  or "how should this feel", "what happens when they tap", or
  "design the transition between states".
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
