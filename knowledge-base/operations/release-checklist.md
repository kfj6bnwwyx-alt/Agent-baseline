# Release Checklist

## Pre-release
- [ ] All acceptance criteria pass (qa skill)
- [ ] Contract compliance verified (design-system-audit)
- [ ] Accessibility audit complete (accessibility-audit)
- [ ] Performance within budget
- [ ] Tests passing (unit, integration, a11y)
- [ ] Documentation updated (component docs, changelog)
- [ ] Migration guide written (if breaking change)
- [ ] Layer 3 context files regenerated (context-engine)

## Release
- [ ] Version bumped per semver
- [ ] Changelog published
- [ ] Package published to registry
- [ ] Contract _index.md updated with new status/date
- [ ] Preview manifests regenerated

## Post-release
- [ ] Verify published package works in consuming projects
- [ ] Notify consuming teams (if breaking change)
- [ ] Update deprecation schedule (if replacing old component)
- [ ] Run drift detection on consuming projects
