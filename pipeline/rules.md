# Content Rules

Canonical content rules for all EdenFinTech LinkedIn operations. Every agent reads this before any content operation. Do not duplicate these rules in agent definitions.

For full company context, also read `SKILL.md` in the project root.

## Five Content Pillars

1. **Diagnostic** — temporary trouble vs value trap
2. **Adversarial Architecture** — self-deception as the real enemy
3. **Asymmetry Math** — downside first, always
4. **System Architecture** — AI doing real analytical work
5. **Case Studies** — the system running on real tickers

## Dual Audience

- **Investor** (RIAs, wealth managers, sophisticated investors): lead with self-deception failure mode and architectural fix
- **Developer** (quant devs, fintech collaborators): lead with technical architecture, adversarial pipeline, LLM hardening

## Hook Rules

- Every hook MUST lead with a failure mode or problem — never a feature
- Name the problem in the first line
- The reader should feel the pain before seeing the solution

## Post Formats

- **Framework**: a methodology element as a standalone principle
- **Case study**: real pipeline output (pass or failure walkthrough)
- **Mechanism**: one specific system behaviour in plain language
- **Reframe**: a conventional investing belief handled differently
- **Pre-mortem**: a kill-path narrative with anonymised or named ticker

## Post Structure

1. **Hook** — names the problem or failure mode
2. **Body** — explains mechanism or case with specific cited evidence
3. **Takeaway** — one concrete conclusion
4. **Optional CTA** — service link (investor) or technical reference (developer)

## Banned Language

Never use: "explosive upside", "massive gains", "you need to see this", "AI-powered" (as headline), any unqualified performance percentage.

## Required Language Register

Use: "asymmetric upside", "bounded downside", "architectural honesty enforcement", "deterministic override", "adversarial validation", "self-deception prevention".

## Citation Rules

- All data claims must cite a specific source: 10-K, earnings call, FMP data, SEC filing, scanner output, system documentation
- Never use "industry reports suggest" or vague attribution
- Source references must be specific enough to verify

## Return Claim Rules

- "Designed to target 30%+ annualised" = allowed
- "Returns 30%+" = NOT allowed
- All performance claims must be qualified with methodology context

## Regulatory Rules

- No stock-specific buy/sell recommendations in any public content
- Show rejections as often as passes
- Lead with failure modes, not features
- Tone: peer-to-peer analytical, never brand-to-retail

## Self-Check (Run Before Submitting Any Draft)

- [ ] Hook leads with failure mode (not feature)?
- [ ] Every data claim cited to a specific source?
- [ ] No banned language present?
- [ ] No unqualified return claims?
- [ ] Tone is peer-to-peer analytical (not brand-to-retail)?
- [ ] No stock-specific buy/sell recommendations?
- [ ] `regulatory_flag`: set true if any language could be interpreted as financial advice
- [ ] `return_claim_flag`: set true if any performance percentage appears
