# Integration Philosophy

## Principle: Own the architecture, delegate the expertise

This kit provides:
- The four-layer design system model (tokens → contracts → context → adapters)
- The 7-dimension component contract schema
- The context engine and 7 blueprint framework
- The orchestration chains and quality gates
- The activation commands and agent routing

It does NOT try to be the best at:
- Token auditing (Murphy's design-system-ops does this better)
- Research methods (MC Dean's designer-skills does this better)
- UI craft decisions (MC Dean's designer-skills does this better)
- TDD enforcement (Superpowers does this better)
- Browser-based testing (Playwright does this better)
- UI rule checking (Vercel's guidelines does this better)

## How skills should integrate

A skill in this kit should:
1. Load YOUR context (contracts, tokens, product brief, personas)
2. Delegate EXECUTION to the best available external skill
3. Apply YOUR quality gates to the output
4. Format output per YOUR templates for the next chain step

A skill should NOT:
- Reconstruct domain expertise that exists in an installable plugin
- Maintain reference files that duplicate upstream content
- Compete with external skills on their core competency

## When to keep knowledge in-house vs. delegate

**Keep in your kit:**
- Contract schema and examples (your IP)
- Four-layer architecture documentation (your IP)
- Quality gate definitions (your governance)
- Chain definitions (your workflow)
- Context bridge formats (your orchestration)
- Team-specific content (brand, tech stack, standards)

**Delegate to external plugins:**
- Audit execution and scoring
- Research method facilitation
- Visual design craft guidance
- Accessibility scanning
- Test enforcement
- UI rule compliance checking

## Maintenance benefit

When you delegate to installed plugins:
- Updates flow automatically on reinstall
- You don't maintain duplicate reference files
- Your skills stay focused on orchestration, not domain content
- Your upstream-tracking.md becomes "check for breaking changes"
  instead of "manually port all changes into our files"

## The reference files we keep

Some reference files in skills/*/references/ remain valuable even
with external plugins installed:
- Output format templates (our format, not theirs)
- Integration guides (how to combine their output with our contracts)
- Mapping files (like figma-to-contract-mapping.md)
- Framework-specific patterns unique to our architecture

Files that could eventually be replaced by plugin delegation:
- skills/user-research/references/ (6 files from MC Dean)
- skills/interaction-design/references/ (2 files from MC Dean)
- skills/ui-design/references/ (2 files from MC Dean)
- skills/ux-design/references/ (3 files from MC Dean)

Keep these as fallbacks for when plugins aren't installed (e.g., on
Windsurf where plugins don't exist), but note in each file that
the installed plugin is the preferred source when available.
