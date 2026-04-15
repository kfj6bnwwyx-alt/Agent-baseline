# Claude.ai Activation Guide

Claude.ai doesn't have slash commands, subagents, or file system access
(unless using computer use / code execution). Activation works through
conversation context.

## Setup options

### Option A: Upload the kit as context
Upload relevant files at the start of a conversation:
- For design work: the contract schema + relevant contracts + the skill you need
- For code work: the relevant contract + code-gen or code-review skill
- For auditing: the contract + the audit skill + WCAG checklist

### Option B: Use Claude.ai skills (if available)
Package skills as .skill files (via adapter generator when built) and
install them. They'll trigger automatically based on descriptions.

### Option C: Reference in conversation
Paste the relevant skill's process section into the conversation and
ask Claude to follow it.

## Activation phrases

| What you want | Upload these files + say |
|---------------|------------------------|
| Build a component | Contract + code-gen SKILL.md → "Implement this contract in React" |
| Audit | Contract + audit SKILL.md → "Audit this code against the contract" |
| Write a PRD | product-brief SKILL.md → "Write a PRD for [feature]" |
| Check a11y | Contract + a11y SKILL.md + WCAG checklist → "Is this accessible?" |

## Context budget
Claude.ai has a large context window but no persistent file access.
Upload only what's needed for the current task. Don't upload the
entire knowledge base — it wastes context on irrelevant information.
