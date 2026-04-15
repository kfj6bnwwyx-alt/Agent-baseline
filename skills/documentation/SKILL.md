---
name: documentation
description: >
  Write component documentation, API reference docs, onboarding
  guides, architecture decision records, and design system-level
  documentation. Use when the user says "write docs for this
  component", "API documentation", "onboarding guide for new
  engineers", "document this decision", "README for the system",
  or "generate Figma MCP component descriptions". Also triggers on
  "technical writing", "usage examples", or "docs site content".
  Do NOT use for auditing components (design-system-audit) or
  building components (code-gen).
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
