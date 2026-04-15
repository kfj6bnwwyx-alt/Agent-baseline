# Windsurf Activation Guide

Windsurf (Cascade) doesn't have slash commands or native subagents.
Activation works through natural language + the .windsurfrules file.

## Setup
1. Copy `.windsurfrules.example` to your project root as `.windsurfrules`
2. Cascade reads this file automatically on every request
3. The rules file tells Cascade about your design system constraints

## Activating skills

Since Cascade can't route to subagents, you activate skills by being
specific in your prompts. The .windsurfrules file primes Cascade with
context, but you need to tell it which skill's process to follow.

### Pattern: Reference the skill directly

Instead of: "Build a Button component"
Say: "Build a Button component following the code-gen skill process in skills/code-gen/SKILL.md. Load the contract from knowledge-base/design-system/contracts/button.contract.yaml first."

### Pattern: Reference the chain for multi-step work

Instead of: "Review this feature"
Say: "Run the feature-review chain from orchestration/chains/feature-review.chain.md against this component."

### Pattern: Load knowledge explicitly

Instead of: "Is this accessible?"
Say: "Audit this for accessibility using the process in skills/accessibility-audit/SKILL.md. Check against the contract's Dimension 3 and knowledge-base/accessibility/wcag-checklist.md."

## Key activation phrases for Windsurf

| What you want | Say this |
|---------------|---------|
| Audit a component | "Audit [X] against its contract following skills/design-system-audit/SKILL.md" |
| Build from contract | "Implement [X] from its contract using skills/code-gen/SKILL.md" |
| Review code | "Review this code using the 6-layer process in skills/code-review/SKILL.md" |
| Check accessibility | "Run an a11y audit using skills/accessibility-audit/SKILL.md" |
| Generate blueprints | "Generate context engine blueprints using skills/context-engine/SKILL.md" |
| Write a PRD | "Write a PRD using the format in skills/product-brief/SKILL.md" |
| Run a chain | "Follow the [chain-name] chain in orchestration/chains/[name].chain.md" |

## Context window management in Windsurf

Windsurf has a ~128K context window (smaller than Claude's 200K).
Be explicit about which files to load:
- "Load ONLY the Button contract and the code-gen skill — don't load the full knowledge base"
- "For this audit, load the contract and the WCAG summary (not the full checklist)"
- If context feels bloated: "Start fresh. Here's the handoff: [summary]"

## Creating Windsurf rules from the kit

The adapter generator (when built) will compile your skills into a
single .windsurfrules file. Until then, the .windsurfrules.example
in adapters/windsurf/ gives the manual version.
