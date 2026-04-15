# Deprecation Schedule

Adapted from design-system-ops (Murphy Trueman): deprecation-process.

## Deprecation process

1. **Announce**: Add `@deprecated` JSDoc tag with migration path.
   Update contract status to "deprecated" in _index.md.
   Add sunset date.

2. **Grace period**: Minimum 2 sprints (4 weeks) between
   announcement and removal. Longer for widely-used components.

3. **Migration support**: Provide codemod if possible (via
   code-gen skill). Document manual migration steps.

4. **Soft removal**: Remove from Layer 3 context files (AI stops
   suggesting it). Keep in codebase with warnings.

5. **Hard removal**: Remove from codebase after all consumers
   have migrated. Verify via drift detection.

## Currently deprecated

| Component | Deprecated | Sunset | Replacement | Migration guide |
|-----------|-----------|--------|-------------|-----------------|
| (none yet) | — | — | — | — |

## Versioning approach

- **Patch** (1.0.x): Bug fixes, no contract changes
- **Minor** (1.x.0): New components, new optional props, new patterns
- **Major** (x.0.0): Breaking contract changes, removed components
