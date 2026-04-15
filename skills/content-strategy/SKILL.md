---
name: content-strategy
description: >
  Information architecture, content structure, taxonomy design,
  navigation labeling, content modeling, and content governance. Use
  when the user asks about "information architecture", "IA audit",
  "taxonomy for our docs", "navigation structure", "how to organize
  content", "labeling system", "content model", or "site structure".
  Also triggers on "card sort results", "tree testing", or "content
  audit". Do NOT use for writing actual copy or UI text (voice, tone,
  microcopy — those need a content-writing skill), visual styling
  (ui-design), or implementation (code-gen).
---

# Content Strategy

You design information architectures, content models, and taxonomies
that make products navigable and content findable.

## IA process

1. **Content inventory**: What exists? Catalog all content types,
   volumes, owners, freshness.

2. **User mental models**: How do users think about this content?
   Card sort results, search analytics, support tickets.

3. **Taxonomy design**: Categories, labels, hierarchies. Use
   user language, not internal jargon. Test with tree testing.

4. **Navigation structure**: Global nav, local nav, breadcrumbs,
   search. Optimize for the top 5 user tasks.

5. **Content model**: Structured content types with required fields,
   relationships, and governance rules.


## Detailed process

### Step 1: Content inventory
What exists? Catalog by: content type, volume, owner, freshness, quality.
Flag content that's outdated, duplicated, or orphaned.

### Step 2: User mental models
How do users think about this content?
Sources: card sort results, search analytics, support tickets, interviews.
What language do they use? (Use their words, not internal jargon.)

### Step 3: Design the taxonomy
Categories, labels, hierarchies based on user mental models.
Test with tree testing: can users find content without seeing the UI?

### Step 4: Design navigation
Map the taxonomy to navigation patterns:
- Global nav: top 5-7 categories
- Local nav: within-section navigation
- Search: for everything else
- Cross-links: related content connections

### Step 5: Define the content model
Structured content types with: required fields, relationships,
governance rules (who owns, update cadence, retirement criteria).

## Output format

```markdown
# Information architecture: [domain]

## Content inventory summary
| Type | Count | Avg age | Owner | Quality |
|------|-------|---------|-------|---------|
| Help articles | 156 | 8 months | Support | Mixed |
| API docs | 42 | 2 months | Eng | Good |

## Taxonomy
### Level 1: [category]
  - Level 2: [subcategory]
    - Level 3: [topic]
    
## Navigation structure
| Location | Pattern | Contents |
|----------|---------|----------|
| Global nav | Hub and spoke | [top categories] |
| Help center | Faceted | by product area + by task |
| API docs | Nested hierarchy | by resource type |

## Content model: Help article
| Field | Required | Type | Governance |
|-------|----------|------|------------|
| Title | yes | text, <60 chars | Author |
| Body | yes | markdown | Author |
| Product area | yes | taxonomy term | Author |
| Last reviewed | yes | date | Auto + owner |
| Retirement date | no | date | Owner |
```


## Knowledge references

| File | When to read |
|------|-------------|
| references/ia-patterns.md | Common IA patterns |
| research/personas/ | Who's navigating this content |
| product/product-brief.md | Product scope context |
