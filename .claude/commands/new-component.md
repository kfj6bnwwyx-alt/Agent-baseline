Run the new-component chain for $ARGUMENTS.

Follow the chain definition in `orchestration/chains/new-component.chain.md`.

Steps:
1. Use the metadata-extractor agent to pull component data from Figma (if Figma source exists)
2. Use the ux-designer agent to define interaction patterns and states
3. Use the ui-designer agent to define token mappings and visual spec
4. Use the code-generator agent to implement from the contract
5. Use the accessibility-reviewer agent to audit the implementation
6. Use the test-writer agent to write contract tests

Between each step, produce a structured context bridge (see `knowledge-base/operations/handoff-spec-template.md`).

After step 4, run a quality gate: use the design-system-auditor agent to verify the implementation matches the contract. If critical findings exist, loop back to code-generator with the findings.

Component name: $ARGUMENTS
