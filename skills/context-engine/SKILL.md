---
name: context-engine
description: >
  Generate the seven context engine blueprints (UX, UI, content,
  accessibility, ethical, technical, business intelligence) and AI
  context files (.windsurfrules, .cursorrules, CLAUDE.md) from Layer 1
  tokens and Layer 2 contracts. Use when the user says "generate
  context files", "rebuild windsurfrules", "build the blueprints",
  "update CLAUDE.md from contracts", "sync Layer 3", "regenerate
  blocked package list", "update import maps", or "build the context
  engine". Do NOT use for extracting from Figma (metadata-extraction)
  or auditing health (design-system-audit).
---

# Context Engine

You generate Layer 3 AI context files from Layer 1 tokens and Layer 2 contracts.
These files are injected into AI coding tools to prevent drift to off-system packages.

Adapted from design-system-ops (Murphy Trueman): context-engine-builder.

## What you generate

For each target tool:
- **Blocked package list**: MUI, Chakra, shadcn → your system's replacement
- **Component → import lookup table**: Maps component names to correct imports
- **Replacement map**: MUI component → your system equivalent
- **Canonical code examples**: One correct usage example per component
- **Token usage rules**: How to reference tokens in code

For each component (NEW):
- **Preview manifest**: JSON file with all 7 contract dimensions
  structured for any preview renderer to consume. This is the bridge
  between the permanent contract and whatever rendering platform exists
  today. When Figma or Storybook or whatever-comes-next needs to show
  a component preview, it reads this manifest.

## Process

1. Read ALL contracts from _index.md
2. Read token schema
3. For each target tool format, generate the context file
4. For each component contract, generate a preview manifest JSON
   containing all 7 dimensions structured for rendering
5. Validate generated files include every contract's component
6. Validate every preview manifest covers all 7 dimensions

## Knowledge references

| File | When to read |
|------|-------------|
| meta/four-layer-strategy.md | Always — full architecture context needed |
| design-system/contracts/_index.md | Always — full catalog |
| design-system/tokens/_schema.md | Always |
| references/adapter-formats.md | Always — output format per tool |
