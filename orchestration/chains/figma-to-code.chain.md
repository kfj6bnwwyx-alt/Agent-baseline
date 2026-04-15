# Chain: Figma to Code

**Trigger:** "sync from Figma", "extract and build", "Figma to code"

## Steps

### 1. metadata-extraction
**Agent:** metadata-extractor (Haiku)
**Loads:** _contract-schema.md, figma-console-mcp.md, _schema.md
**Output:** Updated contracts + token files
**Bridge to next:** List of changed contracts + diff summary (~200 tokens)

### 2. context-engine
**Agent:** context-engine (Sonnet)
**Loads:** four-layer-strategy.md, _index.md, all changed contracts
**Output:** Regenerated blueprints + IDE context files + preview manifests
**Bridge to next:** Regenerated file list + validation result (~150 tokens)

### 3. code-gen
**Agent:** code-generator (Sonnet)
**Loads:** Updated contracts, platform adapter, regenerated context
**Output:** Implementation code conforming to updated contracts
**Quality gate:** → design-system-auditor checks contract compliance
  - If findings: loop back with fixes (max 2 loops)

## Total context budget: ~14K orchestrated (vs ~38K naive)
