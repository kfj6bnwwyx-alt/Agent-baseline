# Layer Reference

Quick lookup for the four-layer architecture.

## Layers

| Layer | Contains | Format | Owner | Changes when |
|-------|----------|--------|-------|-------------|
| 1: Tokens | Primitives, semantics, component tokens | DTCG JSON | DS team | Rebrand, new scale, new mode |
| 2: Contracts | Component specs (7 dimensions) | YAML | DS team | New component, API change |
| 2b: Patterns | Multi-component compositions | YAML | DS + product | New flow, new composition |
| 3: Context | IDE rules, blueprints, preview manifests | Generated | DS team (auto) | Any L1/L2 change |
| 4: Adapters | React, Angular, SwiftUI implementations | Framework code | Platform teams | L2 contract changes |

## Dependency direction

```
L1 Tokens ← L2 Contracts ← L2b Patterns ← L3 Context ← L4 Adapters
```

Changes flow left to right. Each layer depends only on layers to its left.
When L1 tokens change, everything downstream regenerates.
When L2 contracts change, L3 and L4 update.
L4 can change without affecting anything upstream.

## What lives where

| Artifact | Layer | Path |
|----------|-------|------|
| color.tokens.json | L1 | knowledge-base/design-system/tokens/ |
| button.contract.yaml | L2 | knowledge-base/design-system/contracts/ |
| destructive-confirmation.pattern.yaml | L2b | knowledge-base/design-system/patterns/ |
| ux-blueprint.yml | L3 | .ai/context-engine/ (generated) |
| .windsurfrules | L3 | project root (generated) |
| preview manifests | L3 | .ai/context-engine/ (generated) |
| React component | L4 | src/components/ |
| SwiftUI view | L4 | Sources/SystemUI/ |

## Key files for understanding the system

| File | What it explains | Token cost |
|------|-----------------|-----------|
| meta/four-layer-strategy.md | Full architecture + rationale | ~5K |
| meta/four-layer-strategy.summary.md | Architecture quick reference | ~500 |
| contracts/_contract-schema.md | 7-dimension contract format | ~2K |
| patterns/_pattern-schema.md | Pattern composition format | ~1K |
| tokens/_schema.md | Token tiers, naming, modes | ~1K |
| meta/context-strategy.md | Context window budgets + bridges | ~800 |

## Which skills reference which layers

| Skill | L1 | L2 | L2b | L3 | L4 |
|-------|----|----|-----|----|----|
| design-system-audit | x | x | | | |
| metadata-extraction | x | x | | | |
| context-engine | x | x | x | x | |
| code-gen | | x | x | x | x |
| code-review | | x | | x | x |
| ux-design | | x | x | | |
| ui-design | x | x | | | |
| accessibility-audit | | x | | | |
| governance | x | x | | x | |
| testing | | x | | | x |

## Ownership model

- **DS team** owns L1, L2, L2b, L3 generation
- **Platform teams** own L4 implementations
- **Product teams** can propose L2b patterns (DS team approves)
- **Context engine** automates L3 generation from L1+L2
- **Nobody** should hand-edit L3 files — always regenerate
