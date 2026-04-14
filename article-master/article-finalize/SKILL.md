---
name: article-finalize
description: >
  Steps 11-12 of the article pipeline: validation checklist and finalization
  (schema markup, internal linking, meta social, alt text). Reads draft from disk,
  produces the final publication-ready article + findings JSON.
metadata:
  version: "4.0"
  phase: 3-of-3
  steps: "11-12"
---

# Article Finalize — Steps 11-12

Validate the draft against SEO best practices and produce the final, publication-ready article.

## Input

Read the draft: `content/article-<slug>-draft.md`
Read the research: `research/article-<slug>-research.md` (for keyword data)
Read workspace: BRAND.md, TOV.md
Read appropriate reference: `references/blog-guidelines.md` or `references/landing-page-guidelines.md`

---

## Step 11: Validation — Comprehensive Checklist

Run every check. For each failure, create a finding with severity and action.

### 11a. Title Tag

| Check | Rule | Severity if fail |
|-------|------|:----------------:|
| Contains primary keyword | Keyword in first half of title | warning |
| Length ≤ 60 characters | Count characters (not pixels) | warning |
| Unique | Not duplicate of existing page title | critical |
| Brand suffix | "| [brand_name]" at end (optional for blog, required for landing) | info |
| Compelling | Would you click this in SERP? | info |

### 11b. Meta Description

| Check | Rule | Severity if fail |
|-------|------|:----------------:|
| Exists and non-empty | Must be present | warning |
| Length ≤ 155 characters | Truncation risk above 155 | warning |
| Contains keyword | Natural inclusion, not stuffed | info |
| Contains CTA verb | "Discover", "Learn", "Shop", "Explore" | info |
| Unique | Not duplicate of another page | warning |

### 11c. Heading Structure

| Check | Rule | Severity if fail |
|-------|------|:----------------:|
| Single H1 | Exactly one H1, contains keyword | critical |
| H2 count | Blog: 5-8 / Landing: 3-5 | info |
| No skipped levels | H1→H2→H3, never H1→H3 | warning |
| Keyword in ≥1 H2 | Natural inclusion | warning |
| PAA question as H2 | If snippet opportunity exists | info |

### 11d. Keyword Density

| Check | Rule | Severity if fail |
|-------|------|:----------------:|
| Primary keyword density | 0.5-1.5% | warning (if <0.3% or >2%) |
| Keyword in first 100 words | Present naturally | warning |
| Keyword in conclusion | Present naturally | info |
| Secondary keywords | ≥5 unique secondary terms used | info |
| No keyword stuffing | No unnatural repetition | critical |

Calculate density: `(keyword occurrences × keyword word count) / total word count × 100`

### 11e. Content Quality

| Check | Rule | Severity if fail |
|-------|------|:----------------:|
| Word count meets target | Within ±10% of brief target | warning |
| Readability: Gulpease 60-70 | Calculate or estimate | warning |
| Max sentence length | No sentence > 25 words | info |
| Max paragraph length | No paragraph > 4 sentences | info |
| Active voice | >80% active constructions | info |
| No duplicated content | No paragraphs copy-pasted from competitors | critical |

### 11f. Internal Links

| Check | Rule | Severity if fail |
|-------|------|:----------------:|
| Outgoing links ≥ 3 | To relevant existing pages | warning |
| Links use descriptive anchors | Not "click here" or naked URLs | warning |
| Link targets exist | All URLs resolve (no 404) | warning |
| Incoming links planned | ≥2 existing pages should link TO this article | info |

### 11g. Brand Alignment

| Check | Rule | Severity if fail |
|-------|------|:----------------:|
| Voice matches TOV.md | Blog tone or Landing tone as appropriate | warning |
| No banned words | Check against BRAND.md "Do NOT" list | warning |
| Audience appropriate | Content matches AUDIENCE.md segment | info |
| Pillar aligned | Maps to a PILLARS.md pillar | info |
| Anti-learnings respected | No patterns from LEARNINGS.md anti-learnings | warning |

### 11h. Landing Page Specific (skip for blog)

| Check | Rule | Severity if fail |
|-------|------|:----------------:|
| CTA above the fold | Primary CTA visible without scrolling | critical |
| CTA repeated | At least 2 CTA placements | warning |
| Trust signals present | Reviews, badges, guarantees | warning |
| Mobile CTA visible | Button visible in first mobile screen | warning |
| Max 2 unique CTAs | No decision fatigue | info |

### Validation Output

```markdown
## Step 11: Validation Results

### Score
Pass: [N] / Total: [N] = [X]%

### Failures

| # | Check | Severity | Issue | Fix |
|---|-------|----------|-------|-----|
| 1 | [check name] | warning | [what's wrong] | [how to fix] |
| 2 | ... | | | |

### Auto-Fixed
Items that were fixed automatically during validation:
- [fix 1]
- [fix 2]
```

**Auto-fix where possible:** If title is 62 chars, shorten it. If keyword density is 0.3%, add one natural occurrence. If a heading skips a level, restructure it. Mark auto-fixes in the output.

---

## Step 12: Finalize — Schema, Links, Meta Social, Alt Text

