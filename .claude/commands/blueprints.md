Generate or regenerate the context engine blueprints.

Use the context-engine agent.

Follow the process in the context-engine skill:
1. Read all contracts from _index.md
2. Read token files
3. Generate each of the 7 blueprint YAML files
4. Generate IDE context files (.windsurfrules, .cursorrules, CLAUDE.md)
5. Generate preview manifests per component
6. Validate completeness

Output to `.ai/context-engine/`.

Scope: $ARGUMENTS (or "all" for full regeneration)
