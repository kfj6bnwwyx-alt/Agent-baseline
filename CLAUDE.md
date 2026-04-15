# Design Ops Kit

This repo is a portable skills system for product-to-engineering workflows.
It contains design system knowledge, AI agent skills, and orchestration
chains covering product strategy, research, design, engineering, and quality.

## Architecture

Three layers:
- **Layer A: Knowledge base** (`knowledge-base/`) — domain knowledge in markdown, YAML, JSON
- **Layer B: Skills** (`skills/`) — 23 SKILL.md files with conditional knowledge refs
- **Layer C: Adapters** (`adapters/`) — generated per-tool configs

## Design system: four-layer model

The design system uses a four-layer architecture:
1. **Tokens** (DTCG JSON) → `knowledge-base/design-system/tokens/`
2. **Contracts** (YAML, 7 dimensions per component) → `knowledge-base/design-system/contracts/`
3. **Context files** (generated) → produced by context-engine skill/agent
4. **Adapters** (platform code) → `knowledge-base/engineering/platform-adapters/`

Contracts are the center of gravity. 15+ skills reference them. Read
`knowledge-base/design-system/contracts/_contract-schema.md` to understand
the 7-dimension format.

## Subagents

Custom agents are in `.claude/agents/`. Key agents:
- `design-system-auditor` — audits against contracts (Sonnet)
- `code-generator` — implements from contracts (Sonnet)
- `accessibility-reviewer` — WCAG 2.2 AA (Sonnet)
- `context-engine` — generates 7 blueprints + context files (Sonnet)
- `governance-lead` — system lifecycle decisions (Opus)
- `architect` — technical decisions + ADRs (Opus)
- `metadata-extractor` — Figma Console MCP extraction (Haiku)

## Chains

Defined in `orchestration/chains/`. Key chains:
- `new-component`: metadata-extraction → ux → ui → code-gen → a11y → testing
- `figma-to-code`: metadata-extraction → context-engine → code-gen
- `feature-review`: audit + a11y + code-review + qa (parallel)
- `system-health`: full system audit → governance dashboard

## Context discipline

Skills use progressive disclosure (L1 → L2 → L3). Agents get fresh
context windows. Between chain steps, use structured bridges (~500 tokens)
not full history. See `meta/context-strategy.md`.



## External integrations

This repo is designed to work alongside these external plugins and MCPs.
See `docs/claude-code-setup.md` for install commands.

### Superpowers (obra/superpowers)
TDD enforcement and quality gates. When installed, code-gen follows
test-first workflow and two-stage review (spec compliance, then quality).
Superpowers enforces structure; our skills provide design system knowledge.

### Design System Ops (murphytrueman/design-system-ops)
DS practitioner skill pack. Adds dual-scoring audits, HTML dashboards,
token audit scripts, and chained pre-release validation. Complements
our contract-level auditing with execution-level checking.

### Playwright MCP
Browser automation for real accessibility scanning, visual regression
testing, and interaction verification. Transforms our a11y skill from
checklist-based to execution-based.

### Figma MCP
Design tool connection for token extraction, component metadata, and
design parity checking. Used by metadata-extractor agent.

## Upstream repos

This kit integrates patterns from:
- design-system-ops (Murphy Trueman) — audit, governance, context engine
- designer-skills (MC Dean) — research, UI, interaction, validation
- inclusive-design-skills (MC Dean) — cognitive a11y, adaptive interfaces
- Figma Console MCP (TJ Pitre) — metadata extraction

See `meta/upstream-tracking.md` for sync instructions.
