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

## Knowledge references

| File | When to read |
|------|-------------|
| product/metrics-framework.md | Available metrics and targets |
| (BI blueprint from context-engine) | Full component-outcome mapping |
