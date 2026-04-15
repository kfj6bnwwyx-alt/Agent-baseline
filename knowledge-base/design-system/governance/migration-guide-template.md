# Migration Guide Template

Use this template when publishing a major version with breaking changes.

```markdown
# Migration guide: v[old] → v[new]

## Breaking changes summary
| Change | Affected components | Migration effort |
|--------|-------------------|-----------------|
| [description] | [list] | [low/medium/high] |

## Automated migration
If a codemod is available:
```bash
npx @system/codemod [migration-name]
```

## Manual migration steps

### Change 1: [description]

**Before (v[old]):**
```[language]
[old code]
```

**After (v[new]):**
```[language]
[new code]
```

**Why this changed:** [rationale from ADR or contract change]

### Change 2: [description]
...

## Deprecation timeline
| Component/prop | Deprecated in | Removed in | Replacement |
|---------------|--------------|------------|-------------|
| [name] | v[x] | v[y] | [replacement] |

## Testing your migration
1. Update the package
2. Run the codemod (if available)
3. Run `npx @system/audit` to check for remaining issues
4. Run your test suite
5. Visual regression check

## Getting help
- File an issue: [link]
- Slack: [channel]
- Office hours: [schedule]
```
