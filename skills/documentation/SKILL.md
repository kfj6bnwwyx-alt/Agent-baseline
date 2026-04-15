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


## Detailed process

### For component docs
1. Load the component contract (all 7 dimensions)
2. Generate props table from Dimension 1
3. Generate usage examples from contract defaults and rules
4. Generate do/don't section from Dimension 6
5. Generate accessibility section from Dimension 3
6. Generate Figma MCP description (~600 words, machine-parseable)

### For system docs
1. Load meta/four-layer-strategy.md
2. Explain the architecture for the target audience
3. Include concrete examples from existing contracts
4. Reference the getting started steps

### For onboarding guides
1. Identify the role (designer, engineer, PM)
2. Explain what's relevant to their role
3. Walk through their first task with the system
4. Point to the skills/agents they'll use

### For ADRs
1. Use the ADR template from architecture skill
2. Ensure context section explains the WHY clearly
3. List all alternatives with specific reasons for rejection

## Output format

### Component documentation
```markdown
# [ComponentName]

[One paragraph: what it is, when to use it]

## Import
```[language]
import { ComponentName } from '@system/ui';
```

## Props
| Prop | Type | Default | Description |
|------|------|---------|-------------|
| variant | 'primary' \| 'secondary' | 'primary' | Visual treatment |

## Usage
### Basic
```[language]
<ComponentName>Content</ComponentName>
```

### With loading state
```[language]
<ComponentName loading>Saving...</ComponentName>
```

## Accessibility
- Role: [from Dimension 3]
- Keyboard: [interactions]
- Screen reader: [announcements]

## Do / Don't
- Do: [from Dimension 6]
- Don't: [from Dimension 6]
```

### Figma MCP description format
```
[ComponentName]: [One-line purpose]. Variants: [list].
Props: [key props]. Tokens: [key tokens].
A11y: [key requirement]. Do not: [top rule].
```
Keep under 600 words. Structured for machine parsing.


## Knowledge references

| File | When to read |
|------|-------------|
| templates/api-doc-template.md | API documentation |
| design-system/contracts/[name].contract.yaml | Component docs |
| meta/four-layer-strategy.md | System-level documentation |
| meta/layer-reference.md | Quick architecture reference |
