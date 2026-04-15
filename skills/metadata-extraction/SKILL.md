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

## Knowledge references

| File | When to read |
|------|-------------|
| design-system/contracts/_contract-schema.md | Always |
| design-system/tokens/_schema.md | When extracting tokens |
| meta/four-layer-strategy.summary.md | Always |
| references/figma-console-mcp.md | Always |
