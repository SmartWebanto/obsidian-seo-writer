---
name: article-master
description: >
  12-step SEO article pipeline: research → write → finalize. Works for blog articles
  and landing pages. Brand-aware, SERP-driven, with human review pauses between phases.
  Use when creating new content or auditing existing pages.
  Trigger: /article-master <keyword> [--landing] [--auto]
metadata:
  version: "4.0"
---

# Article Master — Orchestrator

End-to-end SEO content pipeline in 12 steps, split into 3 phases with review pauses.

## Usage

```
/article-master "alpaca vs cashmere"              → blog (default), with pauses
/article-master "alpaca vs cashmere" --landing     → landing page, with pauses
/article-master "alpaca vs cashmere" --auto        → full pipeline, no pauses
/article-research "alpaca vs cashmere"             → only phase 1 (analysis)
/article-write                                     → only phase 2 (reads research from disk)
/article-finalize                                  → only phase 3 (reads draft from disk)
```

## The 12 Steps

```
ANALYSIS (Steps 1-6)                    CREATION (Steps 7-12)
─────────────────────                   ─────────────────────
1. SERP — top 10 competitors            7. Brief — SEO metadata + writing instructions
2. Headings — H1/H2/H3 extraction       8. Draft 1 — first draft (Gulpease 60-70)
3. Structure — best-of outline           9. Gap Analysis — vs competitor coverage
4. Content — depth, examples, data      10. Draft 2 — integrate gaps
5. Context — LSI, semantic map          11. Validate — title/meta/density/headings
6. Insights — TOV, hook, CTA, E-E-A-T  12. Finalize — schema, links, meta social, alt
```

## Orchestration Flow

```
/article-master "keyword"
  │
  ▼
Phase 0: CONTEXT LOADING
  Read workspace/BRAND.md (domain, name, languages, voice, design tokens),
  AUDIENCE.md, TOV.md, PILLARS.md, KEYWORDS.md, LEARNINGS.md, STRATEGY.md
  Determine page type: blog or landing (from --landing flag or intent)
  Generate slug from keyword
  │
  ▼
Phase 1: RESEARCH (Steps 1-6)
  Execute article-research/SKILL.md
  Output → research/article-<slug>-research.md
  │
  ├── [--auto mode] → continue immediately
  └── [default] → PAUSE
      Show research summary to user
      "Research complete. Review research/article-<slug>-research.md"
      "Continue with /article-write or adjust the research first."
  │
  ▼
Phase 2: WRITE (Steps 7-10)
  Execute article-write/SKILL.md
  Reads research from disk
  Output → content/article-<slug>-draft.md
  │
  ├── [--auto mode] → continue immediately
  └── [default] → PAUSE
      Show draft summary to user
      "Draft complete. Review content/article-<slug>-draft.md"
      "Continue with /article-finalize or revise the draft first."
  │
  ▼
Phase 3: FINALIZE (Steps 11-12)
  Execute article-finalize/SKILL.md
  Reads draft from disk
  Output → content/article-<slug>-final.md
           findings/article-<slug>-YYYY-MM-DD.json
           briefs/article-<slug>.md (Obsidian note with frontmatter)
  │
  ▼
DONE
  Show final summary with quality score
```

## Page Type Detection

If no `--landing` flag, auto-detect from search intent:

| Intent | Signals | Default type |
|--------|---------|-------------|
| Informational | "how to", "what is", "guide" | Blog |
| Commercial | "best X", "X vs Y", "review" | Blog |
| Transactional | "buy", "price", "shop" | Landing |
| Navigational | brand name, product name | Landing |

If intent contradicts the flag, warn but proceed with the user's choice.

## File Conventions

All intermediate files use the slug derived from the keyword:

| Phase | Output path | Contains |
|-------|-------------|----------|
| Research | `research/article-<slug>-research.md` | SERP data, headings, structure, semantic map, insights |
| Draft | `content/article-<slug>-draft.md` | Full article draft with metadata |
| Final | `content/article-<slug>-final.md` | Production-ready article |
| Findings | `findings/article-<slug>-YYYY-MM-DD.json` | Validation results as findings |
| Brief | `briefs/article-<slug>.md` | Obsidian note with frontmatter |

Each file is self-contained — no in-memory dependency between phases. You can run research today and write tomorrow.

## References

Read the appropriate reference file based on page type:
- Blog → `references/blog-guidelines.md`
- Landing → `references/landing-page-guidelines.md`

## Sub-Skills

| Skill | Steps | Location |
|-------|-------|----------|
| article-research | 1-6 | `article-research/SKILL.md` |
| article-write | 7-10 | `article-write/SKILL.md` |
| article-finalize | 11-12 | `article-finalize/SKILL.md` |
