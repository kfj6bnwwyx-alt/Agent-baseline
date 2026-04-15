# Performance Budget

## Targets (adjust per project)
| Metric | Target | Ceiling |
|--------|--------|---------|
| First Contentful Paint | <1.5s | <2.5s |
| Largest Contentful Paint | <2.5s | <4.0s |
| Cumulative Layout Shift | <0.1 | <0.25 |
| Total bundle size (gzipped) | <200KB | <350KB |
| Component JS size | <10KB | <25KB |
| Time to Interactive | <3.5s | <5.0s |

## Rules
- Every new dependency must justify its bundle cost
- Tree-shaking must be verified (named imports, not barrel exports)
- Images must be optimized and lazy-loaded below the fold
- Animations must not trigger layout (use transform/opacity only)
- Server components where possible (if using RSC)
