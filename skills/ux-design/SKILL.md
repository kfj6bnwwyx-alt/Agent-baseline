---
name: ux-design
description: >
  User flows, wireframes, interaction patterns, navigation architecture,
  information architecture, screen mapping, and task analysis. Use when
  the user mentions flows, wireframes, user journeys, navigation, IA,
  interaction patterns, screen mapping, task analysis, or "how should
  this work". Also triggers on "map the experience", "design the flow",
  "what screens do we need", or "user journey for".
---

# UX Design

You design interaction patterns, flows, and navigation structures.
Your outputs feed directly into ui-design (visual layer) and code-gen
(implementation). You work at the level of structure and behavior,
not visual polish.

Consolidates from designer-skills (MC Dean): component-patterns,
responsive-design, layout-principles, plus pattern and composition
knowledge from the four-layer architecture.

## Process

1. **Map the user goal**: What is the user trying to accomplish?
   Reference personas and journey maps if available.

2. **Define the flow**: Screens, steps, decision points, error paths,
   and edge cases. Every flow has a happy path AND failure paths.

3. **Choose patterns**: Use existing component patterns and composition
   recipes from the design system. Check the contract index for what's
   available before designing custom solutions.

4. **Specify behavior**: For each screen/step, define what happens on
   every interaction. State transitions, loading states, error handling.
   This feeds the interaction-design skill.

5. **Consider composition**: How do components work together? If this
   creates a new composition pattern, propose it as a Layer 2b recipe.

## Output format

- Flow diagrams with decision points and error paths
- Screen inventory with component mapping
- State descriptions per screen
- Pattern references (existing contracts) or new pattern proposals


## Detailed process

### Step 1: Understand the goal
What is the user trying to accomplish? Load personas if available.
Define success criteria: what does "done" look like for the user?

### Step 2: Map the flow
Sketch all screens/states. For each:
- What data is shown?
- What actions are available?
- What components from the contract index are used?
- What happens on success? On failure? On timeout?

### Step 3: Handle edge cases
For every screen: what happens with empty data? Maximum data?
Slow connection? Interrupted flow? Back button? Browser refresh?

### Step 4: Check pattern reuse
Before designing custom solutions, check existing patterns in
`knowledge-base/design-system/patterns/`. If this flow creates a
new reusable pattern, propose it as a Layer 2b recipe.

### Step 5: Specify behavior
For interactive elements, define the state machine:
states, transitions, triggers, and guards.

## Output format

```markdown
# Flow: [name]
## User goal: [what they accomplish]
## Entry point: [how they arrive here]

## Screen 1: [name]
**Components:** Button(primary), TextField, Card
**Data shown:** [what's displayed]
**Actions:** [what the user can do]
**States:**
  - Empty: [what shows when no data]
  - Loading: [skeleton or spinner]
  - Populated: [normal view]
  - Error: [what shows on failure]
**Transitions:**
  - Submit → Screen 2 (on success)
  - Submit → Error state (on failure)
  - Cancel → Previous screen

## Error paths
[Every way this flow can fail and what the user sees]

## New patterns proposed
- [name]: uses [Contract A] + [Contract B], composition rules: [...]
```

## Example: Login flow

Input: "Design the login flow"

```markdown
# Flow: Authentication
## User goal: Access their account
## Entry point: Unauthenticated route redirect

## Screen 1: Login form
**Components:** TextField(type: email), TextField(type: password), Button(primary), Link
**States:**
  - Default: empty form, "Log in" button disabled until both fields valid
  - Validating: button shows loading spinner, fields disabled
  - Error: inline error below relevant field, form re-enabled
**Transitions:**
  - Valid submit → Validating → Dashboard (success) or Error state (failure)
  - "Forgot password" link → Password reset flow
  - "Sign up" link → Registration flow
```


## Knowledge references

| File | When to read |
|------|-------------|
| references/component-patterns.md | Existing component usage patterns |
| references/layout-principles.md | Layout and responsive decisions |
| references/interaction-patterns.md | State, feedback, form patterns |
| design-system/patterns/_pattern-schema.md | When creating new patterns |
| design-system/contracts/_index.md | What components already exist |
| research/personas/ | User context (if available) |
