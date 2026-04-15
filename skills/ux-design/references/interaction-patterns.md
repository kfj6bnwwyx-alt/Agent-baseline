# Interaction Patterns

## State management for UI components

Every interactive component passes through states:
```
default → hover → focus → active → [result state]
```

Result states: success, error, loading, disabled, selected.

## Feedback timing
- **Immediate** (<100ms): Button press, toggle, checkbox
- **Short** (100-300ms): Transition animations, drawer open
- **Medium** (300ms-1s): Skeleton → content load
- **Long** (>1s): Show progress indicator. >3s: show estimated time.

## Optimistic vs. confirmed updates
- **Optimistic**: Update UI immediately, roll back on failure.
  Use for: low-risk actions (toggle, like, mark as read).
- **Confirmed**: Wait for server response before updating UI.
  Use for: high-risk actions (delete, payment, send).

## Undo pattern
For destructive actions that are reversible:
1. Execute immediately (optimistic)
2. Show toast with "Undo" action
3. Undo window: 5-10 seconds
4. After window closes, persist the action

## Form patterns
- Validate on blur, not on each keystroke
- Show errors inline, adjacent to the field
- Preserve user input on error (never clear the form)
- Disable submit only during submission, not during validation
- Auto-save drafts for long forms
