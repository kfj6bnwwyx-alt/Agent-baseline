# Performance Budget

## Targets (adjust per project)

| Metric | Target | Ceiling | Tool |
|--------|--------|---------|------|
| First Contentful Paint | <1.5s | <2.5s | Lighthouse |
| Largest Contentful Paint | <2.5s | <4.0s | Lighthouse |
| Cumulative Layout Shift | <0.1 | <0.25 | Lighthouse |
| Total bundle (gzipped) | <200KB | <350KB | Bundlesize |
| Per-component JS | <10KB | <25KB | Bundlesize |
| Time to Interactive | <3.5s | <5.0s | Lighthouse |

## Rules
- Every new dependency must justify its bundle cost
- Tree-shaking verified via named imports
- Images optimized and lazy-loaded below fold
- Animations use transform/opacity only (no layout triggers)
- Fonts: max 2 families, woff2 only, display: swap
- Critical CSS inlined, remainder async-loaded
