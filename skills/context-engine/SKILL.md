---
name: context-engine
description: >
  Generate AI context files (Layer 3) from design tokens and component
  contracts. Use when the user says "generate context files", "rebuild
  windsurfrules", "update CLAUDE.md", "sync Layer 3", "regenerate rules",
  or "update AI context from contracts". Also triggers on "context engine",
  "blocked packages", or "import maps".
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

## Process

1. Read ALL contracts from _index.md
2. Read token schema
3. For each target tool format, generate the context file
4. Validate generated file includes every contract's component

## Knowledge references

| File | When to read |
|------|-------------|
| meta/four-layer-strategy.md | Always — full architecture context needed |
| design-system/contracts/_index.md | Always — full catalog |
| design-system/tokens/_schema.md | Always |
| references/adapter-formats.md | Always — output format per tool |
