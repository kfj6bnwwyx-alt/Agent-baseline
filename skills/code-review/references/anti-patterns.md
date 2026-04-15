# Anti-Patterns

## Design system anti-patterns
- **Hardcoded values**: Any color, spacing, font-size, radius, or shadow that isn't a token reference
- **Blocked imports**: MUI, Chakra, shadcn, or any library on the blocked list
- **Contract divergence**: Props that don't match the contract (extra props, wrong types, missing defaults)
- **Missing states**: Component lacks loading, error, empty, or disabled states specified in contract
- **Inline styles for tokens**: Using `style={{color: '#4338ca'}}` instead of token reference

## React anti-patterns
- **Props drilling >2 levels**: Use context or composition instead
- **useEffect for derived state**: Compute during render, don't sync
- **Missing key prop**: List items without stable, unique keys
- **Stale closures**: Event handlers capturing outdated state
- **Unnecessary re-renders**: Large components without memo boundaries
- **Index as key**: Using array index as key for dynamic lists

## Performance anti-patterns
- **Bundle bloat**: Importing entire library for one function (`import _ from 'lodash'` vs `import debounce from 'lodash/debounce'`)
- **Render-path computation**: Expensive calculations inside render without useMemo
- **Unoptimized images**: Missing width/height, no lazy loading, no responsive srcset
- **Layout thrashing**: Reading layout properties then writing them in a loop
