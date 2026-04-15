# Session Memory Patterns

Adapted from design-system-ops (Murphy Trueman): session-memory.

## Purpose
Persist context across sessions so agents don't start from zero each time.
This is especially important for Windsurf (no native session memory)
and Claude.ai (conversations are independent).

## What to remember
- Decisions made in previous sessions (with rationale)
- Components that had issues (prioritize re-checking)
- User preferences (output format, verbosity, tool preferences)
- Project-specific conventions not in the knowledge base yet

## What NOT to remember
- Full conversation history (too large, loses relevance)
- Implementation details that belong in code (use git instead)
- Temporary debugging context (expires with the bug)

## Storage format
```markdown
# Session memory: [project name]
Updated: [timestamp]

## Active decisions
- [decision]: [rationale] (from session [date])

## Watch list
- [component]: [known issue] — check on next audit

## User preferences
- Output format: [preference]
- Verbosity: [preference]

## Project conventions
- [convention not yet in knowledge base]
```

## In Claude Code
Use agent `memory: project` in the subagent definition.
Memory persists at `~/.claude/agent-memory/[project]/`.

## In Windsurf
Generate a handoff doc at session end (see operations/handoff-spec-template.md).
Load it at the start of the next session.

## In Claude.ai
Use the conversation memory system. Key facts are extracted automatically.
For explicit persistence, save a session summary to the project repo.
