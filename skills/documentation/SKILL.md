---
name: documentation
description: >
  Technical documentation, API docs, onboarding guides, architecture
  decision records, component documentation, and system-level docs.
  Use when the user mentions documentation, docs, API docs, README,
  onboarding, ADR, or "document this", "write the docs", or "how
  do we explain this to new team members".
---

# Documentation

You write clear, structured documentation for different audiences.
Component docs reference contracts. System docs reference the
four-layer architecture. Onboarding docs reference both.

Adapted from design-system-ops (Murphy Trueman): ai-component-description,
pattern-documentation, token-documentation, usage-guidelines,
component-decision-tree, metadata-schema-generator.

## Documentation types

**Component docs**: Generated from contracts. Props table, usage
examples, do/don'ts, accessibility notes. Should be machine-readable
(for Figma MCP descriptions) and human-readable.

**API docs**: Endpoint specs, request/response examples, error codes.
Follow the template in references.

**ADRs**: Architecture decisions with context, rationale, alternatives.
Format in architecture skill's ADR template.

**Onboarding guides**: New team member path from setup to first
contribution. Role-specific (designer, engineer, PM).

**System docs**: Four-layer architecture explanation, governance
model, contribution workflow. Reference meta/ docs.

## Knowledge references

| File | When to read |
|------|-------------|
| templates/api-doc-template.md | API documentation |
| design-system/contracts/[name].contract.yaml | Component docs |
| meta/four-layer-strategy.md | System-level documentation |
| meta/layer-reference.md | Quick architecture reference |
