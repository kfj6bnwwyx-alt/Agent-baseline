# Four-Layer AI-Native Design System Strategy

## The situation

Everything in the stack is unstable. LLMs will change. Design tools will change. Web standards and platforms like Angular and React will change. The only thing you can control is the knowledge layer — the contracts, tokens, and patterns that describe your system's intent independent of any implementation.

## The drift problem

AI coding tools default to what they were trained on: Material UI, shadcn, Chakra. Without explicit constraints in every prompt window, generated code drifts to these defaults regardless of your design system. Static documentation can't prevent this because documentation isn't in the AI's context at inference time.

## Five principles

1. **Machine-readable over human-readable.** YAML contracts and DTCG tokens are parseable by any tool.
2. **Contracts before components.** Define the spec first. Implementations are consumers.
3. **Context injection at inference.** Put the right answer in every AI prompt window.
4. **Automated governance over manual review.** Drift detection, token validation, parity checking.
5. **Federated ownership, centralized standards.** DS team owns contracts. Platform teams own adapters.

## Architecture

### Layer 1: Design Tokens (DTCG)
Machine-readable primitives and semantics in W3C DTCG format. Compiled by Style Dictionary to CSS, SCSS, Swift, Android, Tailwind. These are the atomic values.

Example:
```json
{
  "color": {
    "action": {
      "primary": {
        "$value": "{color.indigo.600}",
        "$type": "color",
        "$description": "Primary action background"
      }
    }
  }
}
```

### Layer 2: Component Contracts
Platform-agnostic YAML spec per component. This is where design opinion lives.

```yaml
component: Button
props:
  variant: { type: enum, values: [primary, secondary, ghost, destructive], default: primary }
  size: { type: enum, values: [sm, md, lg], default: md }
  disabled: { type: boolean, default: false }
  loading: { type: boolean, default: false }
tokens:
  background: action.primary.bg
  text: action.primary.text
  border-radius: radius.md
accessibility:
  role: button
  min-target: 44px
  focus-visible: required
rules:
  do:
    - "Use primary for single main action per view"
    - "Include loading state for async operations"
  dont:
    - "Never use more than one primary button per section"
    - "Never disable without visible explanation"
```

### Layer 2b: Composition Patterns
Multi-component recipes referencing contracts by name:

```yaml
pattern: destructive-confirmation
uses: [Dialog, Button]
composition:
  - Dialog with descriptive body explaining consequences
  - Button(variant: destructive) as confirm action
  - Button(variant: ghost) as cancel action
rules:
  - Confirm button is NEVER the default focus
  - Body text must name the specific item being destroyed
```

### Layer 3: AI Context Files
Generated from L1+L2, tailored per tool. Contains blocked packages, import maps, replacement tables, code examples. This is the delivery mechanism.

### Layer 4: Platform Adapters
Thin, disposable implementations. React, Angular, SwiftUI. Owned by platform teams. Conform to L2 contracts. When you swap frameworks, only L4 rewrites.

## Governance
- Automated drift detection (design-system-ops)
- Token validation against DTCG schema
- Component parity checking (Figma Console MCP)
- Health dashboards with severity scoring

## Metrics
1. AI compliance rate (% of generated code using system components)
2. Token coverage (% of UI values mapped to tokens)
3. Contract coverage (% of components with YAML contracts)
4. Drift velocity (new off-system references per sprint)
5. Context file freshness (days since last L3 regeneration)
