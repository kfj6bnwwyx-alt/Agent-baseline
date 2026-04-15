# Drift Thresholds

Adapted from design-system-ops (Murphy Trueman): drift-detection.

## Severity levels

| Severity | Condition | Action |
|----------|-----------|--------|
| Critical | Blocked package imported in production | Fix within 24 hours |
| Critical | Hardcoded value overriding token | Fix within 1 sprint |
| High | Component prop diverges from contract | Fix within 2 sprints |
| High | Missing a11y requirement from contract | Fix within 1 sprint |
| Medium | Naming doesn't match convention | Fix when component is next touched |
| Medium | Pattern used without recipe | Create recipe, don't block |
| Low | Style inconsistency within tolerance | Track, batch fix quarterly |

## Acceptable drift

Not all drift is bad. Acceptable cases:
- **Prototype/spike**: Drift is expected and temporary
- **Platform limitation**: Contract requires something the platform can't do (document as ADR)
- **Intentional override**: Approved deviation with ADR (e.g., marketing landing page)

## Drift detection cadence

- **Continuous**: Blocked package linting (CI/CD)
- **Per PR**: Token usage check (code review skill)
- **Weekly**: Contract compliance scan (design-system-audit)
- **Monthly**: Full system health audit (system-health chain)
