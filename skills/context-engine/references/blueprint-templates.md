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



## Additions: UX Blueprint — Named Flow Categories

Add these under the `flows:` key in the UX blueprint:

```yaml
flows:
  authentication:
    type: "multi-step"
    steps:
      - screen: login
        components: [TextField, Button, Link]
        transitions: {success: dashboard, failure: error_state}
      - screen: registration
        components: [TextField, Button, Checkbox, Link]
        transitions: {success: verification, failure: error_state}
      - screen: password_reset
        components: [TextField, Button]
        transitions: {success: confirmation, failure: error_state}
      - screen: session_expired
        components: [Dialog, Button]
        transitions: {reauth: login, cancel: logout}
    error_paths:
      - condition: "invalid credentials"
        handling: "inline error, preserve input, suggest reset"
      - condition: "account locked"
        handling: "specific message with unlock timeframe"

  data_entry:
    type: "progressive"
    patterns:
      - single_field: "inline validation on blur"
      - multi_field_form: "validate per field, summary on submit"
      - multi_step_wizard: "progress indicator, save draft, back navigation"
      - bulk_edit: "inline editing with batch save"
    validation_timing:
      - on_blur: "format validation"
      - on_submit: "required fields, cross-field validation"
      - real_time: "character count, password strength only"

  navigation:
    patterns:
      - global_nav: "persistent, max 7 top-level items"
      - local_nav: "contextual to section, collapses on mobile"
      - breadcrumbs: "show path for >2 levels deep"
      - deep_linking: "every view has a shareable URL"
      - back_navigation: "browser back always works predictably"
    wayfinding:
      - "current location always visible"
      - "path to any section ≤3 clicks from home"

  feedback:
    patterns:
      - success: {component: Toast, duration: "3s auto-dismiss", position: "top-right"}
      - error: {component: "inline or Banner", duration: "persistent until resolved", position: "adjacent to cause"}
      - warning: {component: Banner, duration: "persistent until dismissed", position: "top of relevant section"}
      - info: {component: Toast, duration: "5s auto-dismiss", position: "top-right"}
      - progress: {component: "ProgressBar or Skeleton", duration: "until complete", position: "replacing content"}
```

## Additions: Content Blueprint — Terminology Glossary

Add under a `terminology:` key:

```yaml
terminology:
  glossary:
    - term: "[domain term]"
      definition: "[plain language definition]"
      context: "[where this term appears in the UI]"
      aliases: ["[other names users might use]"]
      do_not_confuse_with: "[similar term with different meaning]"

  disambiguation:
    - term: "account"
      contexts:
        - context: "billing"
          meaning: "payment and subscription management"
        - context: "auth"
          meaning: "user identity and credentials"
      guidance: "Always qualify: 'billing account' or 'user account'"

  abbreviations:
    acceptable: ["URL", "PDF", "API", "FAQ"]
    spell_out_first_use: ["SSO (single sign-on)", "MFA (multi-factor auth)"]
    never_abbreviate: ["information (not 'info')", "application (not 'app' in formal contexts)"]
```

## Additions: Accessibility Blueprint — AT Matrix + Dark Mode Contrast

```yaml
assistive_technology:
  support_matrix:
    screen_readers:
      - name: "VoiceOver"
        platforms: ["macOS Safari", "iOS Safari"]
        priority: "must pass"
      - name: "NVDA"
        platforms: ["Windows Chrome", "Windows Firefox"]
        priority: "must pass"
      - name: "JAWS"
        platforms: ["Windows Chrome"]
        priority: "should pass"
      - name: "TalkBack"
        platforms: ["Android Chrome"]
        priority: "must pass"
    testing_cadence: "every component release"
    baseline: "task completion with screen reader only (no sighted assistance)"

  dark_mode_contrast:
    rules:
      - "All AA contrast ratios must be met in BOTH light and dark modes"
      - "Test with actual dark mode tokens, not inverted light mode"
      - "Semantic color tokens must resolve to AA-passing values in both modes"
      - "Focus indicators must be visible on dark backgrounds (use outline, not box-shadow)"
      - "Elevation via lightness (not shadow) in dark mode — test contrast of stacked surfaces"
    testing: "run contrast checks in both modes during every a11y audit"
```

## Additions: Ethical Blueprint — Bias Detection

