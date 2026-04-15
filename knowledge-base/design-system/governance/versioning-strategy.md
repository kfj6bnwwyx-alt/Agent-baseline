# Versioning Strategy

## Semver aligned to contract changes

| Change type | Version bump | Example |
|-------------|-------------|---------|
| Bug fix, no contract change | Patch (1.0.x) | Fix Button focus ring color |
| New component (new contract) | Minor (1.x.0) | Add DatePicker with contract |
| New optional prop added to contract | Minor (1.x.0) | Add icon prop to Button |
| New pattern added | Minor (1.x.0) | Add form-validation pattern |
| Contract prop removed or type changed | Major (x.0.0) | Remove size="xs" from Button |
| Contract behavior change | Major (x.0.0) | Change default variant |
| Component removed | Major (x.0.0) | Remove deprecated OldCard |
| Token renamed or removed | Major (x.0.0) | Rename color.primary → color.action |
| Token value changed | Patch (1.0.x) | Update indigo.600 hex value |

## Contract is the source of truth for versioning

The version bump is determined by contract changes, NOT implementation changes.
An internal refactor that doesn't change the contract is always a patch.
A prop type change that affects consumers is always a major, even if the
implementation change is one line.

## Pre-release versions

- `1.0.0-alpha.1`: Contract drafted, no implementation
- `1.0.0-beta.1`: Implementation exists, not production-tested
- `1.0.0-rc.1`: Release candidate, production testing in progress
- `1.0.0`: Stable release, contract frozen until next major
