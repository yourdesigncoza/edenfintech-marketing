# EdenFinTech — Company Context (SKILL.md)

## What EdenFinTech Does

EdenFinTech is a deep value turnaround signal service. It identifies quality businesses
60%+ off their all-time high where the market has mispriced temporary distress as permanent
decline. Investments require: bounded downside, visible catalysts, and a 30%+ annualised
return hurdle. Otherwise: no position.

## The Core Insight

The value trap problem is not an information problem. Everyone has the same 10-Ks. It is a
self-deception problem. EdenFinTech's edge is architectural honesty enforcement.

## The System Architecture

The EdenFinTech scanner runs a multi-agent adversarial pipeline:
1. ATH Gate: only investigates stocks 60%+ off all-time high
2. 3-stage Analyst: fundamentals → qualitative → synthesis
3. Adversarial Validator: red-team + pre-mortem running in parallel
4. Blind Epistemic Reviewer: cannot see analyst scores or price targets (enforced in code)
5. Hardening Gates: probability anchoring detection, evidence laundering detection,
   deterministic contradiction detection, CAGR exception panel
6. Deterministic Pipeline: scoring → sizing → report (pure math, no LLM)

Key structural guardrails:
- If interest coverage < 1.0 AND equity < 0 AND FCF margin ≤ 0 → forced thesis break,
  math overrides LLM narrative regardless of story quality
- Probability banding: estimates forced to 50/60/70/80 only — no false precision
- Non-linear downside penalty: a 60% downside position is dramatically worse than 30%,
  not just twice as bad
- Hard breakpoints: CAGR < 30% = 0% size, probability < 60% = 0% size
- Regulatory/political risk: deterministic -2 confidence penalty, no override
- Legal/investigation risk: -2 confidence penalty, no override available

## The Investment Process (8 Steps)

1. Finding Ideas: beaten-down sectors, upcoming catalysts, businesses that can double in 2-3 years
2. First Filter: solvency, dilution, revenue growth, ROIC, valuation — fail any one, move on
3. Deep Analysis: comparative, not absolute — rank peers by balance sheet > margin > catalyst > optionality
4. Qualitative Deep Dive: moat, management, problem/fix map, incentive alignment, catalyst stack
5. Valuation: Revenue × FCF Margin × FCF Multiple / Shares = Price Target (bear/base/stretch)
6. Decision: weighted score — worst-case downside 45%, base-case probability 40%, CAGR 15%
7. Position Sizing: asymmetry math, confidence caps, hard breakpoints — ~12 positions max
8. After the Buy: monitor catalysts, management, margins, competition, macro cash flow events

## Pattern Recognition Setups

- Solvency scare, survival secured: market prices near-distress, balance sheet actually stabilised
- Quality franchise, temporary margin compression: durable demand + input cost or execution shock
- Strong business, narrative discount: fundamentals stable, macro/political narrative drives discount
- New operator, old asset: credible CEO with relevant track record, early milestones already met

## Anti-Patterns (Value Traps)

- Cheap with no catalyst timeline
- High upside claim with fragile financing
- Thesis depending on multiple expansion only
- Position sizing based on confidence language, not downside math

## Five Content Pillars

1. The diagnostic — temporary trouble vs value trap
2. The adversarial architecture — self-deception as the real enemy
3. The asymmetry math — downside first, always
4. System architecture — AI doing real analytical work
5. Case studies — the system running on real tickers

## Dual Audience

- Investor audience (RIAs, wealth managers, sophisticated investors):
  lead with self-deception failure mode and architectural fix
- Developer audience (quant devs, fintech collaborators):
  lead with technical architecture, adversarial pipeline, LLM hardening

## Mandatory Content Rules

BANNED language: "explosive upside", "massive gains", "you need to see this",
"AI-powered" (as headline), any unqualified performance percentage

REQUIRED language register: "asymmetric upside", "bounded downside",
"architectural honesty enforcement", "deterministic override",
"adversarial validation", "self-deception prevention"

- No stock-specific buy/sell recommendations in any public content
- All data claims must cite a specific source: 10-K, earnings call, FMP data,
  SEC filing, scanner output — never "industry reports suggest"
- Return claims must be qualified: "designed to target 30%+ annualised" is allowed,
  "returns 30%+" is not
- Lead with failure modes, not features — name the problem before the solution
- Show rejections as often as passes — methodology visible in public is the
  pre-launch track record substitute
- Tone: peer-to-peer analytical, never brand-to-retail

## Obsidian Vault (Output Archive)

Vault location: /home/laudes/zoot
Vault name: Paperclip_EdenFintech

Use Obsidian MCP to archive final outputs:
- Published posts → Paperclip_EdenFintech/Posts/Published/
- Lead profiles → Paperclip_EdenFintech/Leads/ (Active/Contacted/Converted/Archived)
- Weekly reports → Paperclip_EdenFintech/Reports/
- Raw insights → Paperclip_EdenFintech/Insights/
- Update _Index.md after every state change

Workflow state lives in Paperclip tickets. Obsidian is the permanent output archive.
