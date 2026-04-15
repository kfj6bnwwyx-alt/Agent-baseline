# Chain: System Health

**Trigger:** "how healthy", "system health", "full audit"

## Steps (PARALLEL where possible)

### 1a. Token audit
**Agent:** design-system-auditor (Sonnet)
**Loads:** tokens/_schema.md, all token files
**Focus:** DTCG compliance, naming, coverage, orphaned tokens
**Output:** Token health report

### 1b. Component audit
**Agent:** design-system-auditor (Sonnet)
**Loads:** _index.md, all contracts, sample implementations
**Focus:** Contract coverage, implementation compliance, naming
**Output:** Component health report

### 1c. Accessibility scan
**Agent:** accessibility-reviewer (Sonnet)
**Loads:** wcag-checklist.md, all contracts Dimension 3
**Focus:** System-wide a11y compliance
**Output:** A11y health report

### 2. Drift detection
**Agent:** design-system-auditor (Sonnet)
**Loads:** contracts + implementations + drift-thresholds.md
**Input:** Results from 1a-1c
**Output:** Drift report with severity per threshold

### 3. Health dashboard
**Agent:** governance-lead (Opus)
**Loads:** four-layer-strategy.md, metrics-framework.md, all reports from above
**Output:** Aggregated health dashboard with trends + remediation roadmap

## Metrics produced
| Metric | Source |
|--------|--------|
| Token coverage % | Token audit |
| Contract coverage % | Component audit |
| A11y compliance % | A11y scan |
| Drift velocity | Drift detection |
| Context file freshness | Governance check |

## Total context budget: ~26K across parallel agents
