# Chain: New Component

**Trigger:** "new component", "build from scratch", "create [X] component"

## Steps

### 1. metadata-extraction (if Figma source exists)
**Agent:** metadata-extractor (Haiku)
**Loads:** _contract-schema.md, figma-console-mcp.md
**Output:** [component].contract.yaml (draft) + token updates
**Bridge to next:** Contract path + extraction coverage summary (~200 tokens)

### 2. ux-design
**Agent:** ux-designer (Sonnet)
**Loads:** component-patterns.md, layout-principles.md, contract from step 1
**Output:** Interaction spec with states, transitions, error paths
**Bridge to next:** State machine + component list + pattern references (~300 tokens)

### 3. ui-design
**Agent:** ui-designer (Sonnet)
**Loads:** brand-guidelines.md, tokens, contract
**Output:** Token mapping per state, visual hierarchy, dark mode verification
**Bridge to next:** Token mappings + state treatments summary (~250 tokens)

### 4. code-gen
**Agent:** code-generator (Sonnet)
**Loads:** contract, platform adapter, strategy summary, tech-stack.md
**Output:** Component implementation + co-located tests
**Quality gate:** → design-system-auditor runs contract compliance check
  - If critical/high findings: loop back to code-gen with findings (max 2 loops)
  - If pass: continue to step 5

### 5. accessibility-audit
**Agent:** accessibility-reviewer (Sonnet)
**Loads:** contract Dimension 3, wcag-checklist.md, aria-patterns.md
**Output:** A11y audit report
**Quality gate:**
  - If critical (missing keyboard, no SR): loop back to code-gen (max 1 loop)
  - If medium/low: document as known issues, continue

### 6. testing
**Agent:** test-writer (Sonnet)
**Loads:** contract, code from step 4
**Output:** Contract tests + a11y tests + interaction tests

## Total context budget: ~17K orchestrated (vs ~62K naive sequential)
## Duration: ~15-25 minutes with subagents
