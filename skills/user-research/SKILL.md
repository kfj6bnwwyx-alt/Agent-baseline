---
name: user-research
description: >
  User research methods: persona creation, journey mapping, interview
  guides, usability test plans, affinity diagrams, diary studies, card
  sorts, and Jobs-to-Be-Done analysis. Use when the user mentions
  research, personas, interviews, usability testing, journey maps,
  user insights, or synthesis. Also triggers on "understand our users",
  "plan a study", or "what do users need".
---

# User Research

You guide research planning, execution, and synthesis.

Consolidates 10 skills from designer-skills (MC Dean): user-persona,
empathy-map, journey-map, interview-script, summarize-interview,
usability-test-plan, diary-study-plan, affinity-diagram, jobs-to-be-done,
card-sort. Plus inclusive research methods from inclusive-design-skills.


## Detailed process

### Step 1: Define research questions
What do you want to LEARN? (Not what you'll ask — that comes later.)
Research questions guide method selection.

### Step 2: Choose method
Match method to question:
- "Who are our users?" → Persona creation (refs/persona-framework.md)
- "What's their experience like?" → Journey mapping (refs/journey-mapping.md)
- "What do they think about X?" → Interviews (refs/interview-methods.md)
- "Can they use X?" → Usability testing (refs/usability-testing.md)
- "What patterns exist in the data?" → Synthesis (refs/synthesis-techniques.md)
- "What do they actually need?" → JTBD analysis (refs/synthesis-techniques.md)
- "Diverse/vulnerable population?" → Also load refs/inclusive-research.md

### Step 3: Plan the study
Participant criteria, recruitment, compensation, logistics, timeline.
For usability tests: tasks, success criteria, metrics.
For interviews: guide with warm-up, exploration, wrap-up.

### Step 4: Execute
Follow the method-specific guide in references.
Record with consent. Take notes in real-time.

### Step 5: Synthesize
Transform raw data into insights using synthesis techniques:
affinity diagramming, JTBD mapping, insight cards.

## Output format (varies by method)

### Persona
```markdown
# [Name] — [Archetype]
## Demographics: [age range, role, tech comfort]
## Goals: [primary, secondary]
## Frustrations: [specific, evidence-based]
## Behaviors: [how they currently solve this]
## Context: [where, when, with whom]
## Quote: "[Representative statement]"
```

### Usability test results
```markdown
# Usability test: [feature]
## Participants: [N], [criteria]
## Task results
| Task | Completion | Avg time | Errors | Key observation |
|------|-----------|----------|--------|-----------------|
| [task] | 4/5 (80%) | 2:15 | 3 | Hesitated at step 2 |
## Top findings (by severity × frequency)
1. [finding]: [evidence], [recommendation]
```

### Interview synthesis
```markdown
# Research synthesis: [topic]
## Participants: [N], [criteria]
## Insight 1: [title]
**Evidence:** [N] participants mentioned this
**Pattern:** [what we observed]
**So what:** [why it matters]
**Now what:** [recommendation]
```

## Example: Planning a usability test

Input: "Plan a usability test for the new checkout flow"

Load `references/usability-testing.md`, then produce:
- 3-5 tasks with specific success criteria and time limits
- Participant criteria matching target persona
- Metrics: completion rate (>80%), time on task, error rate, satisfaction
- Facilitation notes: don't lead, note hesitation, ask "what are you thinking?"


## Knowledge references

| File | When to read |
|------|-------------|
| references/persona-framework.md | Creating or refining personas |
| references/journey-mapping.md | Mapping user journeys |
| references/interview-methods.md | Preparing interview scripts |
| references/synthesis-techniques.md | Affinity diagrams, JTBD |
| references/usability-testing.md | Planning usability tests |
| references/inclusive-research.md | Diverse or vulnerable populations |
| research/templates/interview-guide.md | Interview guide template |



## Delegation to MC Dean's designer-skills

When designer-skills is installed, delegate method execution:

| Research task | Your skill does | MC Dean's skill does |
|--------------|----------------|---------------------|
| Persona creation | Define output format, link to product context | Guide through demographics, goals, behaviors, context |
| Journey mapping | Define touchpoints from your product, link to contracts | Facilitate stage × dimension mapping |
| Interviews | Load product context, define research questions | Guide script creation, facilitation techniques |
| Usability testing | Define tasks from acceptance criteria, link to contracts | Guide test plan, metrics, facilitation |
| Synthesis | Define insight format for your team | Guide affinity diagramming, JTBD extraction |
| Inclusive research | Load inclusive design requirements from ethical skill | Guide accommodation, recruitment, analysis |

### Combined workflow pattern
```
1. YOUR skill: Load product context + relevant contracts + personas
2. MC DEAN's skill: Execute the research method with domain expertise
3. YOUR skill: Format output per your team's template
4. YOUR skill: Feed output to the next chain step (via context bridge)
```

Your skill owns the context (what you're researching and why).
MC Dean's skill owns the method (how to do the research well).
