---
name: content-writing
description: >
  UI copy, voice and tone, microcopy, error messages, empty states,
  button labels, and terminology management. Use when the user asks
  about "error message copy", "button label", "empty state text",
  "voice and tone", "microcopy", "placeholder text", "confirmation
  dialog wording", "tooltip text", "onboarding copy", "what should
  this say", or "write the UI text for". Also triggers on "tone of
  voice", "terminology", "content guidelines", or "writing style
  for our product". This is distinct from content-strategy (which
  handles IA and taxonomy) — content-writing handles the actual words.
---

# Content Writing

You write UI text: labels, messages, descriptions, and copy that
follows the system's voice, adapts tone to context, and respects
content patterns.

Maps to Murphy Trueman's Content Blueprint in the context engine.

## Voice and tone

Voice is consistent (the system's personality). Tone adapts to context:
- **Success**: Warm, brief. "Saved" not "Your changes have been successfully saved"
- **Error**: Clear, actionable. "Password too short. Use at least 8 characters"
- **Empty state**: Encouraging, guiding. What will appear + how to start
- **Destructive**: Specific, honest. "Delete this project? This removes all files permanently"
- **Loading**: Brief or silent. Only show text for waits >3 seconds

## Content patterns

| Element | Pattern | Example |
|---------|---------|---------|
| Button labels | Verb + noun, max 3 words | "Save changes", "Delete project" |
| Error messages | What happened + what to do | "Email not found. Check spelling or sign up" |
| Empty states | What goes here + action to start | "No projects yet. Create your first project" |
| Tooltips | One sentence, no period | "Appears on your public profile" |
| Confirmations | Name the specific action | "Delete 'Q3 Report'?" not "Are you sure?" |
| Placeholders | Example format, not instruction | "jane@example.com" not "Enter your email" |

## Knowledge references

| File | When to read |
|------|-------------|
| brand/voice-tone.md | Voice and tone definitions (when populated) |
| accessibility/plain-language.md | Language accessibility rules |
| (content blueprint from context-engine) | Full content specification |
