# Micro-Animation Patterns

Adapted from designer-skills (MC Dean): micro-animation.

## Timing guidelines

| Action | Duration | Easing |
|--------|----------|--------|
| Button press | 100ms | ease-out |
| Modal open | 200-250ms | ease-out |
| Modal close | 150-200ms | ease-in |
| Drawer slide | 250-300ms | ease-in-out |
| Toast enter | 200ms | ease-out |
| Toast exit | 150ms | ease-in |
| Page transition | 200-300ms | ease-in-out |
| Skeleton pulse | 1.5s loop | ease-in-out |
| Hover state | 150ms | ease-out |
| Color change | 200ms | ease-out |

## Principles
- **Purpose**: Every animation must serve a function (feedback,
  orientation, continuity). Never animate for decoration.
- **Speed**: When in doubt, faster. Users notice slow more than fast.
- **Easing**: ease-out for entrances (fast start, gentle stop).
  ease-in for exits (gentle start, fast finish).
- **Reduced motion**: Always provide `prefers-reduced-motion` alternative.
  Crossfade or instant cut. Never disable feedback entirely.

## Properties to animate (GPU-friendly)
- transform (translate, scale, rotate)
- opacity
- clip-path

## Never animate
- width/height (causes layout reflow)
- top/left/right/bottom (use transform: translate instead)
- font-size
- box-shadow (use opacity on a pseudo-element instead)
