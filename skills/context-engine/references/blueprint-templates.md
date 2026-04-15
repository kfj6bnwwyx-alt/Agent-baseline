# Blueprint Templates

These are the YAML structure templates for each of the 7 context engine
blueprints. The context-engine generates these by aggregating data from
Layer 1 tokens and Layer 2 contracts.

Based on Murphy Trueman's context-engine-builder (design-system-ops).

## 1. UX Blueprint

```yaml
# ux-blueprint.yml
metadata:
  generated: [timestamp]
  source_contracts: [list of contracts used]
  coverage: [percentage]

patterns:
  [pattern-name]:
    trigger: "What initiates this pattern"
    components: [list from contract uses]
    states: [from pattern behavior.states]
    transitions:
      - from: [state]
        to: [state]
        on: "trigger"
    completion: "What defines success"
    errors: "What happens on failure"
    edge_cases:
      - empty_state: "behavior"
      - max_data: "behavior"

selection_rules:
  - intent: "When user needs to [goal]"
    use: [pattern-name]
    not: [alternative-pattern]
    reason: "Why this pattern fits better"

flows:
  [flow-name]:
    steps:
      - screen: [name]
        components: [from contracts]
        transitions: [to next screen]
    error_paths:
      - condition: [failure]
        handling: [what user sees]
```

## 2. UI Blueprint

```yaml
# ui-blueprint.yml
metadata:
  generated: [timestamp]
  token_files: [list]
  coverage: [percentage]

tokens:
  color:
    primitives: [from L1 tokens]
    semantics:
      [category]:
        [name]:
          value: [reference]
          usage: "When to use this token"
  spacing:
    scale: [from L1]
    usage_rules:
      - "Use spacing.2 (8px) for related element gaps"
      - "Use spacing.4 (16px) for section separation"
  typography:
    scale: [from L1]
    hierarchy:
      - level: display
        token: [reference]
        usage: "Page titles, hero text"
      - level: heading
        token: [reference]
        usage: "Section headers"

layout:
  grid:
    columns: [per breakpoint]
    gutters: [token reference]
    margins: [token reference]
  breakpoints:
    - name: sm
      value: 640px
      changes: [what adapts]

visual_rules:
  elevation:
    - level: 0
      shadow: none
      usage: "Flat surfaces"
    - level: 1
      shadow: [token]
      usage: "Cards, dropdowns"
  border_radius:
    - [scale with usage rules]
```

## 3. Content Blueprint

```yaml
# content-blueprint.yml
voice:
  attributes:
    - "Confident but not arrogant"
    - "Helpful but not patronizing"
  vocabulary:
    preferred:
      - term: "use"
        instead_of: "utilize"
    prohibited:
      - term: [jargon]
        reason: "Users don't understand this"

tone:
  contexts:
    success:
      mood: "warm, brief"
      example: "Saved" not "Changes saved successfully"
    error:
      mood: "clear, actionable"
      example: "Password too short. Use 8+ characters"
    empty:
      mood: "encouraging, guiding"
      example: "No projects yet. Create your first project"
    destructive:
      mood: "specific, honest"
      example: "Delete 'Q3 Report'? This can't be undone"

patterns:
  button_labels:
    format: "verb + noun"
    max_length: 3 words
    examples: ["Save changes", "Delete project", "Create account"]
  error_messages:
    format: "what happened + what to do"
    examples: ["Email not found. Check spelling or sign up"]
  empty_states:
    format: "what goes here + action"
    examples: ["No projects yet. Create your first project"]
```

## 4. Accessibility Blueprint

```yaml
# accessibility-blueprint.yml
component_contracts:
  [ComponentName]:
    role: [ARIA role]
    aria_required: [attributes]
    keyboard:
      [key]: [action]
    focus:
      on_open: [target]
      on_close: [return target]
    announcements:
      [state_change]: [announcement text]
    min_target: [size]

system_rules:
  focus_visible:
    style: "2px solid [token], 2px offset"
    applies_to: "all interactive elements"
  color_contrast:
    normal_text: "4.5:1 minimum"
    large_text: "3:1 minimum"
    ui_components: "3:1 minimum"
  motion:
    max_duration: "5 seconds for any animation"
    reduced_motion: "respect prefers-reduced-motion"
    essential_only: "animation must serve function, not decoration"

testing:
  automated: [axe-core rules that must pass]
  manual:
    - "Screen reader: full task completion"
    - "Keyboard: all interactions reachable"
    - "Zoom: 200% without content loss"
```

## 5. Ethical Blueprint

```yaml
# ethical-blueprint.yml
prohibitions:
  - pattern: "Manipulative urgency"
    rule: "No fake timers or false scarcity"
    bad_example: "'Only 2 left!' when stock is fine"
    good_example: "Show actual stock when relevant"
  - pattern: "Confirmshaming"
    rule: "Decline options use neutral language"
    bad_example: "'No thanks, I hate saving money'"
    good_example: "'No thanks' or 'Skip'"

inclusive_design:
  name_inputs:
    required: "Support non-Latin characters"
    prohibited: "No arbitrary length limits"
  gender:
    required: "Free-text or non-binary options"
    prohibited: "No forced binary selection"

data_privacy:
  consent:
    marketing: "opt-in only"
    analytics: "opt-in with clear purpose"
    essential: "can be opt-out with explanation"
```

## 6. Technical Blueprint

```yaml
# technical-blueprint.yml
component_contracts:
  [ComponentName]:
    props:
      [propName]:
        type: [TypeScript type]
        default: [value]
        required: [boolean]
    ref_forwarding: [required/optional]
    polymorphic: [as prop type if applicable]

composition:
  valid_children:
    [ParentComponent]: [allowed child types]
  context_dependencies:
    [Component]: [required providers]

performance:
  bundle_budgets:
    per_component: "10KB max gzipped"
    total_library: "200KB max gzipped"
  ssr: [requirements]
  lazy_loading: [which components]

integration:
  imports: "named exports, tree-shakeable"
  versioning: "semver, contract changes = major"
  overrides: "theme tokens via CSS custom properties"
```

## 7. Business Intelligence Blueprint

```yaml
# business-intelligence-blueprint.yml
component_outcomes:
  [ComponentName]:
    business_function: "conversion | engagement | retention | trust"
    primary_metric: [metric name]
    secondary_metrics: [list]
    anti_metrics:
      - metric: [name]
        reason: "Optimizing this would harm UX"

experimentation:
  safe: ["color", "copy", "size", "order"]
  requires_review: ["navigation", "form flow", "error handling"]
  never: ["accessibility features", "security indicators"]

analytics:
  required_events:
    - component: [name]
      event: "rendered"
      fields: [page, variant, position]
    - component: [name]
      event: "interacted"
      fields: [page, variant, action]

## Engine Manifest

```yaml
# engine-manifest.yml
version: "1.0"
generated: [timestamp]
blueprints:
  - name: ux
    file: ux-blueprint.yml
    coverage: [percentage]
  - name: ui
    file: ui-blueprint.yml
    coverage: [percentage]
  # ... all 7
total_coverage: [weighted average]
source_contracts: [count]
source_tokens: [count]
```
