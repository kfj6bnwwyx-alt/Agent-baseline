# Four-Layer Architecture (Summary)

**Layer 1: Design Tokens** — DTCG JSON primitives. Colors, spacing, typography. Compiled by Style Dictionary.

**Layer 2: Component Contracts** — Platform-agnostic YAML per component. Props, token mappings, a11y rules, do/don'ts.

**Layer 2b: Composition Patterns** — Multi-component recipes referencing contracts by name.

**Layer 3: AI Context Files** — Generated from L1+L2 per tool. Blocked-package lists, import maps, code examples.

**Layer 4: Platform Adapters** — Thin framework implementations (React, Angular, SwiftUI) conforming to L2 contracts.

**Dependency:** Tokens ← Contracts ← Context ← Adapters. DS team owns L1-L3. Platform teams own L4.
