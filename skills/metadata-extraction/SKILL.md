---
name: metadata-extraction
description: >
  Extract component metadata and design tokens from Figma using
  Figma Console MCP. Pull component specs, variant structures,
  token definitions, and layer hierarchies, then transform into
  Layer 1 DTCG tokens and Layer 2 YAML contracts. Use when the
  user says "pull from Figma", "extract component specs", "sync
  tokens from Figma", "update contracts from Figma library", or
  "get metadata via Console MCP". Also triggers on "Figma extraction",
  "figma_get_component", or "figma_get_variables". Do NOT use for
  generating context files from contracts (context-engine) or
  generating implementation code (code-gen).
---

# Metadata Extraction

You extract structured component metadata from Figma and transform it into
the four-layer architecture artifacts: DTCG tokens and YAML contracts.

## Pipeline

1. **Extract** via Figma Console MCP:
   - `figma_get_design_system_kit` for full system
   - `figma_get_component` for individual components
   - `figma_get_variables` for tokens/variables

2. **Transform** extracted data into:
   - `component-name.metadata.json` (intermediate format)
   - `component-name.contract.yaml` (Layer 2 contract)
   - Token updates to DTCG JSON (Layer 1)

3. **Validate** output against schemas:
   - Contract must conform to _contract-schema.md
   - Tokens must conform to _schema.md

4. **Update** manifest tracking coverage


## Detailed process

### Step 1: Connect and assess
Verify Figma Console MCP connection. Determine scope:
- Full system extraction: `figma_get_design_system_kit`
- Single component: `figma_get_component` with component key
- Tokens only: `figma_get_variables`

### Step 2: Extract raw data
Pull component metadata including:
- Component name, description, variant structure
- Property definitions (type, default, options)
- Token/variable references
- Layer hierarchy and auto-layout specs
- Accessibility annotations if present

### Step 3: Transform to contract YAML
Map extracted data to the 7-dimension contract schema:
- Figma properties → Dimension 1 (API/props)
- Figma variables/tokens → Dimension 2 (visual)
- Figma a11y annotations → Dimension 3 (accessibility)
- Figma layer hierarchy → Dimension 4 (composition)
- Figma interaction specs → Dimension 5 (behavior)
- Fill gaps with TODO markers for human review

### Step 4: Validate and output
Check generated contract against `_contract-schema.md`.
Update `_index.md` with new/updated component entry.

## Output format

For each component extracted:
```yaml
# [component].contract.yaml — generated from Figma [date]
# Source: [Figma file URL]
# Coverage: [which dimensions were auto-populated vs TODO]

component: TextField
category: input
description: "Single-line text input with label and validation"
status: draft  # Always draft until human reviews

props:
  # ... populated from Figma properties
tokens:
  # ... populated from Figma variables
accessibility:
  # ... populated from annotations, or TODO if missing
composition:
  # ... populated from layer hierarchy
behavior:
  states: [idle, focus, filled, error, disabled]
  # TODO: transitions need human specification
rules:
  # TODO: do/don't rules require human design judgment
platform-notes:
  figma:
    component-name: "TextField"
    file-key: "[extracted]"
```

## Example: Single component extraction

Input: "Pull the TextField component from Figma"

```
1. figma_get_component(component_key="...")
   → Returns: name, description, properties, variants, variables
2. Map properties to props dimension
3. Map variables to tokens dimension  
4. Generate text-field.contract.yaml
5. Update _index.md: TextField | draft | text-field.contract.yaml
```


## Knowledge references

| File | When to read |
|------|-------------|
| design-system/contracts/_contract-schema.md | Always |
| design-system/tokens/_schema.md | When extracting tokens |
| meta/four-layer-strategy.summary.md | Always |
| references/figma-console-mcp.md | Always |
