# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What This Is

EdenFinTech Marketing is an autonomous LinkedIn content pipeline orchestrated entirely by Claude Code. No external task management platform — all state lives in markdown files, agents are Claude Code subagents, and the pipeline runs via the `/eden:run` slash command. The user (John) is the board; all governance gates are interactive terminal decisions.

## How to Run

```
/eden:run
```

This runs the full 10-step pipeline: mine insights → create briefs → write drafts → approve (Gate 1) → queue check → publish → collect engagement → identify leads (Gate 3) → update strategy → reflect (self-improvement). Steps are skipped automatically when preconditions aren't met.

## Project Structure

```
SKILL.md                          # Company context — read before any content work
core_directives.md                # Immutable constitution — brand voice, boundaries, governance
pipeline/
  rules.md                        # DRY content rules (all agents reference this)
state/
  queue.md                        # Post lifecycle: pending_review → approved → published
  insights.md                     # Insight backlog (raw → briefed → used)
  briefs.md                       # Content briefs (ready → drafted → used)
  performance.md                  # Per-post engagement metrics + rolling aggregates
  strategy.md                     # Living strategy memo — the self-improvement feedback loop
  leads.md                        # Lead tracking
  reflection_log.md               # Append-only log of Reflection Agent analysis per cycle
  pending_improvements.md         # PLAN-mode proposals awaiting user approval at Gate 4
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
    content-writer.md             # Drafts LinkedIn posts with self-check + brief peer-scoring
    engagement-analyst.md         # Metrics, leads, strategy updates (merges 5 old roles)
    reflection-agent.md           # Self-improvement: peer scores, patterns, tiered autonomy
```

## 5 Agents

| Agent | Role | Model | Spawned When |
|-------|------|-------|--------------|
| `insight-miner` | Mine insights from docs, web, and input/ | sonnet | Insight backlog < 5 or new input files |
| `audience-strategist` | Convert insights to briefs; init LinkedIn research. Peer-scores insight quality. | sonnet | Raw insights exist |
| `content-writer` | Draft LinkedIn posts from briefs. Peer-scores brief quality. | opus | Ready briefs exist |
| `engagement-analyst` | Metrics, leads, strategy updates | sonnet | Published posts exist or strategy update due |
| `reflection-agent` | Self-improvement: chain scoring, pattern detection, tiered autonomy | sonnet | Every /eden:run cycle (Step 10) |

## Content Rules (DRY)

All content rules live in `pipeline/rules.md`. Agents reference it — never duplicate rules in agent definitions. For company context, read `SKILL.md`.

Key rules: hooks lead with failure modes, all claims cite specific sources, no banned language, return claims qualified, no stock recommendations, peer-to-peer analytical tone.

## Four Governance Gates

1. **Gate 1 (Post Approval)** — `/eden:run` step 4 presents drafts interactively
2. **Gate 2 (Reply Approval)** — engagement-analyst presents reply suggestions
3. **Gate 3 (Outreach Approval)** — `/eden:run` step 8 presents leads interactively
4. **Gate 4 (System Review)** — `/eden:run` step 10 presents auto-changes for audit + improvement proposals for approval

No agent may take autonomous external action without passing the relevant gate.

## Self-Improvement Loop

The pipeline has a multi-layered self-improvement system with three maturity phases:

**Layer 1 — Chain of Critique (Peer-Scoring):** Each agent evaluates upstream agent's output quality (not its own). Audience-strategist scores insights, content-writer scores briefs, reflection-agent scores the full chain. Scores stored in artifact frontmatter/metadata.

**Layer 2 — Reflection Agent (Step 10):** Runs every cycle. Reads all state + peer scores, detects patterns, executes bounded AUTO tweaks or generates PLAN proposals for Gate 4.

**Tiered Autonomy:**
- AUTO: bounded numerical adjustments (pillar weights, format multipliers, hook rankings) with hard clamps + file backups. Minimum 3 cycles of data.
- PLAN: agent prompts, rules, workflow, schemas → written to `state/pending_improvements.md` for Gate 4.

**Three Maturity Phases** (based on rows with actual engagement data in performance.md, not post count):
1. Phase 1 (0 rows with engagement data): Gate 1 approval/rejection as proxy signal
2. Phase 2 (1-5 rows with engagement data): Engagement predictions tracked, calibrating
3. Phase 3 (6+ rows with engagement data): Full outcome-driven feedback loop

**Convergence:** If 3 cycles produce no validated improvements AND fewer than 5 new drafts processed → steady state (monitor-only).

**Immutable Constitution:** `core_directives.md` — brand voice, boundaries, governance. Only the user can modify it. Reflection Agent validates all changes against it.

`state/strategy.md` is the living strategy document:
- Updated by engagement-analyst every 6 published posts (or on breakout/regression detection)
- Also receives bounded AUTO adjustments from the Reflection Agent
- Contains pillar weights, format rankings, hook type performance, audience split
- All content agents read it before operating

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
