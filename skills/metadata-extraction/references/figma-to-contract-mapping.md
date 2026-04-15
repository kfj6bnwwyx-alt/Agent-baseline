# Figma to Contract Field Mapping

How Figma Console MCP output maps to the 7-dimension contract schema.

## Mapping table

| Figma Console MCP field | Contract dimension | Contract field | Notes |
|------------------------|-------------------|---------------|-------|
| Component name | header | component | Direct map |
| Component description | header | description | Use as-is or refine |
| Properties (boolean) | Dim 1: API | props.[name].type: boolean | Direct map |
| Properties (instance swap) | Dim 1: API | props.[name].type: enum | Map swap options to enum values |
| Properties (text) | Dim 1: API | props.[name].type: string | Direct map |
| Properties (variant) | Dim 1: API | props.[name].values | Variant options become enum values |
| Variable references | Dim 2: Visual | tokens.[property] | Map variable name to token path |
| Color variables | Dim 2: Visual | tokens.container.background | Map to semantic token names |
| Spacing variables | Dim 2: Visual | tokens.container.padding | Map to spacing scale |
| Auto-layout specs | Dim 4: Composition | composition.anatomy | Layer order = anatomy order |
| Nested components | Dim 4: Composition | composition.nesting | Parent-child from Figma hierarchy |
| Interaction annotations | Dim 5: Behavior | behavior.states | If annotated in Figma |
| A11y annotations | Dim 3: Accessibility | accessibility | If annotated in Figma |

## Fields that CANNOT be auto-populated from Figma

These require human design judgment:

| Dimension | Field | Why |
|-----------|-------|-----|
| Dim 3: Accessibility | keyboard patterns | Figma doesn't specify keyboard behavior |
| Dim 3: Accessibility | screen reader announcements | Figma doesn't specify SR text |
| Dim 5: Behavior | transitions | Figma states are static, not connected |
| Dim 5: Behavior | animation specs | No timing/easing data in Figma |
| Dim 6: Rules | do/don't | Design opinion requires human judgment |
| Dim 6: Rules | prefer-instead | Cross-component knowledge |
| Dim 7: Platform | framework-specific notes | Figma doesn't know about code |

## Post-extraction checklist
After auto-generating a contract from Figma:
- [ ] Review Dim 1 (API): are all props correctly typed?
- [ ] Review Dim 2 (Visual): do token mappings use semantic names?
- [ ] Fill Dim 3 (Accessibility): add keyboard, SR, focus specs
- [ ] Fill Dim 4 (Composition): verify anatomy order matches intent
- [ ] Fill Dim 5 (Behavior): add state machine and animation specs
- [ ] Fill Dim 6 (Rules): add usage do/don't from design judgment
- [ ] Fill Dim 7 (Platform): add framework-specific implementation notes
- [ ] Set status to "draft" until all dimensions are human-reviewed
