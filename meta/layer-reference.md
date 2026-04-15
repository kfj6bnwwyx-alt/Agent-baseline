# Layer Reference

| Layer | Contains | Format | Owner |
|-------|----------|--------|-------|
| 1: Tokens | Primitives + semantics | DTCG JSON | DS team |
| 2: Contracts | Component specs | YAML | DS team |
| 2b: Patterns | Composition recipes | YAML | DS + product |
| 3: Context | IDE rule files | Generated | DS team (auto) |
| 4: Adapters | Framework code | Per-platform | Platform teams |

Dependency: L1 ← L2 ← L2b ← L3 ← L4. Changes flow left to right.
