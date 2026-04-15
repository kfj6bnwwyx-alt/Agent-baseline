# Upstream Tracking

This file tracks which external repos feed into the design-ops-kit
and how to stay current with their updates.

## Tracked repositories

### design-system-ops (Murphy Trueman)
- **Repo**: https://github.com/murphytrueman/design-system-ops
- **What we use**: context-engine-builder (7 blueprints), token-audit,
  component-audit, drift-detection, system-health, naming-audit,
  contribution-workflow, deprecation-process, session-memory
- **Maps to skills**: design-system-audit, context-engine, governance,
  metadata-extraction, documentation
- **Last synced**: [date]
- **How to update**: Check his SKILL.md files for new patterns,
  process steps, or output formats. Adapt into relevant skill body
  and reference files. Don't change his core framework — align to it.
- **Watch for**: New blueprint types, updated audit criteria,
  new governance patterns, Figma Console MCP integration updates

### designer-skills (MC Dean / Owl-Listener)
- **Repo**: https://github.com/Owl-Listener/designer-skills
- **What we use**: design-research (10 skills → user-research refs),
  ui-design (10 skills → ui-design refs), interaction-design
  (9 skills → interaction-design refs), design-validation
  (8 skills → qa + design-system-audit refs), design-ops
  (6 skills → governance + documentation refs), design-writing
  (4 skills → content-writing refs)
- **Last synced**: [date]
- **How to update**: Check for new skills in each plugin. If a new
  skill maps to an existing skill, add as L3 reference. If it's a
  new concern, consider creating a dedicated skill.

### inclusive-design-skills (MC Dean / Owl-Listener)
- **Repo**: https://github.com/Owl-Listener/inclusive-design-skills
- **What we use**: cognitive accessibility, adaptive interfaces,
  inclusive research, accessibility decision records
- **Maps to skills**: accessibility-audit, user-research, ethical-design
- **Last synced**: [date]
- **How to update**: Check for new skills or updates to existing ones.
  Cognitive a11y and inclusive research content goes to KB files.

### Figma Console MCP (TJ Pitre / Southleft)
- **Repo**: https://github.com/southleft/figma-console-mcp
- **What we use**: Tool reference for metadata-extraction skill
- **Last synced**: [date]
- **How to update**: Check for new tools (they add frequently).
  Update skills/metadata-extraction/references/figma-console-mcp.md.

## Update cadence

- **Monthly**: Quick check of each repo's recent commits/releases
- **Quarterly**: Deep sync — read changelogs, adapt new patterns
- **On major release**: Immediate review for breaking changes

## How to sync

1. Read the upstream repo's recent changes
2. Identify which of your skills are affected
3. Update the skill SKILL.md body and/or reference files
4. Re-run trigger evals to verify no regressions
5. Update "Last synced" date in this file
6. Commit with message: "sync: [repo-name] [version/date]"



### Superpowers (Jesse Vincent / obra)
- **Repo**: https://github.com/obra/superpowers
- **What we use**: TDD enforcement, two-stage review, quality gate pattern
- **Maps to skills**: code-gen (TDD integration), code-review (quality gates)
- **Install**: `/plugin marketplace add obra/superpowers-marketplace`
- **Last synced**: [date]
- **Watch for**: New skill additions, updated enforcement patterns

### Vercel web-design-guidelines
- **Repo**: https://github.com/vercel-labs/agent-skills
- **Skill path**: skills/web-design-guidelines/
- **What we use**: 100+ UI/UX rules for code review Layer 7
- **Maps to skills**: code-review (additional rule set)
- **Last synced**: [date]
- **Watch for**: New rules added, existing rules updated

### Playwright MCP
- **Source**: @anthropic/mcp-playwright (npm)
- **What we use**: Browser automation for a11y scanning, visual regression
- **Maps to agents**: accessibility-reviewer (automated scanning)
- **Last synced**: [date]
- **Watch for**: New capabilities, API changes

### wshobson/agents
- **Repo**: https://github.com/wshobson/agents
- **What we use**: UI/UX design plugin for design system context
- **Install**: `/plugin marketplace add wshobson/agents`
- **Last synced**: [date]
- **Watch for**: UI/UX plugin updates, new design-related agents

### airowe/claude-a11y-skill
- **Repo**: https://github.com/airowe/claude-a11y-skill
- **What we use**: Reference for axe-core + jsx-a11y scan integration
- **Maps to skills**: accessibility-audit (scan execution pattern)
- **Last synced**: [date]
