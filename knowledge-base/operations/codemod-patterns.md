# Codemod Patterns

## When to write a codemod
- Prop renamed: `type="primary"` → `variant="primary"`
- Component renamed: `<OldCard>` → `<SurfaceCard>`
- Import path changed: `@system/ui/Card` → `@system/ui`
- Prop removed with replacement: `size="xs"` → `size="sm"`

## When NOT to write a codemod
- Behavioral change (logic, not syntax)
- Visual-only change (token values, not prop names)
- New required prop (requires human decision about the value)

## Codemod structure (jscodeshift)
```javascript
// rename-prop.js
export default function transformer(file, api) {
  const j = api.jscodeshift;
  return j(file.source)
    .findJSXElements('Button')
    .find(j.JSXAttribute, { name: { name: 'type' } })
    .forEach(path => {
      path.node.name.name = 'variant';
    })
    .toSource();
}
```

## Testing codemods
- Run against snapshot fixtures (before/after pairs)
- Verify no unintended changes outside target components
- Handle edge cases: spread props, dynamic values, aliased imports