```yaml
bias_detection:
  signals:
    narrowing_personalization:
      pattern: "Recommendations that reduce variety over time"
      test: "Does a new user see more options than a returning user?"
      rule: "Personalization must expand discovery, not create filter bubbles"
      example_bad: "Only showing content similar to past clicks"
      example_good: "Mix of personalized + serendipitous discovery"

    default_bias:
      pattern: "Defaults that favor business over user"
      test: "Would the user choose this default if presented all options equally?"
      rule: "Defaults must serve user convenience, not business conversion"
      example_bad: "Newsletter opt-in pre-checked"
      example_good: "Newsletter opt-in unchecked, clear value proposition"

    asymmetric_effort:
      pattern: "Easy to add, hard to remove"
      test: "Count steps to add vs remove. Ratio should be ≤1.5:1"
      rule: "Removal must be as easy as addition"
      example_bad: "1-click subscribe, 5-step unsubscribe"
      example_good: "Subscribe/unsubscribe in same location, same steps"

    anchoring:
      pattern: "Price or option positioning that steers choice"
      test: "Remove the 'decoy' option — does the preferred choice change?"
      rule: "Options must be presented for comparison, not manipulation"
      example_bad: "Expensive option shown first to make middle seem reasonable"
      example_good: "Options ordered by feature set, not by margin"

  audit_frequency: "quarterly, or when adding pricing, personalization, or notification features"
```

## Additions: Technical Blueprint — Event Signatures + Patterns

```yaml
  event_handlers:
    [ComponentName]:
      [handlerName]:
        signature: "(event: [EventType], data: [DataType]) => void"
        required: [boolean]
        bubbles: [boolean]
        description: "When this fires and what data it carries"

  controlled_vs_uncontrolled:
    pattern: "Support both via value/defaultValue convention"
    rules:
      - "If `value` prop is provided: component is controlled"
      - "If `defaultValue` prop is provided: component is uncontrolled"
      - "Never provide both — log a warning if consumer does"
      - "onChange fires in both modes with the same signature"
    components:
      TextField: {controlled: "value + onChange", uncontrolled: "defaultValue"}
      Checkbox: {controlled: "checked + onChange", uncontrolled: "defaultChecked"}
      Select: {controlled: "value + onChange", uncontrolled: "defaultValue"}

  polymorphic:
    pattern: "as prop for render-as-different-element"
    type: "<C extends React.ElementType = 'button'>"
    rules:
      - "Default element type matches semantic purpose (button for Button)"
      - "Props extend the target element's native props"
      - "Ref type matches the target element"
    example: |
      <Button as="a" href="/next">Continue</Button>
      // Renders <a> with Button styling, href is type-safe
```

## Additions: BI Blueprint — Usage Analytics + Performance

```yaml
  usage_analytics:
    component_render_frequency:
      event: "component_rendered"
      fields: [component_name, page, variant, viewport_size]
      purpose: "Which components are most/least used"
      threshold: "Alert if core component usage drops >20% week-over-week"

    interaction_rates:
      event: "component_interacted"
      fields: [component_name, action_type, page, time_to_interact]
      purpose: "Which interactive components are engaged with"

    error_rates:
      event: "component_error"
      fields: [component_name, error_type, page, user_action_before]
      purpose: "Which components generate the most user errors"
      threshold: "Alert if error rate >5% for any component"

    performance_impact:
      metrics:
        - component_render_time: "Time from mount to painted (ms)"
        - component_bundle_size: "JS size per component (KB gzipped)"
        - component_cls_contribution: "CLS caused by this component"
      threshold: "Alert if render_time >100ms or CLS >0.05"
      measurement: "RUM data, sampled in production"

  ## UI Blueprint — Responsive Behavior Detail

  responsive_rules:
    approach: "mobile-first, enhance for larger"
    breakpoints:
      sm: {value: "640px", description: "Large phone / small tablet"}
      md: {value: "768px", description: "Tablet portrait"}
      lg: {value: "1024px", description: "Tablet landscape / small desktop"}
      xl: {value: "1280px", description: "Desktop"}
    component_adaptations:
      Dialog: "Full-screen below md, centered modal above"
      Navigation: "Bottom tabs below md, side nav above"
      DataTable: "Card list below md, table above"
      Form: "Single column below md, multi-column above lg"
    token_changes:
      spacing: "Reduce by one scale step below md"
      typography: "Reduce display sizes by ~20% below md"
      touch_targets: "Minimum 44px always, 48px on mobile"
```
