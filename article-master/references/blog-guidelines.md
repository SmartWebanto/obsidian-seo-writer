# Blog Article Guidelines

Reference for writing and optimizing blog articles. Use alongside the article-master SKILL.

## Blog Article Anatomy

```
┌─────────────────────────────────────────┐
│  TITLE TAG (≤60 chars, keyword front)   │
│  META DESCRIPTION (≤155 chars + CTA)    │
├─────────────────────────────────────────┤
│                                         │
│  H1 — Single, keyword-rich             │
│                                         │
│  INTRO (50-80 words)                    │
│  Hook → context → what you'll learn     │
│  → Include keyword in first 100 words   │
│                                         │
│  H2 — Topic section 1                   │
│  [200-300 words, 1 image, 1 link]       │
│                                         │
│  H2 — Topic section 2                   │
│  [200-300 words]                        │
│                                         │
│  H2 — PAA question (exact phrasing)     │
│  [40-60 word direct answer first]       │
│  [then expand with detail]              │
│                                         │
│  H2 — Unique angle / brand expertise    │
│  [connects to PILLARS.md]               │
│                                         │
│  H2 — FAQ (if PAA questions remain)     │
│  H3 Q: [question]                       │
│  A: [concise answer]                    │
│                                         │
│  CONCLUSION (50-80 words)               │
│  Summary → CTA → internal link          │
│                                         │
├─────────────────────────────────────────┤
│  AUTHOR BYLINE + DATE                   │
│  RELATED ARTICLES (3-5 links)           │
│  SCHEMA: Article/BlogPosting JSON-LD    │
└─────────────────────────────────────────┘
```

## Content Rules

### Voice (from TOV.md → Web / SEO → Blog post)
<!-- Load voice settings from workspace/TOV.md at runtime -->
- Follow page-type adjustments from TOV.md → Web / SEO → Blog post
- "We" for brand, "you" for reader
- Active voice preferred

### Structure Rules
- H2 count: 5-8 (not more)
- Paragraph length: 2-4 sentences max
- One idea per paragraph
- Use bullet lists for 3+ items
- Include at least 1 image per H2 section
- Alt text describes information, not the image

### SEO Minimums
| Element | Requirement |
|---------|-------------|
| Title | ≤60 chars, keyword in first half |
| Meta | ≤155 chars, includes CTA verb |
| H1 | Single, contains keyword naturally |
| Keyword density | 0.5-1.5% (natural, not forced) |
| Internal links out | ≥3 to relevant pages |
| Internal links in | Request from ≥2 existing pages |
| External links | 2-5 authoritative sources |
| Images | ≥3 with descriptive alt text |
| Word count | Top-10 avg + 20% |
| Reading level | Flesch-Kincaid 60-70 (adjust per audience) |

### Featured Snippet Targeting
- Use the PAA question verbatim as H2
- Answer in the first 40-60 words directly below the H2
- Format: paragraph snippet (most common for informational)
- For list snippets: use ordered/unordered list immediately after H2
- For table snippets: use HTML table

### Schema Markup
```json
{
  "@context": "https://schema.org",
  "@type": "BlogPosting",
  "headline": "[H1]",
  "author": {
    "@type": "Organization",
    "name": "[brand_name from BRAND.md]"
  },
  "publisher": {
    "@type": "Organization",
    "name": "[brand_name from BRAND.md]",
    "logo": { "@type": "ImageObject", "url": "[logo URL]" }
  },
  "datePublished": "[ISO date]",
  "dateModified": "[ISO date]",
  "image": "[hero image URL]",
  "description": "[meta description]"
}
```

Add `FAQPage` schema if the article contains Q&A/PAA sections.

### Multi-language Blog
<!-- Adjust URL patterns based on site structure and languages in BRAND.md -->

| Language | URL pattern | Notes |
|----------|-------------|-------|
| <!-- primary --> | /blog/[slug]/ | Primary |
| <!-- lang 2 --> | /[lang]/blog/[slug]/ | Translate, don't transliterate |

### Content Pillar Alignment
Every blog article must map to one of the pillars defined in PILLARS.md.
Load pillar definitions and channel weighting from `workspace/PILLARS.md → Web / SEO`.
