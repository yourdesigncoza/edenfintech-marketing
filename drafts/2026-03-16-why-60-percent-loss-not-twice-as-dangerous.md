---
brief_id: B006
insight_id: I005
pillar: 3 - Asymmetry Math
format: mechanism
hook_type: failure-mode
audience: investor
status: approved
self_check:
  hook_leads_with_failure_mode: true
  all_claims_cited: true
  no_banned_language: true
  no_unqualified_return_claims: true
  tone_peer_to_peer: true
  no_stock_recommendations: true
regulatory_flag: false
return_claim_flag: false
gate1_outcome: approved
gate1_notes: null
created: 2026-03-16
---

Most position sizing models treat a 60% potential loss as twice the risk of 30%. That is arithmetically wrong, and the error compounds inside every portfolio that uses linear downside modelling.

To recover from a 30% loss requires a 43% gain. To recover from a 60% loss requires a 150% gain. The relationship is not proportional -- each additional percentage point of downside demands exponentially more recovery than the previous one.

This is not an obscure quantitative insight. It is basic arithmetic that most sizing frameworks quietly ignore. When a portfolio model halves position size to account for double the downside, it underestimates the deep-drawdown scenario by a margin that becomes material at portfolio level.

The standard defence is "I already apply a margin of safety to my positions." But a margin of safety constrains how much you pay. It does not constrain how much you lose if you are wrong. Entry discipline and downside modelling are separate mechanics -- a conservative entry price does not correct a linear sizing assumption in the event of a deep drawdown.

EdenFinTech applies a non-linear downside penalty in its sizing math. Deep-downside scenarios compress position size dramatically rather than proportionally. And hard breakpoints enforce a floor: if projected CAGR falls below 30% or probability below 60%, position size drops to zero. Not reduced. Zero.

30% loss → 43% recovery needed.
60% loss → 150% recovery needed.

The math is not linear. Your sizing should not be either.

#DeepValue #ValueInvesting #RiskManagement #AsymmetricRisk

---

## Internal Notes (not for publishing)

- **Source references**:
  - Non-linear downside penalty: SKILL.md -- "The System Architecture": "Non-linear downside penalty: a 60% downside position is dramatically worse than 30%, not just twice as bad"
  - Recovery math (43% from 30% loss, 150% from 60% loss): I005 core idea; basic mathematical derivation (verifiable arithmetic)
  - Hard breakpoints (CAGR < 30% = 0% size, probability < 60% = 0% size): SKILL.md -- "The System Architecture": "Hard breakpoints"
  - Standard position sizing models treating downside linearly: I005 core idea
- **Brief alignment**: Hook names the failure mode (linear downside modelling) as specified in B006 hook concept. Covers all three talking points: non-linear recovery math with specific numbers, standard sizing models' linear error, and EdenFinTech's non-linear penalty with hard breakpoints. Preempts the "margin of safety" objection by distinguishing entry discipline from downside modelling. Ends with the concrete mechanism takeaway.
- **Strategy alignment**: Directive 1 (hook leads with failure mode -- linear downside modelling as widespread error). Directive 4 (Asymmetry Math at 1.3x). Strategy.md note: data-driven posts outperform by 52% in finance (ciela.ai, 2025) -- the specific recovery percentages serve as quantified data anchors. Directive 8 (approximately 1,400 characters, at the upper end of the 1,000-1,400 optimal range for mechanism posts). Directive 10 (4 hashtags at end, includes #DeepValue and #ValueInvesting plus pillar-specific niche tags). Hook type combines "named failure mode" (Highest) with "curiosity gap with quantified promise" (High) per strategy.md rankings.
