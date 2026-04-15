# API Documentation Template

## Component doc structure

```markdown
# [ComponentName]

## Overview
[One paragraph: what this is, when to use it, which contract it implements]

## Import
```[language]
import { ComponentName } from '@system/ui';
```

## Props

| Prop | Type | Default | Required | Description |
|------|------|---------|----------|-------------|
| variant | enum | 'primary' | no | Visual variant per contract |

## Usage

### Basic
```[language]
<ComponentName>Label</ComponentName>
```

### With variants
```[language]
<ComponentName variant="secondary">Label</ComponentName>
```

## States
- **Default**: [description]
- **Loading**: [description + when to show]
- **Error**: [description + recovery action]
- **Disabled**: [description + when to use]

## Accessibility
- Role: [ARIA role from contract]
- Keyboard: [Tab, Enter, Space, Escape behaviors]
- Screen reader: [announcements per state]
- Min target: [from contract]

## Do / Don't
[Pulled directly from contract rules.do and rules.dont]

## Tokens used
[Token mappings from contract — helps devs verify correct token usage]

## Related
- [Component]: [relationship]
- [Pattern]: [composition recipe name]
```

## Figma MCP description format

For writing component descriptions back to Figma (via Figma Console MCP):

```
[Component name]: [One-line purpose]. Variants: [list]. 
Required props: [list]. Tokens: [key tokens]. 
A11y: [key requirement]. Do not: [top don't rule].
```

Keep under 600 words. Structured for machine parsing.
