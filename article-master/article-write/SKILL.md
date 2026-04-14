---
name: article-write
description: >
  Steps 7-10 of the article pipeline: SEO brief generation, first draft
  (Gulpease 60-70), gap analysis vs competitors, and second draft integrating gaps.
  Reads research from disk, produces a complete draft.
metadata:
  version: "4.0"
  phase: 2-of-3
  steps: "7-10"
---

# Article Write — Steps 7-10

Transform research into a complete, publication-ready draft.

## Input

Read the research file: `research/article-<slug>-research.md`
Read workspace: BRAND.md, TOV.md, AUDIENCE.md, PILLARS.md
Read the appropriate reference:
- Blog → `article-master/references/blog-guidelines.md`
- Landing → `article-master/references/landing-page-guidelines.md`

---

## Step 7: Brief — SEO Metadata + Writing Instructions

Generate the SEO brief that guides the draft. This is the contract between research and writing.

### For Blog Articles

```markdown
## Step 7: Article Brief

### SEO Metadata
| Field | Value |
|-------|-------|
| Target keyword | [from research] |
| Secondary keywords | [5-10 to include naturally] |
| Title tag | [≤60 chars, keyword in first half] |
| Title alt 1 | [alternative] |
| Title alt 2 | [alternative] |
| Meta description | [≤155 chars, includes CTA] |
| Meta alt | [alternative] |
| H1 | [contains keyword naturally] |
| URL slug | /blog/[slug]/ |
| Schema | BlogPosting + FAQPage (if FAQ section) |

### Writing Instructions
| Field | Instruction |
|-------|-------------|
| Word count | [target from research: competitor avg + 20%] |
| Readability | Gulpease index 60-70 (accessible but not childish) |
| Sentence length | Max 20-25 words per sentence |
| Paragraph length | Max 3-4 sentences |
| Voice | [from TOV.md → Web/SEO → Blog post] |
| Audience | [from AUDIENCE.md segment] |
| Pillar | [from PILLARS.md] |
| Anti-learnings | [from LEARNINGS.md — patterns to avoid] |

### Section-by-Section Instructions
| # | H2 | Word target | Must include | Internal link opportunity |
|---|-----|-------------|-------------|--------------------------|
| 1 | [from research outline] | [words] | [key points] | [link to existing page] |
| 2 | ... | | | |

### Featured Snippet Strategy
| Field | Value |
|-------|-------|
| Target H2 | [which heading to optimize for snippet] |
| Format | paragraph / list / table |
| Answer length | 40-60 words, direct answer first |
```

### For Landing Pages

```markdown
## Step 7: Landing Page Brief

### SEO Metadata
| Field | Value |
|-------|-------|
| Target keyword | [from research] |
| Title tag | [≤60 chars, keyword + brand] |
| Meta description | [≤155 chars, benefit + CTA] |
| H1 | [benefit-driven, keyword natural] |
| URL | /[slug]/ |
| Schema | Product or WebPage + BreadcrumbList |

### Section-by-Section Instructions
| # | Section | Purpose | Word target | CTA? |
|---|---------|---------|------------|:----:|
| 1 | Hero | Capture + convert | 30-50 | Yes |
| 2 | Value props | Why this product | 60-80 | No |
| 3 | Social proof | Trust | 40-60 | No |
| 4 | Products | Browse/select | 20-40 | Yes |
| 5 | Education | Overcome objections | 100-150 | No |
| 6 | Final CTA | Convert | 20-30 | Yes |

### Design Direction
- Button: [from BRAND.md → Design tokens → Buttons → Primary]
- Hero image: [description]
- Mobile: CTA visible without scrolling
```

---

## Step 8: Draft 1 — First Draft

Write the complete article following the brief from Step 7.

### Writing Rules

**Readability target: Gulpease 60-70**
- Sentences: max 20-25 words
- Paragraphs: max 3-4 sentences
- Use active voice
- One idea per paragraph
- Use bullet lists for 3+ items
- Explain jargon naturally (per TOV.md)

