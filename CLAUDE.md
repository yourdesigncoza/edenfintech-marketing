# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What This Is

EdenFinTech Marketing is an autonomous LinkedIn content pipeline orchestrated entirely by Claude Code. No external task management platform — all state lives in markdown files, agents are Claude Code subagents, and the pipeline runs via the `/eden:run` slash command. The user (John) is the board; all governance gates are interactive terminal decisions.

## How to Run

```
/eden:run
```

This runs the full 9-step pipeline: mine insights → create briefs → write drafts → approve (Gate 1) → queue check → publish → collect engagement → identify leads (Gate 3) → update strategy. Steps are skipped automatically when preconditions aren't met.

## Project Structure

```
SKILL.md                          # Company context — read before any content work
pipeline/
  rules.md                        # DRY content rules (all agents reference this)
state/
  queue.md                        # Post lifecycle: pending_review → approved → published
  insights.md                     # Insight backlog (raw → briefed → used)
  briefs.md                       # Content briefs (ready → drafted → used)
  performance.md                  # Per-post engagement metrics + rolling aggregates
  strategy.md                     # Living strategy memo — the self-improvement feedback loop
  leads.md                        # Lead tracking
drafts/
  {YYYY-MM-DD-slug}.md            # One file per post draft with frontmatter metadata
input/
  *.md                            # Drop raw material here — mined on next /eden:run
  processed/                      # Processed input files moved here
.claude/
  commands/eden/run.md            # The orchestrator skill
  agents/
    insight-miner.md              # Surfaces insights from SKILL.md, web research, input/
    audience-strategist.md        # Converts insights to briefs; seeds strategy on init
    content-writer.md             # Drafts LinkedIn posts with self-check
    engagement-analyst.md         # Metrics, leads, strategy updates (merges 5 old roles)
```

## 4 Agents

| Agent | Role | Model | Spawned When |
|-------|------|-------|--------------|
| `insight-miner` | Mine insights from docs, web, and input/ | sonnet | Insight backlog < 5 or new input files |
| `audience-strategist` | Convert insights to briefs; init LinkedIn research | sonnet | Raw insights exist |
| `content-writer` | Draft LinkedIn posts from briefs | opus | Ready briefs exist |
| `engagement-analyst` | Metrics, leads, strategy updates | sonnet | Published posts exist or strategy update due |

## Content Rules (DRY)

All content rules live in `pipeline/rules.md`. Agents reference it — never duplicate rules in agent definitions. For company context, read `SKILL.md`.

Key rules: hooks lead with failure modes, all claims cite specific sources, no banned language, return claims qualified, no stock recommendations, peer-to-peer analytical tone.

## Three Governance Gates

1. **Gate 1 (Post Approval)** — `/eden:run` step 4 presents drafts interactively
2. **Gate 2 (Reply Approval)** — engagement-analyst presents reply suggestions
3. **Gate 3 (Outreach Approval)** — `/eden:run` step 8 presents leads interactively

No agent may take autonomous external action without passing the relevant gate.

## Self-Improvement Loop

`state/strategy.md` is a living document that evolves based on engagement data:
- Updated every 6 published posts (or on breakout/regression detection)
- Contains pillar weights, format rankings, hook type performance, audience split
- All content agents read it before operating — influences pillar priority, hook selection, format choice
- On first run, audience-strategist performs deep LinkedIn engagement research to seed it

## Obsidian Archive (Write-Only)

Vault: `Edenfintech_Socials` at `/home/laudes/zoot`. Write final outputs only — never read from Obsidian.
- Published posts → `Posts/Published/`
- Strategy reports → `Reports/`
- Leads → `Leads/{Active,Contacted,Converted,Archived}/`
- Insights → `Insights/`
- Update `_Index.md` after every write.

## LinkedIn Integration

- **Official API** (`r_member_postAnalytics`): impressions, reactions, comments count, reshares, members reached
- **stickerdaniel/linkedin-mcp-server** (Patchright): comment text, commenter profiles for lead discovery
- **Publishing**: manual — user copies post text to LinkedIn

## When Editing

- `pipeline/rules.md` is the single source of truth for content rules — edit there, not in agent files
- `state/strategy.md` is auto-generated — edit only to override or seed
- Agent definitions in `.claude/agents/` define persona and process — keep focused and concise
- The orchestrator `.claude/commands/eden/run.md` controls pipeline flow — changes affect all steps
- `agents_paperclip_archive/` contains the old Paperclip-based agent definitions for reference
