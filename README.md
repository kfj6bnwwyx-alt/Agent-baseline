# Design Ops Kit

A portable, tool-agnostic skill system for product-to-engineering workflows. Covers product strategy, research, design, engineering, and quality — with context window discipline built into every layer.

## Quick start

```bash
git clone <this-repo> design-ops-kit
cp .role.example.yaml .role.yaml   # Set your role
python adapters/generate.py --target windsurf  # Generate for your tool
```

## Architecture

| Layer | Contents | Portable? |
|-------|----------|-----------|
| **A: Knowledge base** | Markdown, YAML, JSON domain knowledge | Yes |
| **B: Skills** | 19 SKILL.md files with conditional refs | Yes |
| **C: Adapters** | .windsurfrules, .cursorrules, CLAUDE.md | Generated per tool |

## Roles

| Role | Skills active | Overhead |
|------|--------------|----------|
| Design systems lead | 10 | ~10K |
| Product designer | 6 | ~6K |
| UX researcher | 4 | ~4K |
| Product owner | 3 | ~3K |
| Frontend engineer | 5 | ~5K |
| QA engineer | 4 | ~4K |

## Key integrations

- **design-system-ops** (Murphy Trueman) — audit, governance, drift, context engine
- **designer-skills** (MC Dean) — research, UI craft, interaction, validation
- **inclusive-design-skills** (MC Dean) — cognitive a11y, adaptive interfaces
- **Figma Console MCP** (TJ Pitre) — metadata extraction, token management

See `meta/context-strategy.md` for the context window philosophy.

MIT License.
