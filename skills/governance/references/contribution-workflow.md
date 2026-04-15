# Contribution Workflow

Adapted from design-system-ops (Murphy Trueman): contribution-workflow.

## Proposal process

1. **Request**: Open a proposal issue with:
   - What component/pattern/token is needed
   - Which teams need it and how many
   - Existing workarounds (screenshots/code)
   - Rough complexity estimate

2. **Triage**: DS team reviews weekly. Outcomes:
   - **Accept**: Assign to sprint, create contract first
   - **Defer**: Add to backlog with rationale
   - **Redirect**: Existing component/pattern handles this
   - **Reject**: Doesn't fit the system (explain why)

3. **Contract-first development**:
   - Write the Layer 2 contract YAML before any code
   - Review contract with consuming teams
   - Implement Layer 4 adapter against approved contract
   - Run design-system-audit against contract
   - Update Layer 3 context files via context-engine

4. **Release**:
   - Version bump per semver
   - Migration guide if breaking
   - Update manifest and _index.md
   - Regenerate context files

## Contribution from non-DS teams

Product teams can propose Layer 2b patterns:
- Must reference existing contracts by name
- Cannot modify existing contracts
- DS team reviews composition rules
- Approved patterns enter the pattern catalog
