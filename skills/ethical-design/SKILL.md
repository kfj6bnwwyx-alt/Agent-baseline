---
name: ethical-design
description: >
  Ethical guardrails for UI design: dark pattern detection and
  prevention, inclusive design enforcement, data privacy patterns,
  consent flows, and bias detection. Use when the user asks about
  "dark patterns", "manipulative UI", "inclusive design rules",
  "consent pattern", "privacy by design", "bias in our interface",
  "confirmshaming", "forced continuity", "hidden costs", or "is
  this ethical". Also triggers on "responsible design", "GDPR
  consent flow", "gender-neutral defaults", or "data handling
  patterns". This is distinct from accessibility (which covers
  WCAG compliance) — ethical design covers manipulation, inclusion,
  and privacy.
---

# Ethical Design

You enforce ethical guardrails — concrete rules that prevent the design
system from being used to manipulate, exclude, or harm users. These are
not aspirational principles but specific prohibitions and requirements.

Maps to Murphy Trueman's Ethical Blueprint in the context engine.

## Dark pattern prohibitions

Each prohibition is a specific pattern the system forbids:

| Pattern | Rule | Bad example | Good example |
|---------|------|-------------|-------------|
| Manipulative urgency | No fake countdown timers or false scarcity | "Only 2 left!" (when untrue) | Show actual stock if relevant |
| Forced continuity | Cancellation must be as easy as sign-up | 5-step cancel, 1-step sign-up | Same flow, same steps |
| Confirmshaming | No guilt language on decline options | "No thanks, I hate saving money" | "No thanks" or "Skip" |
| Hidden costs | All costs visible before commitment | Fees revealed at checkout | Full price shown on product page |
| Misdirection | No visual emphasis steering away from user preference | Tiny "decline" next to huge "accept" | Equal visual weight for both options |
| Roach motel | Easy to enter, must be equally easy to exit | Can't find delete account | Delete in account settings, same depth as create |

## Inclusive design rules

- Gender: never force binary selection. Offer free-text or "prefer not to say"
- Names: support non-Latin characters, no arbitrary length limits, no "first/last" forced split
- Imagery: represent diversity in illustrations, photos, avatars
- Language: gender-neutral defaults, avoid idioms that don't translate
- Cultural: no assumptions about date format, currency, address structure

## Data privacy patterns

- Consent: opt-in for marketing, clear purpose statement per data type
- Display: mask PII by default, reveal on explicit user action
- Retention: state how long data is kept, offer export and deletion
- Notifications: respect frequency preferences, easy to reduce or stop


## Detailed process

### Step 1: Identify the interaction type
Is this: a sign-up flow, a cancellation, a data collection form,
a notification pattern, a pricing display, a personalization system?

### Step 2: Check against dark pattern prohibitions
Run through each prohibition in the table. For each:
- Is there any manipulative urgency?
- Is effort symmetric (as easy to leave as to join)?
- Is the language neutral (no guilt, no shame)?
- Are all costs visible before commitment?
- Is visual emphasis honest (not steering away from user preference)?

### Step 3: Check inclusive design rules
- Gender: free-text or non-binary options?
- Names: no arbitrary limits, non-Latin support?
- Imagery: diverse representation?
- Language: gender-neutral, no idioms?

### Step 4: Check data and privacy
- Is consent opt-in with clear purpose?
- Is PII masked by default?
- Can users export and delete their data?
- Are notification preferences easily reduced?

### Step 5: Check for bias signals
- Does personalization narrow or expand options?
- Do defaults favor the business over the user?
- Is effort symmetric between adding and removing?

## Output format

```markdown
# Ethical review: [feature/flow]
## Result: [pass/issues-found/block]

### [BLOCK] Confirmshaming on cancellation
**Pattern:** Cancel button text says "No, I want to keep paying more"
**Rule:** Decline options must use neutral language
**Fix:** Change to "Cancel subscription" — neutral, specific
**Good example:** "Keep subscription" / "Cancel subscription" (equal weight)

### [ISSUE] Asymmetric effort
**Pattern:** Sign-up is 1 step, cancellation is 5 steps
**Rule:** Cancellation must be as easy as sign-up
**Fix:** Reduce cancellation to 1-2 steps with clear confirmation
**Metric impact:** May reduce short-term retention but increases trust

### [PASS] Data consent
Consent is opt-in, purpose is stated, preferences are accessible.
```

## Example: Reviewing a sign-up flow

Input: "Review the onboarding flow for ethical issues"

Check:
1. Is the "skip" option visually equal to "continue"? (no misdirection)
2. Are optional fields clearly marked? (no forced data collection)
3. Is the privacy policy linked, not buried? (transparency)
4. Can users complete onboarding without marketing opt-in? (consent)
5. Is the "delete account" option as findable as "create account"? (symmetry)


## Knowledge references

| File | When to read |
|------|-------------|
| (ethical blueprint will be generated by context-engine) | Always |
| accessibility/plain-language.md | Content ethics overlap |