**For Blog:**
- Write in the brand voice (TOV.md → Web/SEO → Blog)
- Include keyword in: title, H1, first 100 words, 1-2 H2s, conclusion
- Keyword density: 0.5-1.5% (natural, never forced)
- Each H2 section: topic paragraph → supporting detail → evidence/example
- If targeting a snippet: answer the question in the first 40-60 words under the H2

**For Landing:**
- Write in landing voice (TOV.md → Web/SEO → Landing page)
- Every word must earn its place — 300-500 total
- Benefit-first, feature-second
- CTA: "Discover", "Explore", "Shop the collection" (never "Buy now" or "Click here")

### Structure for Blog Draft

```markdown
# [H1]

[Intro: 50-80 words. Hook → context → what you'll learn. Keyword in first 100 words.]

## [H2 from brief]

[Content per brief instructions. 200-300 words. Include secondary keyword.]

[Image suggestion: description of ideal image, alt text]

## [H2 — PAA question verbatim]

[Direct answer: 40-60 words — this is the snippet target.]

[Extended answer: 100-200 more words with detail, examples, data.]

... [repeat for each H2]

## Conclusion

[Summary of key points. 50-80 words. CTA to relevant product/category. Internal link.]

---
*Written by [brand_name] · Last updated: [date]*
```

### Draft 1 Output

Save to: `content/article-<slug>-draft.md` with frontmatter:

```yaml
---
type: article-draft
version: 1
keyword: [primary keyword]
format: blog | landing
word_count: [actual]
target_word_count: [from brief]
gulpease: [estimated]
date: YYYY-MM-DD
status: draft-1
---
```

---

## Step 9: Gap Analysis — Draft vs Competitors

Compare Draft 1 against the top 3 competitors from research.

### Gap Check Matrix

```markdown
## Step 9: Gap Analysis

### Topic Coverage
| Topic/Subtopic | Comp 1 | Comp 2 | Comp 3 | Our Draft | Gap? |
|---------------|:------:|:------:|:------:|:---------:|:----:|
| [topic] | ✓ | ✓ | ✓ | ✓ | No |
| [topic] | ✓ | ✓ | ✓ | ✗ | YES |
| [topic] | ✓ | | ✓ | ✗ | Maybe |

### Keyword Coverage
| Keyword | In competitors | In our draft | Action |
|---------|:--------------:|:------------:|--------|
| [secondary kw] | 3/3 | Yes | OK |
| [secondary kw] | 3/3 | No | ADD |
| [LSI term] | 2/3 | No | Consider |

### Structural Gaps
- [ ] Missing H2 that all competitors have?
- [ ] Word count below target?
- [ ] Missing FAQ section that competitors have?
- [ ] Missing data/statistics that competitors cite?
- [ ] Missing visuals/diagrams that competitors use?

### Gaps to Fix in Draft 2
1. [specific gap + where to add it]
2. [specific gap + where to add it]
3. [specific gap + where to add it]
```

---

## Step 10: Draft 2 — Integrate Gaps

Revise Draft 1 to fill the gaps identified in Step 9.

**Rules:**
- Add missing topics/subtopics where they fit naturally (don't just append)
- Add missing secondary keywords (weave in, don't stuff)
- Expand thin sections that competitors cover more deeply
- Maintain Gulpease 60-70 after additions
- Don't bloat — if a gap isn't valuable for the reader, skip it
- Update word count in frontmatter

### Draft 2 Output

Update `content/article-<slug>-draft.md`:
- Change frontmatter `version: 2`, `status: draft-2`
- Update `word_count` to new count
- Add a `## Changelog` section at the bottom:

```markdown
## Changelog
### Draft 2 (YYYY-MM-DD)
- Added section on [topic] (Gap #1)
- Expanded [H2] with data from [source] (Gap #2)
- Added secondary keyword "[keyword]" in sections 2, 4 (Gap #3)
- Word count: [old] → [new]
```

End with:
```
**Draft complete.** Run `/article-finalize` to validate and produce the final version.
```
