# Contract Schema

Every component contract is a YAML file with these sections:

```yaml
component: ComponentName           # PascalCase, matches code export
category: action|input|layout|...  # Semantic grouping
description: "..."                 # One-line purpose

props:                             # Typed API surface
  propName:
    type: enum|boolean|string|number|IconName|ReactNode
    values: [...]                  # For enums
    default: value
    required: true|false

tokens:                            # Token mappings per variant/state
  background: semantic.token.name
  text: semantic.token.name

slots:                             # Composition points (optional)
  - name: children
    accepts: [Text, Icon]

accessibility:
  role: button|dialog|...
  min-target: 44px
  focus-visible: required
  aria-*: requirements

rules:
  do: ["Usage guidance"]
  dont: ["Anti-patterns"]
  forbidden-with: [ComponentName]  # Incompatible compositions
```
