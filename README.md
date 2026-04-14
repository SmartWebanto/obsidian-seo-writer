# Context-First SEO Writing with Obsidian + Claude Code

Write SEO articles that know your brand, audience, and strategy — not generic content from a blank page.

## The Technique

Most AI-generated content starts from zero every time. You paste a keyword, get a generic article, and spend hours fixing the tone, adding brand voice, and connecting it to your strategy.

This vault flips that. You build a **context layer** once — brand identity, audience personas, tone of voice, content pillars, keywords — and every article written through the pipeline inherits that context automatically.

```
┌──────────────────────────────────────────────────────────┐
│                                                          │
│  ┌────────────┐              ┌─────────────────────┐    │
│  │  WORKSPACE │─────────────▶│  ARTICLE PIPELINE   │    │
│  │  (context) │              │  (12 steps)         │    │
│  │            │              │                     │    │
│  │  BRAND     │              │  1-6:  Research     │    │
│  │  AUDIENCE  │              │  7-10: Write        │    │
│  │  TOV       │              │  11-12: Finalize    │    │
│  │  PILLARS   │              │                     │    │
│  │  KEYWORDS  │              └─────────────────────┘    │
│  │  ...       │                       │                 │
│  └────────────┘                       ▼                 │
│                              ┌─────────────────────┐    │
│                              │  OUTPUT              │    │
│                              │  research/           │    │
│                              │  content/            │    │
│                              │  briefs/             │    │
│                              └─────────────────────┘    │
│                                                          │
│  Obsidian links everything. Graph view shows connections.│
└──────────────────────────────────────────────────────────┘
```

## Vault Structure

```
.
├── workspace/                 Context layer (8 files)
│   ├── BRAND.md               Identity, domain, USP, design tokens
│   ├── AUDIENCE.md            Personas, pain points, segments
│   ├── TOV.md                 Voice spectrum, writing rules, page-type tone shifts
│   ├── PILLARS.md             Content pillars and topic distribution
│   ├── KEYWORDS.md            Keyword clusters mapped to pillars
│   ├── COMPETITORS.md         Competitive landscape and content gaps
│   ├── STRATEGY.md            Priorities, goals, decisions log
│   └── LEARNINGS.md           What worked, what failed (grows over time)
│
├── article-master/            12-step pipeline
│   ├── SKILL.md               Orchestrator
│   ├── article-research/      Steps 1-6: SERP analysis, structure, semantic map
│   ├── article-write/         Steps 7-10: Brief, draft, gap analysis, revision
│   ├── article-finalize/      Steps 11-12: Validation, schema, meta, linking
│   └── references/
│       ├── blog-guidelines.md
│       └── landing-page-guidelines.md
│
├── research/                  Output: research notes
├── content/                   Output: drafts and finals
├── briefs/                    Output: Obsidian brief notes
├── .obsidian/                 Minimal config (dataview plugin)
└── .claude/commands/
    └── onboard.md             Interactive setup wizard
```

## Multi-Client Setup

This vault is **one vault per client**. For multiple clients, clone the repo once per client:

```bash
git clone <this-repo> acme-seo
git clone <this-repo> beta-corp-seo
```

Each vault is fully independent — its own workspace, research, content, and Obsidian graph. No risk of cross-contamination between clients.

## Quick Start

### 1. Clone and open in Obsidian

```bash
git clone <this-repo> my-brand
cd my-brand
```

