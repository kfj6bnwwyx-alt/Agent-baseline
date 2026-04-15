# Engineering Anti-Patterns

## Design system anti-patterns
- **Hardcoded values**: Any color/spacing/font/radius/shadow not referencing a token
- **Blocked imports**: MUI (@mui/*), Chakra (@chakra-ui/*), shadcn, or any blocked lib
- **Contract divergence**: Props that don't match the contract spec
- **Missing states**: No loading, error, empty, or disabled state when contract requires
- **Wrapper soup**: Wrapping system components in custom divs with overriding styles
- **Token misuse**: Using primitive tokens (blue.500) instead of semantic (action.primary)
- **Copy-paste components**: Duplicating a system component instead of using it

## General code anti-patterns
- **Props drilling**: Passing props through >2 intermediate components
- **God components**: Single component handling multiple unrelated concerns
- **Premature abstraction**: Making something generic before the 3rd use case
- **Magic numbers**: Unexplained numeric values in layout or logic
- **Silent failures**: Catching errors without handling or surfacing them
- **Test mocking abuse**: Mocking so much that tests don't verify real behavior

## Performance anti-patterns
- **Full library imports**: `import _ from 'lodash'` instead of named imports
- **Render-path computation**: Expensive work in render without memoization
- **Layout thrashing**: Interleaving reads and writes to the DOM
- **Unoptimized images**: No lazy loading, no srcset, no explicit dimensions
- **Bundle bloat**: Adding large dependencies for small features
