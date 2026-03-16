# Input Folder

Drop any markdown file here. It will be mined for content insights on the next `/eden:run` cycle.

## Accepted content

- Ticker analyses or scanner output
- Meeting notes or research
- Article drafts or commentary
- Competitor analysis
- Market observations
- Academic research excerpts

## What happens

1. The insight-miner agent scans this folder at the start of every pipeline run
2. It extracts content-worthy insights, tags them with pillar and audience
3. Extracted insights go to `state/insights.md` with source tier 1 (highest priority)
4. Processed files are moved to `input/processed/` so they aren't re-scanned
