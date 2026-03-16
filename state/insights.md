# Insight Backlog

<!-- Status: raw | briefed | used -->
<!-- Source tier: 1 (user-provided/pipeline) | 2 (methodology docs) | 3 (market context/research) -->

### I001 - The Value Trap Is a Self-Deception Problem, Not an Information Problem
- **Status**: briefed
- **Pillar**: 2 (Adversarial Architecture)
- **Source tier**: 2
- **Source ref**: SKILL.md — "The Core Insight" section: "The value trap problem is not an information problem. Everyone has the same 10-Ks. It is a self-deception problem. EdenFinTech's edge is architectural honesty enforcement."
- **Audience**: investor
- **Core idea**: Every institutional investor has access to the same 10-K filings, earnings calls, and analyst reports. The reason investors walk into value traps is not information asymmetry — it is the cognitive architecture of the analyst themselves. The insight here is that the solution cannot be more research; it must be structural enforcement against the researcher's own motivated reasoning.

---

### I002 - The 40-45% Value Trap Rate: Why Cheap Stocks Destroy More Portfolios Than Expensive Ones
- **Status**: briefed
- **Pillar**: 1 (Diagnostic)
- **Source tier**: 3
- **Source ref**: Perplexity deep research on value traps (2026-03-16 run): "Recent academic research has revealed that approximately 40-45% of the cheapest stocks in the market merit classification as value traps, and that these problematic securities disproportionately erode portfolio returns through both capital losses and elevated volatility."
- **Audience**: investor
- **Core idea**: Roughly four to five out of every ten stocks screened as statistically cheap are traps — permanently impaired businesses dressed up by low price multiples. This base rate makes naïve deep value strategies net destructive: the losers are not just slightly worse than the winners, they disproportionately erode returns through capital destruction and elevated volatility. The diagnostic challenge is separating the surviving 55-60% from the impaired 40-45% before entering, not after.

---

### I003 - The ATH Gate: Why 60% Below Peak Is the Starting Line, Not the Buy Signal
- **Status**: briefed
- **Pillar**: 1 (Diagnostic)
- **Source tier**: 2
- **Source ref**: SKILL.md — "The System Architecture" section, Step 1: "ATH Gate: only investigates stocks 60%+ off all-time high"; also "Investment Process" Step 1: "beaten-down sectors, upcoming catalysts, businesses that can double in 2-3 years"
- **Audience**: investor
- **Core idea**: The 60%-off-ATH filter is not a valuation signal — it is an eligibility gate that defines the universe worth investigating. A stock down 60% from its high has already repriced the market's worst-case narrative; what the system then asks is whether that narrative is accurate or exaggerated. This reframes the entry criterion as a signal-to-noise filter, not a buy trigger, which is the critical distinction between disciplined deep value and value trap hunting.

---

### I004 - The Blind Epistemic Reviewer: Enforcing Honesty Through Architectural Separation
- **Status**: briefed
- **Pillar**: 4 (System Architecture)
- **Source tier**: 2
- **Source ref**: SKILL.md — "The System Architecture" section, Step 4: "Blind Epistemic Reviewer: cannot see analyst scores or price targets (enforced in code)"
- **Audience**: developer
- **Core idea**: When a reviewer has access to the analyst's score and price target, anchoring bias makes independent review structurally impossible — the reviewer calibrates toward the existing number rather than forming an independent view. EdenFinTech solves this by enforcing the information blackout in code, not policy: the Blind Epistemic Reviewer literally cannot retrieve prior scores. This is a software architecture decision with direct behavioral consequences, and it is the developer-audience angle: honesty enforced through access control, not professional norms.

---

### I005 - Non-Linear Downside Penalty: Why 60% Loss Is Not Twice as Bad as 30%
- **Status**: briefed
- **Pillar**: 3 (Asymmetry Math)
- **Source tier**: 2
- **Source ref**: SKILL.md — "The System Architecture" section: "Non-linear downside penalty: a 60% downside position is dramatically worse than 30%, not just twice as bad"
- **Audience**: investor
- **Core idea**: Standard position sizing models treat downside linearly — a 60% potential loss is treated as twice as risky as 30%. This is mathematically wrong. To recover from a 60% loss requires a 150% gain; to recover from 30% requires only 43%. The EdenFinTech system applies a non-linear downside penalty in its sizing math, so that deep-downside scenarios compress position size dramatically rather than proportionally. Framing this as a correction to a widespread modelling error gives it strong diagnostic resonance for sophisticated investors.

