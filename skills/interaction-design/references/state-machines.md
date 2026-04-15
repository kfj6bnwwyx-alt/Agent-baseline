# State Machine Patterns

Adapted from designer-skills (MC Dean): state-machine.

## When to use state machines
- Component has >3 states
- Transitions have conditions or side effects
- "Impossible states" need to be prevented
- Multiple actors can change state (user, server, timer)

## Format

```
States: idle, loading, success, error, empty
Initial: idle

Transitions:
  idle → loading     [trigger: fetch]
  loading → success  [trigger: data received, guard: data.length > 0]
  loading → empty    [trigger: data received, guard: data.length === 0]
  loading → error    [trigger: fetch failed]
  error → loading    [trigger: retry, max: 3]
  success → loading  [trigger: refresh]
  empty → loading    [trigger: refresh]

Side effects:
  enter loading: show skeleton, start timeout(30s)
  enter error: log to analytics, show error message
  enter success: hide skeleton, announce to screen reader
  timeout in loading: transition to error("timeout")
```

## Common component state machines

**Async data component**: idle → loading → success | error | empty
**Form field**: pristine → dirty → validating → valid | invalid
**Toggle**: off → on (with optimistic + rollback)
**Multi-step wizard**: step1 → step2 → ... → stepN → complete
