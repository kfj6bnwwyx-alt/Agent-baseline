# Chain: Feature Review

**Trigger:** "full review", "pre-release check", "review this feature"

## Steps (PARALLEL — each agent gets fresh context)

### 1a. design-system-audit
**Agent:** design-system-auditor (Sonnet)
**Loads:** Relevant contracts, _contract-schema.md
**Output:** Contract compliance report with findings

### 1b. accessibility-audit
**Agent:** accessibility-reviewer (Sonnet)
**Loads:** wcag-checklist.md, aria-patterns.md, relevant contracts Dim 3
**Output:** WCAG compliance report

### 1c. code-review
**Agent:** code-reviewer (Sonnet)
**Loads:** code-standards.md, anti-patterns.md, tech-stack.md
**Output:** Code quality report with severity

### 1d. qa
**Agent:** qa-engineer (Sonnet)
**Loads:** acceptance criteria from product brief, relevant contracts
**Output:** QA report with edge cases found

### 2. merge (parent session)
Aggregate all 4 reports. Deduplicate findings across reports.
Produce unified review with priority ordering.

## Ship/no-ship recommendation
- Any CRITICAL finding = block
- 3+ HIGH findings = block
- HIGH findings with workarounds = conditional ship with follow-up tickets

## Total context budget: ~32K across 4 parallel agents (~8K each)
