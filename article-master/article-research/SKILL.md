---
name: article-research
description: >
  Steps 1-6 of the article pipeline: SERP analysis, heading extraction, structure
  outline, content depth analysis, semantic context mapping, and insights extraction.
  Produces a research document that feeds the writing phase.
metadata:
  version: "4.0"
  phase: 1-of-3
  steps: "1-6"
---

# Article Research — Steps 1-6

Analyze the SERP landscape for a keyword and produce a comprehensive research document.

## Input

- **Keyword** (required): the target keyword
- **Page type**: blog or landing (from orchestrator)
- **Context**: workspace files already loaded by orchestrator

## Step 1: SERP — Top 10 Competitor Analysis

**With DataForSEO:** Call `mcp__dfs__serp_organic_live_advanced` with depth: 10 for the target keyword.

**Without DataForSEO (fallback):** Use web search to find the top 10 ranking pages for the keyword. Open each URL and extract the data manually. This is slower but produces the same output.

For each of the top 10 results, extract:

| Field | How |
|-------|-----|
| URL | From SERP data |
| Title | From SERP data |
| Position | From SERP data |
| Content type | Classify: guide, listicle, how-to, comparison, product page, landing |
| Word count | From SERP snippet or content parsing |
| Domain authority | From SERP data if available |

Also extract SERP features present:
- Featured Snippet (type: paragraph, list, table)
- People Also Ask (list all questions)
- Image Pack
- Video carousel
- Knowledge Panel
- Shopping results
- AI Overview

**Output table:**
```markdown
## Step 1: SERP Analysis — "[keyword]"

### Top 10 Results
| # | URL | Title | Type | Est. Words | SERP Features |
|---|-----|-------|------|-----------|---------------|

### SERP Features Present
- Featured Snippet: [yes/no, type]
- PAA questions: [list]
- Image Pack: [yes/no]
- Video: [yes/no]

### Search Intent Classification
- Primary intent: [informational/commercial/transactional/navigational]
- Confidence: [high/medium/low]
- Recommended format: [blog/landing]
```

## Step 2: Headings — Structure Extraction

For the top 3-5 ranking URLs, extract the full heading structure.

**With DataForSEO:** Use `mcp__dfs__on_page_content_parsing` to fetch and parse page content.

**Without DataForSEO (fallback):** Open each competitor URL directly (WebFetch or browser), then extract the heading structure (H1/H2/H3) from the HTML.

**Output:**
```markdown
## Step 2: Heading Structures

### Competitor 1: [URL]
- H1: [heading]
  - H2: [heading]
    - H3: [heading]
  - H2: [heading]
  ...

### Competitor 2: [URL]
...

### Common H2 Patterns
| H2 Topic | Comp 1 | Comp 2 | Comp 3 | Comp 4 | Comp 5 | Frequency |
|----------|:------:|:------:|:------:|:------:|:------:|:---------:|
```

## Step 3: Structure — Superior Outline

Combine the best patterns from Step 2 into a superior outline. The goal: cover everything competitors cover, PLUS add our unique angle.

**Rules:**
- Include every topic that appears in 3+ of the top 5 competitors (mandatory coverage)
- Include PAA questions as H2s where they fit naturally
- Add 1-2 sections that NO competitor covers (differentiation)
- For blog: 5-8 H2s. For landing: 3-5 sections
- Order by user journey logic, not competitor frequency

**Output:**
```markdown
## Step 3: Proposed Structure

### Blog Outline
| # | H2 | Source | Rationale |
|---|-----|--------|-----------|
| 1 | [heading] | 5/5 competitors | Must-include, foundational |
| 2 | [heading] | 4/5 competitors | Must-include |
| 3 | [heading] | PAA question | Snippet opportunity |
| 4 | [heading] | 2/5 competitors | Valuable but under-covered |
| 5 | [heading] | Original | Our unique angle — [PILLARS.md connection] |
| 6 | [heading] | PAA question | FAQ/snippet |
| 7 | [heading] | 3/5 competitors | Must-include |

### OR Landing Page Outline
| # | Section | Purpose | Word target |
|---|---------|---------|------------|
| 1 | Hero | Capture + convert | 30-50 |
| 2 | Value props | Why this product | 60-80 |
| 3 | Social proof | Trust | 40-60 |
| 4 | Product showcase | Browse | 20-40 |
| 5 | Education/FAQ | Overcome objections | 100-150 |
| 6 | Final CTA | Convert | 20-30 |
```

