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


## Detailed process

### Step 1: Establish context
What's the component or screen? Who's the audience?
Load brand guidelines and relevant tokens.

### Step 2: Map every state to tokens
For each interactive state (idle, hover, focus, active, loading,
disabled, error, success, empty), specify the exact token reference
for every visual property that changes.

### Step 3: Validate hierarchy
Check that visual priority is clear:
- One dominant element per section (size or weight or color)
- Secondary elements visually recede (lighter weight, muted color)
- Disabled elements are visually distinct without relying on color alone

### Step 4: Dark mode verification
If using semantic tokens correctly (action.primary.bg not indigo.600),
dark mode works automatically. Flag any token that would need manual
dark mode handling.

### Step 5: Responsive considerations
Note which visual properties change at breakpoints.
Which tokens shift? Which elements reflow?

## Output format

```markdown
# Visual spec: [component/screen]

## Token mapping
| Element | Property | Token | Light value | Dark value |
|---------|----------|-------|-------------|------------|
| Container | background | surface.primary | #FFFFFF | #1C1C1A |
| Label | color | text.primary | #1A1A18 | #E8E7E3 |
| Label | font-size | typography.fontSize.sm | 14px | 14px |

## State treatments
### hover
| Property | Token change |
|----------|-------------|
| background | surface.primary → surface.primary-hover |

### focus
| Property | Token |
|----------|-------|
| ring | border.focus |
| ring-offset | 2px (hardcoded, focus ring spec) |

### disabled
| Property | Token |
|----------|-------|
| background | surface.disabled |
| text | text.disabled |
| cursor | not-allowed |

## Hierarchy check
- Primary action: Button(primary) — highest contrast, largest target
- Secondary info: Helper text — smallest size, muted color
- Visual flow: top-to-bottom, label → input → helper → action
```

## Example: Card component visual spec

Input: "Design the visual tokens for a Card component"

```markdown
## Token mapping
| Element | Property | Token |
|---------|----------|-------|
| Container | background | surface.elevated |
| Container | border | border.subtle |
| Container | border-radius | radius.lg |
| Container | padding | spacing.5 |
| Container | shadow | elevation.sm |
| Title | color | text.primary |
| Title | font-size | typography.fontSize.lg |
| Title | font-weight | typography.fontWeight.medium |
| Description | color | text.secondary |
| Description | font-size | typography.fontSize.md |
```


## Knowledge references

| File | When to read |
|------|-------------|
| brand/brand-guidelines.md | Always — brand context |
| design-system/tokens/color.tokens.json | Color work |
| design-system/tokens/_schema.md | Token naming conventions |
| references/visual-hierarchy.md | Layout composition |
| references/dark-mode.md | Theme and dark mode work |
| design-system/contracts/[name].contract.yaml | Token mappings for specific components |



## Delegation to MC Dean's designer-skills

When designer-skills is installed, delegate craft execution:

| Design task | Your skill does | MC Dean's skill does |
|------------|----------------|---------------------|
| Color system | Define token structure, brand constraints | Guide palette creation, harmony, contrast |
| Typography | Define token scale, platform constraints | Guide type hierarchy, pairing, rhythm |
| Visual hierarchy | Define component priority from contracts | Guide size/weight/color/space decisions |
| Dark mode | Define semantic token requirements | Guide surface elevation, contrast, desaturation |
| Spacing | Define scale from token schema | Guide rhythm, density, responsive adaptation |
| Data viz | Define component contracts for chart types | Guide encoding, color, interaction patterns |

Your skill owns the token architecture.
MC Dean's skill owns the visual craft.
