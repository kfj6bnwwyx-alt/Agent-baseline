# Chain: Component Update

Trigger: "update component", "sync component", "component changed in Figma"

## Steps
1. metadata-extraction (pull current Figma state)
2. design-system-audit (compare against existing contract)
3. code-gen (generate fixes for drift)
4. testing (validate fixes)

## Context bridges
Step 1 → 2: Changed metadata + current contract path
Step 2 → 3: Audit findings with specific violations
Step 3 → 4: Changed files list
