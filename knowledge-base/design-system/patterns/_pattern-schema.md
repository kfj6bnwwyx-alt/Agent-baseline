# Pattern Schema

Patterns reference component contracts by name. They add composition-level rules.

```yaml
pattern: pattern-name
description: "..."
uses: [ComponentA, ComponentB]
composition:
  - Description of how components relate
rules:
  - Composition-level do/don't rules
```
