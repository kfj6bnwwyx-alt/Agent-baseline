# Dark Mode Design

Adapted from designer-skills (MC Dean): dark-mode-design.

## Principles
- Dark mode is NOT just inverting colors
- Use desaturated colors (saturated colors vibrate on dark bg)
- Reduce contrast slightly (pure white on pure black is harsh)
- Elevate surfaces with lighter shades, not shadows
- Test with real content, not just components

## Surface hierarchy (dark mode)
- **Background**: darkest (#111 - #1a1a1a)
- **Surface 1**: slightly lighter (#1c1c1c - #222)
- **Surface 2**: card level (#252525 - #2a2a2a)
- **Surface 3**: elevated/modal (#2f2f2f - #333)
- **Overlay**: semi-transparent black (rgba(0,0,0,0.5))

In dark mode, elevation = lightness (opposite of light mode shadows).

## Text on dark backgrounds
- Primary text: ~87% white (not pure white) — #e0e0e0 - #ebebeb
- Secondary text: ~60% white — #999 - #a0a0a0
- Disabled text: ~38% white — #666

## Common mistakes
- Using pure black (#000) as background (too stark)
- Using pure white (#fff) for text (too much contrast)
- Keeping saturated brand colors unchanged (they glow)
- Relying only on color to show state changes (test with low brightness)
- Forgetting to test images, illustrations, and shadows