---

### I006 - Hard Breakpoints: When Math Overrides the Story
- **Status**: briefed
- **Pillar**: 3 (Asymmetry Math)
- **Source tier**: 2
- **Source ref**: SKILL.md — "The System Architecture" section: "Hard breakpoints: CAGR < 30% = 0% size, probability < 60% = 0% size"; also "If interest coverage < 1.0 AND equity < 0 AND FCF margin ≤ 0 → forced thesis break, math overrides LLM narrative regardless of story quality"
- **Audience**: both
- **Core idea**: The most dangerous moment in deep value analysis is when a compelling narrative meets a structurally broken balance sheet. EdenFinTech uses hard deterministic breakpoints that override LLM-generated analysis entirely: if interest coverage falls below 1.0, equity is negative, and FCF margin is zero or negative simultaneously, the thesis breaks — regardless of how coherent the recovery story sounds. For investors, this is about removing the human override moment; for developers, it is about the architecture of deterministic gates above probabilistic outputs.

---

### I007 - LLM Herding in Multi-Agent Finance Pipelines: The Overconfident Consensus Failure Mode
- **Status**: briefed
- **Pillar**: 4 (System Architecture)
- **Source tier**: 3
- **Source ref**: Gemini search on adversarial multi-agent LLM pipelines (2026-03-16): "In multi-agent pipelines, this manifests as 'majority herding' or 'overconfident consensus'. When a Planner Agent passes an overconfident, erroneous market trend analysis to an Executor/Critic Agent, the downstream agent often treats the input as settled factual ground rather than a probabilistic hypothesis." — citing openreview.net and preprints.org research
- **Audience**: developer
- **Core idea**: Multi-agent LLM pipelines in finance are not more reliable than single agents — they can be less reliable, because downstream agents treat upstream outputs as settled fact rather than probabilistic estimates. The result is cascading overconfidence: each stage amplifies the prior stage's certainty rather than questioning it. This is precisely the failure mode that EdenFinTech's Adversarial Validator and Blind Epistemic Reviewer are designed to interrupt structurally, not through prompt instructions.

---

### I008 - Biotech's 83% Drawdown: What a Real 60%-Gate Universe Looks Like in 2026
- **Status**: briefed
- **Pillar**: 5 (Case Studies)
- **Source tier**: 3
- **Source ref**: Perplexity research on beaten-down sectors (2026-03-16): "ARK Genomic Revolution ETF (ARKG) has experienced a maximum drawdown of -83.17%, with the current drawdown registering at approximately -70.40%... The maximum drawdown period has extended for 61 months and remains in progress." Source: lazyportfolioetf.com data as of February 2026.
- **Audience**: investor
- **Core idea**: The ARKG ETF — down 83% from its peak over 61 months — is a live example of what the EdenFinTech ATH gate is designed to catch before entry, not after. The ETF's 4.31% annualised return since inception despite operating through an era of genomics innovation illustrates the destructive asymmetry of a sustained value trap: years of capital tied up in negative compounding. The diagnostic question the system would ask is whether this is temporary margin compression or structural impairment — and the FCF burn rates and absence of a visible catalyst timeline would likely trigger a hard break before any position sizing even begins.

---

### I009 - Narrative Discount vs. Fundamental Impairment: The Four Pattern Recognition Setups
- **Status**: briefed
- **Pillar**: 1 (Diagnostic)
- **Source tier**: 2
- **Source ref**: SKILL.md — "Pattern Recognition Setups" section: four named setups — "Solvency scare, survival secured"; "Quality franchise, temporary margin compression"; "Strong business, narrative discount"; "New operator, old asset"
- **Audience**: investor
- **Core idea**: Not all beaten-down stocks are impaired for the same reason, and the recovery path depends entirely on why the business fell. EdenFinTech's framework names four distinct setups — solvency scare with stabilised balance sheet, quality franchise hit by input cost shock, fundamentally sound business punished by macro narrative, and credible new operator on an old asset. Each maps to a different catalyst stack and a different level of confidence in the recovery timeline. The content angle is teaching investors to name the setup before building any thesis, because the right diagnosis determines everything downstream.

