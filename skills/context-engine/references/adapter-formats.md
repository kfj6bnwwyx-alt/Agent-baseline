# Adapter Output Formats

## .windsurfrules
Markdown file injected into Windsurf context. Structure:
```
# Design System Rules
## Blocked packages
Do NOT use: @mui/*, @chakra-ui/*, shadcn/*
## Component imports
[table mapping component name → import path]
## Token usage
[how to reference tokens in code]
## Examples
[one example per core component]
```

## .cursorrules
Same structure, `.cursorrules` filename. Cursor-specific conventions if any.

## CLAUDE.md
Same structure for Claude Code projects.

## .skill ZIP
For Claude.ai: package the relevant subset as a .skill file.
