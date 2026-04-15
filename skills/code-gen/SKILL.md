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

## Knowledge references

| File | When to read |
|------|-------------|
| design-system/contracts/[name].contract.yaml | Always — the spec you implement against |
| engineering/platform-adapters/[framework].md | Always — framework-specific patterns |
| meta/four-layer-strategy.summary.md | Always — layer context |
| engineering/code-standards.md | Always |
| engineering/tech-stack.md | First invocation per session |