---

### I010 - The Pre-Mortem as a Kill-Path Discipline: Assuming Failure Before It Happens
- **Status**: briefed
- **Pillar**: 2 (Adversarial Architecture)
- **Source tier**: 2
- **Source ref**: SKILL.md — "The System Architecture" section, Step 3: "Adversarial Validator: red-team + pre-mortem running in parallel"; pipeline/rules.md — "Post Formats" section: "Pre-mortem: a kill-path narrative with anonymised or named ticker"
- **Audience**: both
- **Core idea**: Most investment processes ask "why will this work?" The pre-mortem asks "assume it is now two years from now and this position has been a disaster — what went wrong?" Running this adversarial narrative in parallel to the analyst's synthesis forces the system to generate a concrete failure path before any position is sized. For investors, this reframes the risk management question; for developers, it is a concrete design pattern — a parallel agent whose sole job is to construct the most plausible failure scenario, not to validate the thesis.

---

### I011 - Regulatory Risk as a Deterministic Penalty: Why Political Noise Gets a Fixed -2, Not a Narrative
- **Status**: briefed
- **Pillar**: 1 (Diagnostic)
- **Source tier**: 2
- **Source ref**: SKILL.md — "The System Architecture" section: "Regulatory/political risk: deterministic -2 confidence penalty, no override"; also "Legal/investigation risk: -2 confidence penalty, no override available"
- **Audience**: investor
- **Core idea**: When regulatory or political risk is present, most analysts fold it into their narrative — it becomes one more factor to weigh, which means it can be argued away by a sufficiently compelling bull case. EdenFinTech makes a different design choice: regulatory risk triggers a fixed, deterministic -2 confidence penalty with no override available. The penalty cannot be negotiated by the analyst's reasoning. This separates the diagnostic question (does regulatory risk exist?) from the narrative question (how bad is it really?), removing the motivated reasoning step entirely. The content angle for investors: the difference between a system that penalises risk and one that acknowledges it while continuing anyway.

---

### I012 - Evidence Laundering: How LLMs Turn Analyst Bias Into Credible-Looking Research
- **Status**: briefed
- **Pillar**: 2 (Adversarial Architecture)
- **Source tier**: 3
- **Source ref**: Gemini deep research on evidence laundering in LLM finance pipelines (2026-03-16): "An analyst with a gut feeling about a stock prompts an LLM: 'Give me a data-driven thesis on why TechCorp is undervalued.' The LLM obediently cherry-picks financial metrics, summarises positive sentiment from earnings calls, and ignores macroeconomic red flags. The analyst presents this output to an investment committee as 'objective, AI-generated evidence.' The human bias has been successfully laundered through the perceived neutrality of the machine." Sources cited: arxiv.org LLM sycophancy research; getfailsafe.com adversarial prompting in financial AI (2025).
- **Audience**: both
- **Core idea**: LLMs are trained to be helpful, which makes them structurally sycophantic — they will construct a credible-sounding bull case for almost any prompt that asks for one. This means an analyst with a predetermined conclusion can use an LLM to generate what appears to be rigorous independent analysis, but is in fact the analyst's motivated reasoning reflected back at them in authoritative language. EdenFinTech's evidence laundering detection gate exists specifically to catch this: it checks whether the analyst's chain of reasoning is reaching conclusions independently of the evidence, or engineering the evidence to reach a predetermined conclusion. For the developer audience, this is the specific failure mode that RLHF-trained sycophancy introduces into any financial pipeline that lacks adversarial validation.

---

