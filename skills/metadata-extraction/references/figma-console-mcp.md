# Figma Console MCP Reference

Key tools for metadata extraction:

| Tool | Use for |
|------|---------|
| `figma_get_design_system_kit` | Full system extraction — tokens, components, styles in one call |
| `figma_get_variables` | Design tokens and variables with multi-format export |
| `figma_get_component` | Component metadata or reconstruction spec |
| `figma_get_component_for_development` | Component + image for dev handoff |
| `figma_check_design_parity` | Compare Figma spec against code implementation |
| `figma_generate_component_doc` | Platform-agnostic markdown documentation |

## Connection modes
- **Remote SSE**: Read-only, 22 tools. Good for extraction.
- **Cloud Mode**: Read + write, 83 tools. Good for writing descriptions back.
- **NPX/Local**: Full 94+ tools. Best for complete workflows.

## Output format
Extraction produces JSON matching the structure in _contract-schema.md.
Transform to YAML contract as a second step.
