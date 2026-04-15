# Chain: Parity Check (Figma vs Code)

Trigger: "check parity", "compare Figma to code", "is the code matching Figma"

## Steps
1. metadata-extraction (pull current Figma state via Console MCP)
2. design-system-audit (compare extracted metadata against existing contract)
3. code-review (compare implementation against contract)
4. documentation (produce parity report with specific divergences)

## Context bridges
Step 1 → 2: Extracted metadata + current contract path
Step 2 → 3: Contract compliance findings (Figma-side)
Step 3 → 4: Code compliance findings + Figma findings for combined report

## Output
Parity report showing Figma ↔ Contract ↔ Code alignment per dimension.
Divergences flagged with which side is "correct" (contract is source of truth).
