# Chain: Contract from Scratch

Trigger: "create a contract for", "new component contract", "write the contract"

## Steps
1. metadata-extraction (if Figma source exists — skip if designing from scratch)
2. ux-design (define interaction patterns and states)
3. ui-design (define token mappings and visual spec)
4. accessibility-audit (define a11y requirements)
5. documentation (assemble into 7-dimension contract YAML)
6. governance (register in _index.md, create decision record)

## Context bridges
Step 1 → 2: Raw component metadata (or "no Figma source" flag)
Step 2 → 3: Interaction spec with states and transitions
Step 3 → 4: Visual spec with token mappings
Step 4 → 5: A11y requirements
Step 5 → 6: Completed contract file path

## Quality gate
After step 5, run design-system-audit on the new contract against
_contract-schema.md to verify all 7 dimensions are populated.
