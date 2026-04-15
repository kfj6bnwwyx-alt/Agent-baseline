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


## Detailed process

### Step 1: Inventory source artifacts
Read `_index.md` to get full contract catalog.
Read token files for L1 coverage.
Note which blueprints have sufficient source data to generate.

### Step 2: Generate each blueprint
For each of the 7 blueprints, compile from contracts:

**UX blueprint**: Aggregate Dimension 5 (behavior) across all contracts.
Extract interaction patterns, state machines, transition rules.

**UI blueprint**: Aggregate Dimension 2 (visual) + L1 tokens.
Token hierarchy, layout rules, responsive specs.

**Content blueprint**: Aggregate Dimension 6 (rules) for copy-related rules.
Voice attributes, tone modulation, content patterns, terminology.

**Accessibility blueprint**: Aggregate Dimension 3 across all contracts.
Per-component a11y contracts, system-level rules, testing protocols.

**Ethical blueprint**: Aggregate Dimension 6 prohibitions + ethical rules.
Dark pattern prohibitions, inclusive design, privacy patterns.

**Technical blueprint**: Aggregate Dimension 1 (API) + Dimension 7 (platform).
TypeScript interfaces, composition rules, performance constraints.

**BI blueprint**: Component-to-outcome mapping from product metrics.

### Step 3: Generate IDE context files
Compile blocked packages, import maps, replacement tables, code examples
into `.windsurfrules`, `.cursorrules`, `CLAUDE.md` formats.

### Step 4: Generate preview manifests
One JSON file per component with all 7 dimensions for any preview renderer.

### Step 5: Validate completeness
Every contract's component must appear in technical + a11y blueprints at minimum.

## Output format

```
.ai/context-engine/
  ux-blueprint.yml
  ui-blueprint.yml
  content-blueprint.yml
  accessibility-blueprint.yml
  ethical-blueprint.yml
  technical-blueprint.yml
  business-intelligence-blueprint.yml
  engine-manifest.yml
  usage-guide.md
```

## Example: UX blueprint structure

```yaml
# ux-blueprint.yml
patterns:
  destructive-confirmation:
    trigger: "User initiates destructive action"
    components: [Dialog, Button]
    states: [closed, open-idle, confirming, confirmed]
    transitions:
      - from: closed
        to: open-idle
        on: "destructive action initiated"
    rules:
      - "Confirm button is never default focus"
selection_rules:
  - intent: "User needs to confirm a destructive action"
    use: destructive-confirmation
    not: inline-undo
    reason: "Irreversible actions require explicit confirmation"
```


## Knowledge references

| File | When to read |
|------|-------------|
| meta/four-layer-strategy.md | Always — full architecture context needed |
| design-system/contracts/_index.md | Always — full catalog |
| design-system/tokens/_schema.md | Always |
| references/adapter-formats.md | Always — output format per tool |
