# Claude Code Setup Guide

Run these commands after cloning the repo and opening Claude Code.

## Step 1: Install external plugins

These complement the design-ops-kit's skills with enforcement,
execution, and maintained rule sets.

```bash
# Superpowers — TDD enforcement, quality gates, structured dev workflow
# 146K stars, battle-tested. Enforces test-before-code, two-stage review.
/plugin marketplace add obra/superpowers-marketplace
/plugin install superpowers@superpowers-marketplace

# Murphy's Design System Ops — the original DS practitioner skill pack
# Token audits with dual scoring, a11y audits mapped to WCAG criteria,
# HTML dashboards, chained pre-release validation pipelines.
/plugin marketplace add murphytrueman/design-system-ops
/plugin install design-system-ops@design-system-ops

# wshobson/agents — UI/UX design plugin for the design systems context
# Comprehensive design patterns, accessibility, modern patterns.
/plugin marketplace add wshobson/agents
/plugin install ui-ux-design@claude-code-workflows

# MC Dean's designer-skills — 63 design skills across 6 domains
# Research, UI design, interaction, validation, ops, writing.
# These are the upstream source for many of our reference files.
# Installing the actual pack means updates flow automatically.
/plugin marketplace add Owl-Listener/designer-skills
/plugin install designer-skills@designer-skills

# MC Dean's inclusive-design-skills — cognitive a11y, adaptive interfaces
/plugin marketplace add Owl-Listener/inclusive-design-skills
/plugin install inclusive-design-skills@inclusive-design-skills
```

## Step 1b: Understanding the integration model

Your kit and the external plugins serve different purposes:

| Layer | Your kit provides | External plugins provide |
|-------|------------------|------------------------|
| Knowledge | Contracts, tokens, patterns, four-layer architecture | Domain-specific methods, audit scripts |
| Process | Chains, quality gates, context bridges | TDD enforcement, validation pipelines |
| Orchestration | Agents, slash commands, routing | Slash commands within their domain |
| Execution | Output specs, format templates | Actual scanning, scoring, dashboard generation |

The principle: **your kit is the architecture, external plugins are the expertise.**
When Murphy improves his token audit, you get it. When MC Dean adds a research
method, it's available. Your skills orchestrate their execution against your contracts.

## Step 2: Configure MCP servers

```bash
# Figma — read designs, extract tokens, generate code from Figma files
# Required for metadata-extraction skill and figma-to-code chain
claude mcp add figma -- npx -y figma-developer-mcp --stdio

# Playwright — browser automation for real a11y testing and visual regression
# Enables the accessibility-reviewer agent to run actual scans, not just checklists
claude mcp add playwright -- npx -y @anthropic/mcp-playwright

# Figma Console MCP (TJ Pitre) — your existing Figma metadata extraction tool
claude mcp add figma-console -- npx mcp-remote http://127.0.0.1:29979/mcp
```

## Step 3: Verify setup

```
# Check agents are discovered
claude agents

# Check plugins installed
/plugin list

# Check MCP servers
/mcp

# Run a quick test
/audit system
```

## What you now have

| Capability | Source | Activation |
|-----------|--------|-----------|
| Design system auditing | Your kit + Murphy's pack | /audit or natural language |
| Code generation from contracts | Your kit | /figma-to-code or /new-component |
| TDD enforcement | Superpowers | Automatic — enforces test-first |
| Accessibility scanning | Your kit + Playwright MCP | /a11y with actual browser testing |
| Token auditing with dual scoring | Murphy's pack | "audit tokens" |
| Pre-release validation pipeline | Murphy's pack + your chains | /health or natural language |
| Quality gates between chain steps | Superpowers pattern + your chains | Automatic in chains |
| 100+ UI rules checking | Vercel web-design-guidelines (install separately if desired) | During code review |
| Figma extraction | Your kit + Figma MCP | /figma-to-code |
| HTML health dashboards | Murphy's pack | After system-health chain |

## Integration architecture

```
Your kit (knowledge + orchestration)
  ├── .claude/agents/ → route to specialists
  ├── .claude/commands/ → /slash activation
  ├── skills/ → domain knowledge + process
  ├── knowledge-base/ → contracts, tokens, patterns
  │
  ├── Superpowers (enforcement)
  │   └── TDD, quality gates, two-stage review
  │
  ├── Design System Ops (DS-specific execution)
  │   └── Token audit scripts, a11y audit scripts, dashboards
  │
  ├── Playwright MCP (browser execution)
  │   └── Real a11y scans, visual regression, interaction testing
  │
  └── Figma MCP (design tool connection)
      └── Token extraction, component metadata, design parity
```

Your kit provides the knowledge architecture and orchestration.
External plugins provide enforcement and execution.