Open the folder as a vault in Obsidian. Install the [Dataview](https://github.com/blackfool/obsidian-dataview) community plugin when prompted.

### 2. Set up your workspace

#### With Claude Code (recommended)

```
/onboard
```

The wizard guides you through each file, asks focused questions, and writes your answers. Takes ~20 minutes for the full set, ~10 for the minimum.

#### Manually

Fill the workspace files in this order — each one builds on the previous:

| # | File | Time | What it captures | Minimum? |
|---|------|------|-----------------|:--------:|
| 1 | **BRAND.md** | ~5 min | Name, domain, USP, languages, voice attributes | Yes |
| 2 | **AUDIENCE.md** | ~5 min | Primary persona, pain points, buying triggers | Yes |
| 3 | **TOV.md** | ~5 min | Voice spectrum (5 dimensions), writing rules, key messages | Yes |
| 4 | PILLARS.md | ~5 min | 3-4 content themes with topics | |
| 5 | KEYWORDS.md | ~5 min | Keyword clusters mapped to pillars | |
| 6 | COMPETITORS.md | ~5 min | Top 3 competitors, strengths/weaknesses | |
| 7 | STRATEGY.md | ~3 min | Current phase, priorities, goals | |
| 8 | LEARNINGS.md | — | Grows over time as you publish | |

**The first 3 files (BRAND, AUDIENCE, TOV) are the minimum** needed to run the article pipeline. The rest improve quality but don't block you.

### 3. Write your first article

```
/article-master "your target keyword"
```

The pipeline runs in 3 phases with pauses between each:

```
Phase 1: RESEARCH (Steps 1-6)
  Analyze SERP, extract competitor headings, build outline,
  map semantic context, extract insights
  → research/article-<slug>-research.md
  → PAUSE for review

Phase 2: WRITE (Steps 7-10)
  Generate SEO brief, write draft, gap analysis vs competitors,
  integrate gaps into final draft
  → content/article-<slug>-draft.md
  → PAUSE for review

Phase 3: FINALIZE (Steps 11-12)
  Validate (title/meta/density/headings/brand alignment),
  add schema markup, internal linking plan, social meta, alt text
  → content/article-<slug>-final.md
  → briefs/article-<slug>.md (Obsidian note)
```

Flags:
- `--landing` — landing page instead of blog article
- `--auto` — skip pauses, run all 12 steps continuously

You can also run phases individually:
- `/article-research "keyword"` — only research
- `/article-write` — only writing (reads research from disk)
- `/article-finalize` — only finalization (reads draft from disk)

## The 12 Steps

| # | Step | What it does |
|---|------|-------------|
| 1 | **SERP** | Top 10 competitor analysis, SERP features, intent classification |
| 2 | **Headings** | H1/H2/H3 extraction from top 3-5 competitors |
| 3 | **Structure** | Superior outline: competitor patterns + unique angles |
| 4 | **Content** | Depth analysis: examples, data, visuals, E-E-A-T signals |
| 5 | **Context** | Semantic map: related keywords, LSI terms, cannibalization check |
| 6 | **Insights** | Voice patterns, hook analysis, CTA patterns from competitors |
| 7 | **Brief** | SEO metadata + section-by-section writing instructions |
| 8 | **Draft 1** | Full article draft (Gulpease 60-70 readability) |
| 9 | **Gap Analysis** | Draft vs competitor coverage: topics, keywords, structure |
| 10 | **Draft 2** | Integrate gaps, maintain readability |
| 11 | **Validate** | 30+ checks: title, meta, density, headings, brand alignment |
| 12 | **Finalize** | Schema markup, internal links, social meta, image alt text |

## Output Files

| File | Location | Purpose |
|------|----------|---------|
| Research | `research/article-<slug>-research.md` | SERP data, headings, outline, semantic map |
| Draft | `content/article-<slug>-draft.md` | Article draft with frontmatter |
| Final | `content/article-<slug>-final.md` | Production-ready article |
| Brief | `briefs/article-<slug>.md` | Obsidian note with wikilinks to workspace |

Each file is self-contained — no in-memory dependency between phases. You can run research today and write tomorrow.

## Requirements

| Tool                                                              |  Required?  | What for                                                                                     |
| ----------------------------------------------------------------- | :---------: | -------------------------------------------------------------------------------------------- |
| [Obsidian](https://obsidian.md)                                   |     Yes     | Vault navigation, graph view, wikilinks                                                      |
| [Claude Code](https://claude.ai/code)                             |     Yes     | Runs the pipeline and onboard wizard                                                         |
| [Dataview plugin](https://github.com/blackfool/obsidian-dataview) | Recommended | Queries across notes (future dashboards)                                                     |
| [DataForSEO](https://dataforseo.com)                              |  Optional   | Automates Step 1 (SERP data) and Step 5 (keyword data). Without it, do these steps manually. |

## How the Context Layer Works

Every workspace file is linked to the others via Obsidian wikilinks. When the article pipeline loads context in Phase 0, it reads:

- **BRAND.md** → domain, name, voice attributes, design tokens for landing pages
- **AUDIENCE.md** → who you're writing for, their pain points
- **TOV.md** → how to write (spectrum positions, rules, page-type adjustments)
- **PILLARS.md** → which pillar this article belongs to
- **KEYWORDS.md** → cannibalization check, cluster mapping
- **COMPETITORS.md** → competitive context
- **STRATEGY.md** → current priorities
- **LEARNINGS.md** → patterns to avoid

This context flows into every step. The brief references TOV for tone. The validation checks BRAND for banned words. The schema uses domain from BRAND. The outline connects to PILLARS.

## License

MIT
