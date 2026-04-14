# Landing Page Guidelines

Reference for creating and optimizing landing pages. Use alongside the article-master SKILL.

## Landing Page Anatomy

```
┌─────────────────────────────────────────┐
│  TITLE TAG (≤60 chars, keyword + brand) │
│  META DESCRIPTION (≤155, benefit + CTA) │
├─────────────────────────────────────────┤
│                                         │
│  ┌─────────────────────────────────┐    │
│  │         HERO SECTION            │    │
│  │                                 │    │
│  │  H1 — Benefit-driven headline   │    │
│  │  Subheadline (15-25 words)      │    │
│  │  PRIMARY CTA [button]           │    │
│  │  Trust signal (1 line)          │    │
│  │  Hero image (lifestyle/product) │    │
│  │                                 │    │
│  └─────────────────────────────────┘    │
│                                         │
│  VALUE PROPOSITION (3-4 blocks)         │
│  ┌─────┐  ┌─────┐  ┌─────┐            │
│  │Icon │  │Icon │  │Icon │            │
│  │Benf1│  │Benf2│  │Benf3│            │
│  └─────┘  └─────┘  └─────┘            │
│                                         │
│  SOCIAL PROOF                           │
│  Reviews / ratings / press / "As seen"  │
│                                         │
│  PRODUCT SHOWCASE                       │
│  Product grid or featured items         │
│                                         │
│  EDUCATION / OBJECTION HANDLING         │
│  FAQ accordion / objection handling     │
│                                         │
│  FINAL CTA                              │
│  Repeat hero CTA + urgency if applic.   │
│                                         │
├─────────────────────────────────────────┤
│  FOOTER (minimal — don't distract)      │
└─────────────────────────────────────────┘
```

## Landing Page vs Blog — Key Differences

| Aspect | Blog Article | Landing Page |
|--------|-------------|--------------|
| **Goal** | Educate, build authority, organic traffic | Convert visitors to buyers |
| **Intent** | Informational / commercial | Transactional / navigational |
| **Word count** | 1,000-2,500+ | 300-600 |
| **CTAs** | Soft (read more, explore) | Direct (shop, buy, get) |
| **Navigation** | Full site nav visible | Minimal or hidden nav |
| **Internal links** | Many (build link equity) | Few (reduce exit paths) |
| **Tone** | Educational, warm | Aspirational, concise, action-driven |
| **Images** | Illustrative, supporting | Hero-dominant, product-focused |
| **Schema** | BlogPosting + FAQ | Product / WebPage + Breadcrumb |

## Content Rules for Landing Pages

### Voice (from TOV.md → Web / SEO → Landing page)
<!-- Load voice settings from workspace/TOV.md at runtime -->
- Follow page-type adjustments from TOV.md → Web / SEO → Landing page
- Benefit-first, not feature-first
- CTA style from BRAND.md or TOV.md

### Headline Formula

**Pattern: [Benefit] + [Product/Category] + [Differentiator]**

<!-- Replace these with brand-specific examples from BRAND.md -->
Examples:
- "[Key benefit] — [emotional payoff]"
- "[Comparison advantage] over [alternative]"
- "[Product] [crafted/built/designed] by [differentiator]"

### Hero Section Checklist
- [ ] H1 visible without scrolling (mobile + desktop)
- [ ] CTA button visible without scrolling
- [ ] One trust signal near CTA (shipping, returns, material)
- [ ] Hero image: lifestyle shot, not product-on-white
- [ ] No more than 30 words above the fold (excluding nav)

### Value Proposition Blocks
Use 3 or 4 blocks. Each block:
- Icon or small image (48x48 or 64x64)
- Short title (3-5 words)
- One sentence of supporting text
- No CTA per block (the section CTA comes after)

<!-- Load value props from BRAND.md → USP and Core values -->

| Block | Title | Supporting |
|-------|-------|-----------|
| <!-- value 1 --> | <!-- short title --> | <!-- one sentence --> |
| <!-- value 2 --> | <!-- short title --> | <!-- one sentence --> |
| <!-- value 3 --> | <!-- short title --> | <!-- one sentence --> |

### Social Proof Options
In order of effectiveness:
1. **Customer reviews** with star ratings (highest trust)
2. **Press logos** ("As featured in...") 
3. **Testimonial quotes** with photo + name
4. **Numbers** ("10,000+ happy customers", "4.8/5 average rating")
5. **UGC** (customer photos from Instagram)

### SEO for Landing Pages

| Element | Requirement |
|---------|-------------|
| Title | ≤60 chars: "[Keyword] — [Brand]" or "[Benefit] \| [Brand]" |
| Meta | ≤155 chars, includes CTA verb + benefit |
| H1 | Single, benefit-driven, contains keyword naturally |
| H2 | 2-4 max (not 8 like blog — keep it focused) |
| Word count | 300-600 (every word must earn its place) |
| Internal links in | Get links FROM blog articles, category pages |
| Internal links out | Minimal (2-3 max — don't send traffic away) |
| Schema | Product or WebPage + BreadcrumbList |
| Canonical | Self-referencing |
| Hreflang | All language versions |

### Conversion Optimization

**CTA Placement:**
- Above the fold (hero) — PRIMARY
- After value props — SECONDARY (optional)
- Bottom of page — REPEAT PRIMARY
- Max 2 unique CTAs on the page (not 5 different messages)

**CTA Button Design (from BRAND.md → Design tokens → Buttons):**
- Background: [from BRAND.md → Buttons → Primary → Background]
- Text: [from BRAND.md → Buttons → Primary → Text]
- Border-radius: [from BRAND.md → Buttons → Primary → Radius]
- Padding: [from BRAND.md → Buttons → Primary → Padding]
- Font: match brand typography settings

**Reducing Friction:**
- Show price transparency (no hidden costs)
- Mention shipping policy near CTA
- Return policy visible
- Payment icons (Visa, Mastercard, PayPal)
- "Secure checkout" if applicable

### Mobile Landing Page Rules
- Hero CTA visible in first screen (no scrolling)
- Value props: stack vertically, not horizontally
- Product grid: 1 column on mobile
- Font: minimum 16px body, 28px+ headline
- Touch targets: minimum 44px height
- Sticky CTA bar at bottom (optional but effective)

### Multi-language Landing Pages

<!-- Adjust based on BRAND.md → Identity → Languages -->

| Language | URL pattern | Priority |
|----------|-------------|----------|
| <!-- primary language --> | /[slug]/ | Every landing page |
| <!-- language 2 --> | /[lang]/[slug]/ | <!-- priority --> |
| <!-- language 3 --> | /[lang]/[slug]/ | <!-- priority --> |

### Landing Page Types by Intent

| Type | When to use | Examples |
|------|------------|---------|
| **Category** | Browse a product group | /category/subcategory/ |
| **Product** | Single product detail | /product-name/ |
| **Campaign** | Time-limited promotion | /summer-sale/, /black-friday/ |
| **Collection** | Seasonal or curated set | /season-collection/, /gift-guide/ |
| **Topic** | Educational + conversion | /why-product/, /product-vs-alternative/ |

Each type has slightly different structure but all follow the hero → value → proof → CTA pattern.
