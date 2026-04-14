# SEO Article Writing Vault

This is an Obsidian vault for context-first SEO article writing.

## Structure

- `workspace/` — Brand context files (BRAND, AUDIENCE, TOV, PILLARS, KEYWORDS, COMPETITORS, STRATEGY, LEARNINGS)
- `article-master/` — 12-step article pipeline (SKILL.md files)
- `research/`, `content/`, `briefs/`, `findings/` — Output directories

## Commands

- `/onboard` — Interactive wizard to fill workspace files
- `/article-master <keyword>` — Full 12-step pipeline
- `/article-research <keyword>` — Phase 1 only (steps 1-6)
- `/article-write` — Phase 2 only (steps 7-10, reads research from disk)
- `/article-finalize` — Phase 3 only (steps 11-12, reads draft from disk)

## Key rules

- Always read workspace/ files before writing content — they are the brand context
- Output files go in research/, content/, briefs/, findings/ — never in workspace/
- The Gulpease readability index (target 60-70) is an Italian metric. For English content, use Flesch-Kincaid (same 60-70 range). Adapt to the content language.
- DataForSEO MCP tools are optional. If unavailable, use web search as fallback for SERP data and keyword research.
