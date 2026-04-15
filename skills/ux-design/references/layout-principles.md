# Layout Principles

## Spacing system
Build on a base unit (4px or 8px). All spacing is a multiple.
Common scale: 4, 8, 12, 16, 24, 32, 48, 64, 96.

## Layout patterns

**Stack**: Vertical list. Default pattern for most content flows.
Gap consistent within a section, larger between sections.

**Cluster**: Horizontal group that wraps. Use for tags, buttons,
meta information. Set gap and let items flow naturally.

**Sidebar**: Fixed-width sidebar + fluid main content.
Collapse sidebar to overlay below breakpoint.

**Grid**: Equal columns for cards, products, gallery items.
Use auto-fill with minmax for responsive without breakpoints.

## Responsive approach
- Design for mobile first, enhance for larger screens
- Use fluid values where possible (clamp, minmax)
- Set breakpoints at content breaking points, not device sizes
- Common breakpoints: 640px (sm), 768px (md), 1024px (lg), 1280px (xl)
- Test at every width, not just breakpoint boundaries
