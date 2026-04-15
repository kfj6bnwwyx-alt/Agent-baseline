# Chain: Accessibility Remediation

Trigger: "fix accessibility", "remediate a11y", "fix WCAG issues"

## Steps
1. accessibility-audit (identify issues)
2. code-gen (generate fixes per finding)
3. testing (validate a11y fixes)

## Context bridges
Step 1 → 2: Findings list with severity + specific violations
Step 2 → 3: Changed files + which findings each fix addresses
