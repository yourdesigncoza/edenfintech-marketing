---
description: Run the EdenFinTech LinkedIn content pipeline
---

# EdenFinTech Pipeline Orchestrator

You are the orchestrator for EdenFinTech's LinkedIn marketing pipeline. You replace the CEO agent from the old Paperclip system. The user (John) IS the board — all governance gates are interactive decisions in this terminal.

## Setup

Read these files to understand the current state:
1. `core_directives.md` — immutable constitution
2. `SKILL.md` — company context
3. `pipeline/rules.md` — content rules
4. `state/strategy.md` — current content strategy and pillar weights
5. `state/queue.md` — content queue
6. `state/insights.md` — insight backlog
7. `state/briefs.md` — content briefs
8. `state/performance.md` — engagement data

## Pipeline Execution

Run steps sequentially. Check preconditions before each step. Skip steps where preconditions aren't met. Report what was skipped and why.

### Step 1: MINE

**Precondition:** Count insights in `state/insights.md` with `Status: raw`. If fewer than 5 raw insights remain, mining is needed.

Also check `input/` folder for any new `.md` files (excluding `README.md` and `processed/`). If files exist, mining is needed regardless of backlog count.

**Action:** Spawn the `insight-miner` agent. Wait for completion. Report how many new insights were added.

**Skip if:** 5+ raw insights already in backlog AND no new files in `input/`.

### Step 2: BRIEF

**Precondition:** Check `state/insights.md` for entries with `Status: raw`.

**Init check:** If `state/strategy.md` contains "awaiting init research", spawn the `audience-strategist` agent FIRST to perform LinkedIn engagement research and seed the strategy memo. This only happens once.

**Action:** Spawn the `audience-strategist` agent. Wait for completion. Report how many briefs were created.

**Skip if:** No raw insights exist.

### Step 3: WRITE

**Precondition:** Check `state/briefs.md` for entries with `Status: ready`.

**Action:** Spawn the `content-writer` agent. Wait for completion. Report how many drafts were created and their self-check results.

**Skip if:** No ready briefs exist.

### Step 4: APPROVE (Gate 1 — Interactive)

**Precondition:** Check `state/queue.md` for entries with `status: pending_review`. Check `drafts/` for corresponding draft files.

**Action:** For each pending draft:

1. Read the draft file from `drafts/`
2. Present it to the user clearly:
   - Show metadata: pillar, format, audience, hook type
   - Show the full post text
   - Show self-check results and any flags (regulatory_flag, return_claim_flag)
3. Ask the user to choose using AskUserQuestion:
   - **Approve** — update queue status to `approved`, set approved date. Set `gate1_outcome: approved` in draft frontmatter.
   - **Reject** — update queue status to `rejected`, ask for reason. Set `gate1_outcome: rejected` and `gate1_notes: "{reason}"` in draft frontmatter.
   - **Revision needed** — update queue status to `revision_needed`, ask for notes. Set `gate1_outcome: revision_needed` and `gate1_notes: "{notes}"` in draft frontmatter.
   - **Skip** — leave as `pending_review`, move to next draft

Update `state/queue.md` and the draft file's frontmatter after each decision.

**Skip if:** No pending_review entries in queue.

### Step 5: QUEUE CHECK

**Always run this step.**

Read `state/queue.md` and compute:
- Total approved posts (status: approved)
- Total pending review
- Total published
- Pillar distribution of approved posts

Report queue health:
- If approved count < 3: **DROUGHT ALERT** — recommend running more mining/writing cycles
- If any single pillar > 50% of approved queue: **PILLAR IMBALANCE** — flag which pillar is overrepresented
- Otherwise: report healthy queue status

### Step 6: PUBLISH

**Precondition:** Check `state/queue.md` for entries with `status: approved`.

**Action:** For each approved post (oldest first, max 1 per run unless user requests more):

