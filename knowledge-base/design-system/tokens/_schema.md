# Token Schema

## Format: W3C DTCG (Design Tokens Community Group)

## Naming
- Primitives: `color.blue.500`, `spacing.4`, `radius.md`
- Semantics: `color.action.primary`, `color.surface.elevated`
- Component: `button.primary.background`, `input.border.default`

Semantic tokens reference primitives. Component tokens reference semantics.
Never reference primitives from component code.

## Compilation
Style Dictionary compiles to: CSS custom properties, SCSS, Swift, Android XML, Tailwind.
