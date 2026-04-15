# Component Patterns

## Core patterns

**Modal/Dialog**: Requires explicit action to dismiss. Traps focus.
Use for: confirmations, destructive actions, complex forms that
shouldn't lose context. Don't use for: information that can be
inline, simple choices (use popover instead).

**Sheet/Drawer**: Slides from edge. Doesn't trap focus by default.
Use for: supplementary content, filters, secondary navigation.
Prefer bottom sheets on mobile, side sheets on desktop.

**Toast/Snackbar**: Transient, auto-dismisses. No required action.
Use for: success confirmations, non-critical info. Don't use for:
errors (those need persistence) or actions (use dialog).

**Popover**: Anchored to trigger element. Light dismiss.
Use for: contextual info, small forms, menus. Don't use for:
complex content or anything requiring scrolling.

**Empty state**: What shows when there's no data yet.
Always include: illustration/icon, explanation, primary action.
Never show a blank screen or just "No results."

**Loading skeleton**: Shape-matched placeholder during data fetch.
Prefer over spinners for predictable content. Match the layout
of the loaded state exactly.

**Error state**: What shows when something fails.
Always include: what happened, why (if known), what to do next.
Never show raw error codes or stack traces.