Apply all final production elements to the article.

### 12a. Schema Markup

**Blog article:**
```json
{
  "@context": "https://schema.org",
  "@type": "BlogPosting",
  "headline": "[H1]",
  "description": "[meta description]",
  "author": {
    "@type": "Organization",
    "name": "[brand_name from BRAND.md]",
    "url": "[domain from BRAND.md]"
  },
  "publisher": {
    "@type": "Organization",
    "name": "[brand_name from BRAND.md]",
    "logo": {
      "@type": "ImageObject",
      "url": "[logo URL from BRAND.md]"
    }
  },
  "datePublished": "[ISO date]",
  "dateModified": "[ISO date]",
  "image": "[hero image URL]",
  "mainEntityOfPage": "[article URL]"
}
```

If FAQPage content exists, add:
```json
{
  "@context": "https://schema.org",
  "@type": "FAQPage",
  "mainEntity": [
    {
      "@type": "Question",
      "name": "[PAA question]",
      "acceptedAnswer": {
        "@type": "Answer",
        "text": "[answer text]"
      }
    }
  ]
}
```

**Landing page:**
- WebPage schema + BreadcrumbList
- Product schema if product-focused (price, availability, reviews)

### 12b. Internal Linking Plan

```markdown
### Outgoing Links (from this article)
| Anchor text | Target URL | Context |
|-------------|-----------|---------|
| [descriptive anchor] | [URL] | [which section] |

### Incoming Links (add to existing pages)
| Source page | Anchor text | Where to add |
|-------------|-------------|-------------|
| [existing URL] | [anchor] | [section of source page] |
```

### 12c. Social Meta Tags

```html
<!-- Open Graph -->
<meta property="og:title" content="[title — can differ from SEO title]">
<meta property="og:description" content="[compelling description for social]">
<meta property="og:image" content="[1200x630 image URL]">
<meta property="og:type" content="article">
<meta property="og:url" content="[canonical URL]">
<meta property="og:site_name" content="[brand_name]">

<!-- Twitter -->
<meta name="twitter:card" content="summary_large_image">
<meta name="twitter:title" content="[title]">
<meta name="twitter:description" content="[description]">
<meta name="twitter:image" content="[same image]">
```

### 12d. Image Alt Text

For every image in the article:

| Image | Alt text | Notes |
|-------|----------|-------|
| Hero | [descriptive: what the image shows, not "hero image"] | Include keyword if natural |
| Section 1 | [describes information, not the image] | |
| Section 2 | [describes information] | |

Rules:
- Describe the information, not the image
- Include keyword in 1 image alt (naturally)
- Use `alt=""` for decorative images only
- Max 125 characters

### 12e. Multi-language Checklist

If the article should be translated (check BRAND.md → Identity → Languages):

| Language | URL | Status | Priority |
|----------|-----|--------|----------|
| <!-- primary language --> | /blog/[slug]/ | This article | Primary |
| <!-- language 2 --> | /[lang]/blog/[slug]/ | To translate | <!-- priority --> |
| <!-- language 3 --> | /[lang]/blog/[slug]/ | To translate | <!-- priority --> |

Add hreflang tags for all language versions.

---

## Final Output

### 1. Final article
Save to: `content/article-<slug>-final.md`

Update frontmatter:
```yaml
---
type: article-final
format: blog | landing
keyword: [primary keyword]
volume: [monthly]
word_count: [final count]
gulpease: [estimated score]
validation_score: [N/N passed]
pillar: [from PILLARS.md]
date: YYYY-MM-DD
status: final
---
```

### 2. Findings JSON
Save validation findings to: `findings/article-<slug>-YYYY-MM-DD.json`

Schema: same as SEO audit findings (id, severity, category, title, evidence, action, effort).
IDs: `article-001`, `article-002`, etc.

### 3. Obsidian brief note
Save to: `briefs/article-<slug>.md` with frontmatter for Dashboard Dataview:

```yaml
---
type: brief
format: blog | landing
keyword: [keyword]
volume: [volume]
intent: [intent type]
pillar: [pillar name]
status: published
date: YYYY-MM-DD
validation_score: [X%]
---
```

Include wikilinks: `[[BRAND]]`, `[[AUDIENCE]]`, `[[TOV]]`, `[[PILLARS]]`.

### 4. Summary

```markdown
## Article Complete

| Field | Value |
|-------|-------|
| Keyword | [keyword] |
| Format | blog / landing |
| Word count | [final] |
| Validation | [N/N] passed ([X%]) |
| Failures fixed | [N] auto-fixed, [N] flagged |
| Schema | [types added] |
| Internal links | [N] outgoing, [N] incoming planned |
| Languages | [N] translations needed |

### Files Created
- `content/article-<slug>-final.md` — publication-ready article
- `findings/article-<slug>-YYYY-MM-DD.json` — validation findings
- `briefs/article-<slug>.md` — Obsidian brief note

### Next Steps
1. Upload to WordPress
2. Add images (hero + per-section)
3. Add internal links from existing pages (see linking plan)
4. Submit to GSC for indexing
5. Share via email newsletter (see distribution angle in research)
6. Share on social (see distribution angle in research)
```
