# WCAG 2.2 AA Checklist

Comprehensive checklist for accessibility audits. This is the full version.
Load only when running dedicated accessibility audits.

## Perceivable
- 1.1.1 Non-text content: alt text for images, aria-label for icons
- 1.3.1 Info and relationships: semantic HTML, proper heading hierarchy
- 1.3.2 Meaningful sequence: DOM order matches visual order
- 1.4.1 Use of color: never color-only to convey information
- 1.4.3 Contrast minimum: 4.5:1 normal, 3:1 large text
- 1.4.4 Resize text: up to 200% without loss of content
- 1.4.11 Non-text contrast: 3:1 for UI components and graphics
- 1.4.12 Text spacing: support user override of line-height, letter-spacing
- 1.4.13 Content on hover/focus: dismissable, hoverable, persistent

## Operable
- 2.1.1 Keyboard: all functionality via keyboard
- 2.1.2 No keyboard trap: can navigate away from all components
- 2.4.3 Focus order: logical and intuitive
- 2.4.6 Headings and labels: descriptive
- 2.4.7 Focus visible: clear focus indicator
- 2.4.11 Focus not obscured: focused element not hidden by sticky headers
- 2.5.5 Target size: minimum 24×24px (44×44px recommended)
- 2.5.8 Target size enhanced: minimum 44×44px

## Understandable
- 3.1.1 Language of page: lang attribute set
- 3.2.1 On focus: no unexpected context change
- 3.3.1 Error identification: clear error messages
- 3.3.2 Labels or instructions: visible before interaction
- 3.3.3 Error suggestion: specific correction guidance

## Robust
- 4.1.2 Name, role, value: all components have accessible names
- 4.1.3 Status messages: programmatically determined without focus
