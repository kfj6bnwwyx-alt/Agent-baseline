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


## Detailed process

### Step 1: Identify the interaction
What triggers it? What's the user's expectation?
What feedback do they need?

### Step 2: Define the state machine
List all states. Draw every transition with trigger and guard conditions.
Include error states and recovery paths.

### Step 3: Specify timing
For each transition that has motion:
- Duration (ms)
- Easing function
- Affected properties (transform, opacity only — never width/height)
- Reduced-motion alternative (instant cut or crossfade)

### Step 4: Choreography (multi-element)
If multiple elements animate together:
- Define the sequence (stagger timing)
- Which element leads, which follows
- Maximum total duration for the full choreography

### Step 5: Document for implementation
Output must be precise enough that a developer implements it
without asking questions about timing or behavior.

## Output format

```markdown
# Interaction spec: [component/flow]

## State machine
```
States: idle, hover, focus, active, loading, success, error
Initial: idle

idle → hover     [mouse-enter]
idle → focus     [tab / programmatic focus]
hover → active   [mouse-down]
active → loading [async operation triggered]
loading → success [complete, data.ok]
loading → error   [complete, !data.ok]
success → idle    [timeout 2s]
error → idle      [dismiss or retry]
```

## Animation specs

### hover → active
| Property | From | To | Duration | Easing |
|----------|------|----|----------|--------|
| transform | scale(1) | scale(0.97) | 100ms | ease-out |
| background | token.bg | token.bg-active | 100ms | ease-out |
**Reduced motion:** Instant background change, no transform

### idle → loading
| Property | From | To | Duration | Easing |
|----------|------|----|----------|--------|
| content opacity | 1 | 0 | 150ms | ease-out |
| spinner opacity | 0 | 1 | 150ms | ease-in (stagger 100ms) |
| spinner rotation | 0deg | 360deg | 800ms | linear (loop) |
**Reduced motion:** Hide content instantly, show static spinner (no rotation)

## Choreography: Toast notification entry
1. Translate from right: 0ms start, 250ms duration, ease-out
2. Fade in: 0ms start, 200ms duration, ease-out
3. Progress bar shrink: 300ms start, 5000ms duration, linear
4. Auto-dismiss: fade out at 5000ms, 200ms duration, ease-in
**Reduced motion:** Instant appear, instant dismiss after 5s
```

## Example: File upload flow

Input: "Specify the interaction for a drag-and-drop file upload"

```
States: idle, drag-over, uploading, progress, success, error

idle → drag-over    [file dragged over zone]
drag-over → idle    [file dragged out without drop]
drag-over → uploading [file dropped]
uploading → progress  [upload started, progress events]
progress → success    [upload complete]
progress → error      [upload failed]
error → idle          [dismiss error]
success → idle        [timeout 3s or dismiss]

Animation: drag-over
- Border: dashed → solid, 150ms ease-out
- Background: transparent → surface.info at 10% opacity, 150ms
- Scale: 1 → 1.01, 200ms ease-out
Reduced motion: border change only, no scale
```


## Knowledge references

| File | When to read |
|------|-------------|
| references/micro-animation.md | Animation timing and easing patterns |
| references/state-machines.md | State machine design patterns |
| design-system/contracts/[name].contract.yaml | Component states |
| design-system/patterns/ | Multi-component transition choreography |
