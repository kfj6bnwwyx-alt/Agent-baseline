---
name: business-intelligence
description: >
  Connect design system components to business outcomes, define
  component-to-metric mappings, set A/B testing guardrails, and
  configure analytics hooks. Use when the user asks "which components
  drive conversion", "what metrics does this pattern affect", "can
  we A/B test this component", "analytics for this flow", "business
  impact of this design change", or "which KPIs does the modal
  affect". Also triggers on "component metrics", "experiment
  guardrails", "usage analytics", or "ROI of this component".
---

# Business Intelligence

You connect design system decisions to measurable business outcomes.
Every component serves a business function — you make those
connections explicit.

Maps to Murphy Trueman's Business Intelligence Blueprint in the
context engine.

## Component-to-outcome mapping

| Business function | Components | Primary metric |
|-------------------|-----------|---------------|
| Conversion | CTAs, sign-up forms, checkout | Conversion rate |
| Engagement | Content cards, interactive elements | Time on page, interactions/session |
| Retention | Onboarding flows, empty states | Day-7 retention, churn rate |
| Trust | Security indicators, social proof | Trust score, support ticket rate |

## A/B testing guardrails

**Safe to experiment**: Color, copy, size, order, layout
**Never experiment with**: Accessibility features, core interaction patterns, security indicators
**Requires review**: Navigation structure, form flow, error handling

## Anti-metrics

Metrics that must NOT be optimized at the expense of user experience:
- Click-through on dark patterns (manipulative urgency)
- Time on page when it indicates confusion, not engagement
- Form completion when it indicates forced flow, not willingness


## Detailed process

### Step 1: Map components to business functions
For each component in the contract index, identify which business
function it primarily serves: conversion, engagement, retention, or trust.

### Step 2: Identify metrics per function
- Conversion: conversion rate, sign-up rate, checkout completion
- Engagement: time on page, interactions per session, return visits
- Retention: day-7/30 retention, churn rate, reactivation rate
- Trust: support ticket rate, NPS, security incident rate

### Step 3: Define experiment boundaries
For each component, classify what's safe to experiment with:
- Safe: color, copy, size, order, layout
- Requires review: navigation, form flow, error handling
- Never: accessibility features, security indicators, core interactions

### Step 4: Define analytics hooks
What events should be tracked? For each interactive component:
- Render event (is it being shown?)
- Interaction event (is it being used?)
- Completion event (did the user finish the task?)
- Error event (did something go wrong?)

## Output format

```markdown
# Business intelligence: [component/feature]

## Component-outcome mapping
| Component | Business function | Primary metric | Current | Target |
|-----------|------------------|---------------|---------|--------|
| CTAButton | Conversion | Click-through rate | 3.2% | 4.5% |
| OnboardingWizard | Retention | Day-7 retention | 42% | 55% |
| TrustBadge | Trust | Support tickets/week | 15 | <8 |

## Experiment plan: [specific experiment]
**Hypothesis:** Changing CTA color from secondary to primary will
increase click-through by 15%.
**Safe to test:** Yes (color change only, no a11y impact)
**Duration:** 2 weeks minimum for statistical significance
**Anti-metric to watch:** Don't optimize click-through at the cost
of downstream conversion (clicking more but buying less = bad)

## Analytics events
| Component | Event | Data fields | Priority |
|-----------|-------|-------------|----------|
| CTAButton | cta_rendered | page, variant, position | Required |
| CTAButton | cta_clicked | page, variant, destination | Required |
| CTAButton | cta_converted | page, variant, value | Required |
```


## Knowledge references

| File | When to read |
|------|-------------|
| product/metrics-framework.md | Available metrics and targets |
| (BI blueprint from context-engine) | Full component-outcome mapping |