## Step 4: Content — Depth Analysis

For the top 3 competitors, analyze content quality:

| Dimension | What to measure |
|-----------|----------------|
| Depth | Do they explain concepts or just mention them? |
| Examples | Do they use real examples, case studies, data? |
| Visuals | Do they use images, charts, infographics? |
| Data | Do they cite statistics, research, studies? |
| Freshness | When was it last updated? |
| E-E-A-T | Author byline, credentials, sources cited? |

**Output:**
```markdown
## Step 4: Content Depth Analysis

| Dimension | Comp 1 | Comp 2 | Comp 3 | Our target |
|-----------|--------|--------|--------|------------|
| Depth | [shallow/medium/deep] | | | Deep (beat all) |
| Examples | [0/1-2/3+] | | | 3+ real examples |
| Data/stats | [yes/no] | | | Yes, cite 3+ sources |
| Visuals | [0/1-3/4+] | | | 1 per H2 section |
| Freshness | [date] | | | Current (2026) |
| E-E-A-T | [weak/medium/strong] | | | Strong |
```

## Step 5: Context — Semantic Map

Build the semantic context around the keyword.

**With DataForSEO:** Call `mcp__dfs__dataforseo_labs_google_related_keywords` and `mcp__dfs__dataforseo_labs_google_keyword_suggestions`.

**Without DataForSEO (fallback):** Use Google autocomplete suggestions, "People Also Ask" from Step 1, and "Related searches" at the bottom of SERP results. For volume/KD estimates, use any free keyword tool or skip — the semantic map is still valuable without exact numbers.

**Output:**
```markdown
## Step 5: Semantic Context

### Primary Keyword
| Field | Value |
|-------|-------|
| Keyword | [keyword] |
| Volume | [monthly] |
| KD | [difficulty] |
| CPC | [cost per click] |
| Intent | [type] |

### Secondary Keywords (include naturally in content)
| Keyword | Volume | KD | Where to use |
|---------|--------|-----|-------------|

### LSI / Related Terms
[List of semantically related terms to weave into the content]

### Questions (from PAA + keyword suggestions)
| Question | Volume | Snippet opportunity? |
|----------|--------|:-------------------:|

### Cannibalisation Check
Existing pages on this site targeting similar keywords:
| URL | Current keyword | Overlap risk |
|-----|----------------|:------------:|
```

## Step 6: Insights — Voice, Hook, CTA, E-E-A-T

Analyze HOW the top competitors write, not just WHAT they cover.

**Output:**
```markdown
## Step 6: Content Insights

### Tone & Voice
| Competitor | Tone | What works | What doesn't |
|-----------|------|------------|-------------|

### Our TOV (from workspace/TOV.md → Web / SEO)
- Blog: [tone shift from TOV.md]
- Landing: [tone shift from TOV.md]
- Words to use: [from TOV.md]
- Words to avoid: [from BRAND.md do-nots]

### Hook Patterns
Top 3 opening hooks from competitors:
1. [hook] — why it works
2. [hook] — why it works
3. [hook] — why it works

### CTA Patterns
| Competitor | CTA text | Placement | Style |
|-----------|----------|-----------|-------|

### E-E-A-T Signals to Include
- [ ] Author byline with credentials
- [ ] Publication date + last modified
- [ ] Expert quotes or citations
- [ ] Original data or research
- [ ] Real product/service experience (domain expertise)
- [ ] Links to authoritative sources

### Pillar Alignment
This article belongs to pillar: **[from PILLARS.md]**
Pillar weight for Web/SEO: [%]
Related articles in this pillar: [links to existing content]
```

---

## Final Output

Save everything to: `research/article-<slug>-research.md`

The file contains all 6 steps in sequence, ready for the writing phase to consume.

End with a summary:

```markdown
## Research Summary

| Field | Value |
|-------|-------|
| Keyword | [keyword] |
| Volume | [monthly] |
| Intent | [type] |
| Page type | blog / landing |
| Top competitor word count avg | [X] |
| Our target word count | [X + 20%] |
| H2 count | [N] |
| Snippet opportunity | [yes/no, type] |
| Pillar | [from PILLARS.md] |
| Cannibalisation risk | [none/low/medium/high] |

**Ready for writing phase.** Run `/article-write` to continue.
```
