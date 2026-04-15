# Chain: Component Update

**Trigger:** "update component", "sync component", "component changed in Figma"

## Steps

### 1. metadata-extraction
**Agent:** metadata-extractor (Haiku)
**Loads:** Existing contract, _contract-schema.md, figma-console-mcp.md
**Output:** Updated contract with diff against previous version
**Bridge to next:** Contract diff summary + changed dimensions (~250 tokens)

### 2. design-system-audit
**Agent:** design-system-auditor (Sonnet)
**Loads:** Old contract, new contract, current implementation
**Output:** Gap report — what implementation needs to change
**Bridge to next:** Specific changes needed with file paths (~300 tokens)

### 3. code-gen
**Agent:** code-generator (Sonnet)
**Loads:** Updated contract, platform adapter, gap report from step 2
**Output:** Updated implementation code
**Quality gate:** → auditor re-checks contract compliance (max 2 loops)

### 4. testing
**Agent:** test-writer (Sonnet)
**Loads:** Updated contract, updated implementation
**Output:** Updated tests + regression check

## Total context budget: ~16K orchestrated