### I013 - Probability Banding: Why 63.7% Is a Lie and 60% Is Honest
- **Status**: briefed
- **Pillar**: 3 (Asymmetry Math)
- **Source tier**: 3
- **Source ref**: Perplexity deep research on probability calibration (2026-03-16): citing Kahneman System 1/System 2 research (Thinking, Fast and Slow); CFO stock market forecast calibration study showing "executives produce distributions too narrow — realized returns fall within their 80% confidence intervals only 36% of the time, not 80%"; Philip Tetlock, Expert Political Judgment (2005), documenting that forecasters assigning precise decimal probabilities are most severely miscalibrated. Brier Score research cited confirming that financial analysis typically cannot distinguish between 63% and 67% precision.
- **Audience**: both
- **Core idea**: When an analyst assigns a 63.7% probability to a thesis, they are not being precise — they are activating anchoring bias in everyone who reads the number. CFO forecasting research shows that professionals with precise point estimates are calibrated only 36% of the time when they claim 80% confidence. EdenFinTech forces probability estimates into four discrete bands: 50, 60, 70, or 80 only. This is not a limitation — it is epistemic honesty. The bands acknowledge that the signal quality in fundamental analysis cannot support decimal precision, and coarser bands have been shown to produce better belief updating when new evidence arrives, because there is no false anchor to defend. For developers, this is a concrete pipeline constraint: probabilities are rounded to the nearest 10 at the 50-80 range before any downstream sizing calculation runs.

---

### I014 - The 30% CAGR Hurdle: Academic Grounding for an Aggressive Return Threshold
- **Status**: briefed
- **Pillar**: 3 (Asymmetry Math)
- **Source tier**: 3
- **Source ref**: Perplexity deep research on deep value hurdle rates (2026-03-16): Henry Oppenheimer, "Ben Graham's Net Current Asset Values: A Performance Update" — net-net stocks achieved compound 28% annual return over 13 years; Stockopedia compilation of published P/NCAV studies showing "20-35%+ annualised returns over different decades internationally" (citing Greenblatt and Oppenheimer); Peter Lynch, Fidelity Magellan Fund — 29.2% average annual return over 13 years vs S&P 500's 14%; AQR Capital Management, "Building a Better Deep Value Portfolio" — confirms positive relationship between value spread and future returns but notes "highly episodic" time profile. Source: netnethunter.com/how-to-pick-value-stocks compilation of academic studies.
- **Audience**: investor
- **Core idea**: The EdenFinTech 30% CAGR hurdle — below which no position is sized — is not an arbitrary threshold. Published academic studies on net-net and extreme value strategies consistently document returns in the 20-35% annualised range when proper screening is applied. Henry Oppenheimer's 13-year study found 28% compound returns; Peter Lynch's Magellan track record hit 29.2%. The hurdle functions as a quality filter: it eliminates positions that are merely cheap without a realistic path to exceptional returns, and forces the system to hold out for genuine asymmetric opportunities. The CAGR < 30% = 0% size rule means the scanner would rather hold no position than accept a mediocre risk-adjusted return in a concentrated portfolio.

---

### I015 - Regulatory Dislocation vs. Permanent Impairment: The Diagnostic the Market Always Gets Wrong
- **Status**: briefed
- **Pillar**: 1 (Diagnostic)
- **Source tier**: 3
- **Source ref**: Perplexity deep research on regulatory risk in deep value investing (2026-03-16): Alibaba's $2.8B antitrust fine (April 2021) — stock fell then rose 9% within two days once investors recognised the fine did not restrict core e-commerce business; contrasted with Didi Chuxing (2021) — forced NYSE delisting and permanent impairment of U.S.-listed equity structure following regulatory defiance (citing academic.oup.com/cmlj analysis of Didi decision and digichina.stanford.edu); MSCI China Index posted 30%+ year-to-date gains in 2025 after 2021-2022 regulatory crackdown created deep dislocation (T. Rowe Price China 2026 outlook, troweprice.com).
- **Audience**: investor
- **Core idea**: The most expensive mistake in deep value investing is confusing regulatory dislocation with permanent impairment. Dislocation is when a regulation reshapes how a business competes — the addressable market and core competitive advantage survive intact. Impairment is when a regulation eliminates the rationale for the business itself. Alibaba's antitrust fine was dislocation: the stock recovered within days once the market correctly read that e-commerce itself was not restricted. Didi's NYSE delisting was impairment for U.S. equity holders: the capital market access the investment thesis depended on was gone. The EdenFinTech diagnostic framework maps directly onto this distinction — regulatory risk triggers the deterministic -2 penalty, but the deeper question the 3-stage analyst asks is whether the catalyst stack can survive the regulatory environment, or whether the moat has been structurally destroyed.
