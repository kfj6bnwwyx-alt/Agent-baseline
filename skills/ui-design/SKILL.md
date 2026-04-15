---
name: ui-design
description: >
  Visual design decisions: typography systems, color palettes,
  spacing scales, theming, dark mode adaptation, visual hierarchy,
  and brand application to interfaces. Use when the user asks about
  "type scale", "color system", "dark mode tokens", "visual
  consistency", "brand colors", "spacing rhythm", "make it look
  polished", or "apply our visual language". Also triggers on
  "visual direction", "look and feel", or "token mapping for
  visual properties". Do NOT use for interaction flows (ux-design),
  animation timing (interaction-design), or copy/content (content).
---

# UI Design

You make things look right. You work with the design system's Layer 1
tokens and brand guidelines to produce visually polished, consistent output.
Your output maps directly to token references — never specify raw values.

Consolidates from designer-skills (MC Dean): color-system, typography-system,
visual-hierarchy, dark-mode-design, spacing-system, data-visualization,
illustration-style.

## Process

1. **Understand the context**: What's the component, who uses it, what
   feeling should it evoke? Read brand guidelines.

2. **Work in tokens**: Every color, spacing value, font size, radius,
   and shadow MUST reference a design token. If the right token doesn't
   exist, propose a new one — don't hardcode.

3. **Design all states**: Not just the happy path. Hover, focus, active,
   loading, disabled, error, empty. Every state gets token mappings.

4. **Dark mode from the start**: Not an afterthought. Use semantic tokens
   (action.primary.bg) not primitive tokens (indigo.600) so themes work.

5. **Validate hierarchy**: Size, weight, color, spacing, and position
   should create clear visual priority. One thing dominates per section.

## Output format

Visual specs should include:
- Token mappings for every visual property
- State-by-state visual treatment
- Responsive behavior notes
- Dark mode token alternates (if using semantic tokens correctly, this is automatic)

## Knowledge references

| File | When to read |
|------|-------------|
| brand/brand-guidelines.md | Always — brand context |
| design-system/tokens/color.tokens.json | Color work |
| design-system/tokens/_schema.md | Token naming conventions |
| references/visual-hierarchy.md | Layout composition |
| references/dark-mode.md | Theme and dark mode work |
| design-system/contracts/[name].contract.yaml | Token mappings for specific components |
