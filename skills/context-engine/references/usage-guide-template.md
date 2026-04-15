# Usage Guide Template

The context engine generates this file alongside the blueprints.
It teaches AI agents how to consume the engine.

```markdown
# Context Engine Usage Guide

## Loading the engine

On task start, load ONLY the blueprints relevant to your task type:

| Task type | Load these blueprints |
|-----------|---------------------|
| Code generation | Technical + UI + Accessibility |
| Code review | Technical + Accessibility + Ethical |
| Visual design | UI + Content |
| Interaction design | UX + UI + Accessibility |
| Content writing | Content + UX + Ethical |
| Accessibility audit | Accessibility + UX + Ethical |
| Full component build | All except BI (unless metrics needed) |
| Business analysis | BI + Technical |

## Query patterns per blueprint

### UX blueprint
- "What pattern should I use for [user intent]?" → check selection_rules
- "What states does [pattern] have?" → check patterns.[name].states
- "What's the error handling for [flow]?" → check flows.[name].error_paths

### UI blueprint  
- "What token for [visual property]?" → check tokens.[category]
- "What changes at [breakpoint]?" → check layout.breakpoints
- "What elevation for [component type]?" → check visual_rules.elevation

### Content blueprint
- "What tone for [context]?" → check tone.contexts.[context]
- "What's our word for [concept]?" → check terminology.glossary
- "Button label pattern?" → check patterns.button_labels

### Accessibility blueprint
- "ARIA for [component]?" → check component_contracts.[name]
- "Keyboard pattern for [component]?" → check component_contracts.[name].keyboard
- "What to test?" → check testing.automated + testing.manual

### Ethical blueprint
- "Is this a dark pattern?" → check prohibitions
- "Gender input rules?" → check inclusive_design.gender
- "Consent required for [data type]?" → check data_privacy.consent

### Technical blueprint
- "Props for [component]?" → check component_contracts.[name].props
- "Can [A] contain [B]?" → check composition.valid_children
- "Bundle budget?" → check performance.bundle_budgets

### BI blueprint
- "What metric for [component]?" → check component_outcomes.[name]
- "Can we A/B test [property]?" → check experimentation
- "What events to track?" → check analytics.required_events

## Never load all blueprints simultaneously
Total engine size is 20-38K tokens. Loading everything wastes context
on irrelevant knowledge. Use the task-type table above.
```
