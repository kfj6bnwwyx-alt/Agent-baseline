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


## Detailed process

### Step 1: Identify the content type
Button label, error message, empty state, tooltip, confirmation,
placeholder, heading, description, or onboarding copy.

### Step 2: Apply voice and tone
Voice is consistent (system personality). Tone adapts to context:
- Success: warm, brief
- Error: clear, actionable
- Empty state: encouraging, guiding
- Destructive: specific, honest
- Loading: brief or silent

### Step 3: Write following content patterns
Each content type has a formula:
- **Button label**: Verb + noun, max 3 words ("Save changes")
- **Error message**: What happened + what to do ("Email not found. Check spelling or sign up.")
- **Empty state**: What goes here + action ("No projects yet. Create your first project.")
- **Tooltip**: One sentence, no period ("Appears on your public profile")
- **Confirmation**: Name the specific action ("Delete 'Q3 Report'?")

### Step 4: Plain language check
- Reading level 8th grade or below
- Active voice ("Click save" not "Save should be clicked")
- Common words ("use" not "utilize")
- One idea per sentence

### Step 5: Accessibility check
- Does it make sense without visual context? (screen reader)
- Is it specific enough? ("Save" is worse than "Save changes")
- Does it avoid idioms? (they don't translate)

## Output format

```markdown
# Content spec: [component/feature]

## [Element]: Button — primary action
**Copy:** "Create account"
**Reasoning:** Verb + specific noun. Not "Submit" (too generic) or
"Sign up" (less formal than the context requires).
**Character count:** 14
**Accessibility:** Descriptive label, screen reader clear

## [Element]: Error — email validation
**Copy:** "Enter a valid email address, like name@example.com"
**Reasoning:** Says what's wrong + shows the expected format.
Not "Invalid input" (too vague) or "Error in field" (no guidance).
**Tone:** Direct, helpful (error context)

## [Element]: Empty state — project list
**Copy:**
Heading: "No projects yet"
Body: "Create a project to start organizing your work."
Action: "Create project" [Button, primary]
**Reasoning:** Names what will appear + clear next action.
Not "Nothing to see here" (dismissive) or just a blank screen.
```

## Example

Input: "Write the error messages for the login form"

```markdown
## Email field — empty
"Enter your email address"

## Email field — invalid format
"Enter a valid email, like name@example.com"

## Password field — empty
"Enter your password"

## Password field — too short
"Password must be at least 8 characters"

## Login — wrong credentials
"Email or password is incorrect. Try again or reset your password."
(Not "Invalid credentials" — too technical. Not "Wrong password" —
reveals which field is wrong, security risk.)

## Login — account locked
"Too many attempts. Try again in 15 minutes, or reset your password."
(Specific time. Clear alternative action.)
```


## Knowledge references

| File | When to read |
|------|-------------|
| brand/voice-tone.md | Voice and tone definitions (when populated) |
| accessibility/plain-language.md | Language accessibility rules |
| (content blueprint from context-engine) | Full content specification |
