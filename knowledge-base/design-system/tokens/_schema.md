# Token Schema

## Format: W3C DTCG (Design Tokens Community Group)

All tokens use the DTCG standard format with `$value`, `$type`,
and optional `$description` fields.

## Token tiers

### Tier 1: Primitives
Raw values with no semantic meaning. Named by their properties.
```json
{
  "color": {
    "blue": {
      "50":  { "$value": "#EFF6FF", "$type": "color" },
      "500": { "$value": "#3B82F6", "$type": "color" },
      "900": { "$value": "#1E3A5F", "$type": "color" }
    }
  },
  "spacing": {
    "1":  { "$value": "4px", "$type": "dimension" },
    "2":  { "$value": "8px", "$type": "dimension" },
    "4":  { "$value": "16px", "$type": "dimension" }
  }
}
```

### Tier 2: Semantics
Intent-mapped tokens that reference primitives. Named by purpose.
```json
{
  "color": {
    "action": {
      "primary": {
        "bg":       { "$value": "{color.blue.500}", "$type": "color", "$description": "Primary action background" },
        "bg-hover": { "$value": "{color.blue.600}", "$type": "color" },
        "text":     { "$value": "{color.white}", "$type": "color" }
      }
    },
    "surface": {
      "primary":   { "$value": "{color.white}", "$type": "color" },
      "secondary": { "$value": "{color.gray.50}", "$type": "color" }
    },
    "text": {
      "primary":   { "$value": "{color.gray.900}", "$type": "color" },
      "secondary": { "$value": "{color.gray.500}", "$type": "color" },
      "disabled":  { "$value": "{color.gray.300}", "$type": "color" }
    }
  }
}
```

### Tier 3: Component tokens (optional)
Scoped to specific components. Reference semantics.
```json
{
  "button": {
    "primary": {
      "bg": { "$value": "{color.action.primary.bg}", "$type": "color" }
    }
  }
}
```

## Naming conventions

- Primitives: `{category}.{property}.{variant}` — `color.blue.500`
- Semantics: `{category}.{concept}.{property}` — `color.action.primary.bg`
- Components: `{component}.{variant}.{property}` — `button.primary.bg`

## Rules
- Component code references SEMANTIC tokens, never primitives
- Primitive tokens are internal — consumed by semantics only
- Every semantic token must reference a primitive (no hardcoded values)
- Token names must be descriptive enough that an AI agent can infer purpose

## Modes (theming)
For dark mode or brand variants, use mode-specific value overrides:
```json
{
  "color": {
    "surface": {
      "primary": {
        "$value": "{color.white}",
        "$type": "color",
        "$extensions": {
          "mode": {
            "dark": "{color.gray.900}",
            "high-contrast": "{color.black}"
          }
        }
      }
    }
  }
}
```

## Compilation
Style Dictionary compiles tokens to platform targets:
- CSS custom properties (`--color-action-primary-bg`)
- SCSS variables (`$color-action-primary-bg`)
- Swift constants (`Color.action.primary.bg`)
- Android XML resources
- Tailwind config values
- JSON for runtime theming
