# ARIA Patterns

Common ARIA patterns for component development. Reference when building
interactive components.

## Dialog/Modal
```
role="dialog" aria-modal="true" aria-labelledby="[title-id]"
```
- Trap focus inside dialog
- Return focus to trigger on close
- Close on Escape

## Tabs
```
role="tablist" > role="tab" aria-selected="true/false" aria-controls="[panel-id]"
role="tabpanel" aria-labelledby="[tab-id]"
```
- Arrow keys navigate tabs, Tab moves to panel content

## Combobox/Autocomplete
```
role="combobox" aria-expanded="true/false" aria-controls="[listbox-id]"
role="listbox" > role="option" aria-selected="true/false"
```
- Type to filter, arrows to navigate, Enter to select

## Alert/Toast
```
role="alert" or role="status" (non-urgent) aria-live="assertive/polite"
```
- assertive for errors, polite for success messages

## Disclosure
```
<button aria-expanded="true/false" aria-controls="[content-id]">
```
- Toggle visibility of associated content

## General rules
- If it looks like a button, use <button> (not div + onClick)
- If it looks like a link, use <a href> (not span + onClick)
- Every form input needs a visible <label>
- Every image needs alt text (or alt="" if decorative)
- aria-label overrides visible text — use aria-labelledby instead
  when visible text exists
