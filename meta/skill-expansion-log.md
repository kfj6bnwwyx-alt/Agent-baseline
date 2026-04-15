# Skill Expansion Log

Track when skills are added, split, or consolidated.

## Current skill count: 23

## History

### v1 — Initial scaffold
20 consolidated skills. Merged 63 designer-skills + 30 design-system-ops
into 20 broader skills for context budget savings.

### v2 — Trigger eval and expansion
Ran trigger evals: 82% accuracy. Identified consolidation-caused failures.
Added 3 new specific skills:
- ethical-design (was missing entirely — Murphy's Ethical Blueprint)
- content-writing (split from content-strategy — voice/tone vs IA)
- business-intelligence (Murphy's BI Blueprint — component-to-metric mapping)
Rewrote all 20 descriptions for trigger precision.

## Decision framework for future skills

**Add a new skill when:**
- A prompt pattern consistently fails to trigger the right skill
- An upstream repo adds a skill for a genuinely new concern
- A team role needs a dedicated tool (e.g., a content writer joins)
- Trigger eval shows a skill's rejection rate is below 70%

**DON'T add a new skill when:**
- The concern can be handled by adding a reference file to an existing skill
- It would duplicate another skill's core responsibility
- It would push total L1 overhead above 4K tokens (~40 skills)

**Split an existing skill when:**
- Trigger eval shows it's catching prompts intended for other skills
- Two distinct user intents are fighting for the same description
- Different team roles need different subsets of the skill's knowledge
