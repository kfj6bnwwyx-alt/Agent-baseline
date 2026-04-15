# Chain: Full Rebrand

Trigger: "rebrand", "new brand", "brand refresh", "update all brand tokens"

## Steps
1. ui-design (define new color, typography, spacing tokens)
2. metadata-extraction (extract new brand assets from Figma if available)
3. context-engine (regenerate all 7 blueprints + context files)
4. design-system-audit (audit all components against new tokens)
5. code-gen (fix token references in components that need updating)
6. testing (run full test suite against new tokens)
7. governance (document the rebrand, update decision log, notify consumers)

## This is the longest chain — use session breaks
Steps 1-2: Session 1 (define the new brand)
Steps 3-4: Session 2 (regenerate and audit)
Steps 5-6: Session 3 (fix and test)
Step 7: Session 4 (governance and communication)

## Context bridges are critical here
Each session handoff doc must include: what tokens changed, which
components are affected, what's been fixed vs outstanding.