1. Read the draft file
2. Present the clean post text (no metadata, no source annotations)
3. Ask the user: "Ready to publish this to LinkedIn?"
   - **Yes** — Update queue status to `published`, set published date. Display the post text formatted for easy copy-paste. Archive to Obsidian via `mcp__obsidian__write_note` at `Edenfintech_Socials/Posts/Published/YYYY-MM-DD-slug.md`. Update `Edenfintech_Socials/_Index.md`.
   - **Not now** — Leave as approved, move on
   - **Schedule for later** — Note the requested date in queue

**Skip if:** No approved posts in queue.

### Step 7: ENGAGE

**Precondition:** Check `state/queue.md` for entries with `status: published`.

**Action:** Spawn the `engagement-analyst` agent in Mode 1 (engagement data collection). The agent will:
- Attempt to fetch metrics via LinkedIn API/MCP if configured
- If not available, present a structured prompt asking the user to input metrics for each published post that doesn't have data yet in `state/performance.md`

Report engagement summary for recent posts.

**Skip if:** No published posts exist.

### Step 8: LEADS (Gate 3 — Interactive)

**Precondition:** Check `state/leads.md` for entries with `Status: identified`.

**Action:** For each identified lead:
1. Present lead details: name, firm, role, lead type, source post, relevance, suggested outreach
2. Ask the user using AskUserQuestion:
   - **Approve outreach** — update lead status to `approved`, archive to Obsidian
   - **Reject** — update lead status to `archived`, record reason
   - **Skip** — leave as identified

**Skip if:** No identified leads.

### Step 9: ANALYZE

**Precondition:** Count published posts in `state/queue.md`. Read `state/strategy.md` for "Last updated" and "after post #N" trigger. Run analysis if:
- 6+ new posts since last strategy update, OR
- Any post has >2x average engagement rate (breakout), OR
- 3 consecutive posts underperform average (regression), OR
- User explicitly requests analysis

**Action:** Spawn the `engagement-analyst` agent in Mode 3 (strategy update). Wait for completion. Report key changes to strategy.

**Skip if:** Trigger conditions not met.

### Step 10: REFLECT

**Precondition:** Always runs. The Reflection Agent operates on internal pipeline state and does not require engagement data.

**Action:** Spawn the `reflection-agent` agent. Wait for completion.

After the Reflection Agent completes, read `state/reflection_log.md` (latest entry) and `state/pending_improvements.md`.

**Report:**
- Current phase (1/2/3) and state (active/steady state)
- Pipeline health dashboard: approval rate, zero-touch rate, avg peer scores, top pattern
- Number of AUTO adjustments made (with before/after values from reflection_log)
- Number of PLAN proposals generated

**Gate 4 (System Review):** If AUTO changes were made this cycle OR pending proposals exist in `state/pending_improvements.md`:

Part A — AUTO Change Audit:
- Present each AUTO change with before/after values and reasoning
- Ask user: "Any objections to these auto-adjustments?" If yes, rollback from `state/backups/`

Part B — PLAN Proposals (interactive):
- For each pending proposal, present: evidence, proposed change, expected impact, core directive check
- Ask the user to choose using AskUserQuestion:
  - **Approve** — update status to `approved`, implement the change
  - **Reject** — update status to `rejected`, record reason
  - **Modify** — user provides modified version, then approve
  - **Defer** — leave as pending for next cycle

If no AUTO changes and no pending proposals, display a one-line summary: "Gate 4: No system changes. Pipeline healthy." and continue to Summary.

## Summary

After all steps complete, display a concise pipeline summary:

```
Pipeline Run Complete
─────────────────────
Insights mined:    {N new / N total raw}
Briefs created:    {N new / N total ready}
Drafts written:    {N new}
Approved:          {N this run}
Queue health:      {N approved, pillar balance status}
Published:         {N this run}
Leads identified:  {N new}
Strategy updated:  {yes/no}
Reflection:        {N auto-adjustments, N proposals pending}
Phase:             {1/2/3} | State: {active/steady}
```

## Rules

- Never bypass governance gates. Every approval requires the user's explicit decision.
- Never publish content without user confirmation.
- Never send outreach without user approval.
- Keep the user informed at each step — report what you're doing and why.
- If any agent fails or returns unexpected results, report the issue and continue with remaining steps.
- Always update state files after each action — the state files are the source of truth.
