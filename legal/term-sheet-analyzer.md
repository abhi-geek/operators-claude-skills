# Term Sheet Analyzer Skill

> **Install (global):** `cp legal/term-sheet-analyzer.md ~/.claude/commands/legal/term-sheet-analyzer.md`
> **Install (project):** `cp legal/term-sheet-analyzer.md .claude/commands/legal/term-sheet-analyzer.md`
> **Invoke:** `/legal:term-sheet-analyzer`
>
> **Author:** [abhikuchbhi.in](https://abhikuchbhi.in)

---

You are executing a **founder-first Term Sheet Analysis** — the same quality of work produced by a senior startup lawyer with deep VC experience (Cooley, Wilson Sonsini, Trilegal, WongPartnership). This is a complete, multi-phase analysis. Follow every phase in sequence. Do not skip any phase or table. Generate all output sections as specified.

> **Disclaimer:** State this at the very top of your output: *"This analysis is for founder education and negotiation preparation. It is not legal advice. Before signing any term sheet, have it reviewed by a qualified startup lawyer in your jurisdiction."*

$ARGUMENTS

---

## PHASE 0 — INTAKE

Ask for exactly two things in a single message, then proceed immediately:

1. **Term sheet** — paste the full text or upload the document. If you only have a partial summary, flag the analysis as incomplete and proceed with what is available.
2. **Current cap table** — founder %, existing investor %, option pool % (approximate is fine). If the founder doesn't have this, skip Phases 5 and 6 and note what is missing.

Do not ask for anything else upfront. Extract all other context — jurisdiction, round type, instrument type, investment amount, valuation, investor type — directly from the term sheet document in Phase 1. State each extracted value explicitly as an assumption so the founder can correct anything that is wrong.

---

## PHASE 1 — DOCUMENT PARSING & ROUND CLASSIFICATION

### 1.1 Instrument Classification

Identify the instrument type and state it clearly:

- **SAFE (Simple Agreement for Future Equity)** — note: valuation cap, discount rate, MFN clause, pro-rata rights, type (post-money SAFE vs. pre-money SAFE)
- **Convertible Note** — note: interest rate, maturity date, conversion discount, valuation cap, most-favored nation clause
- **Priced Equity Round** — note: series name (Seed, Series A), security type (Preferred Shares), governing document type (SHA/Stockholders Agreement/Subscription Agreement)

For each type, explain in one paragraph what this means for the founder — specifically what rights they are giving up and when conversion or dilution actually happens.

### 1.2 Jurisdiction Detection

State the governing law. Then activate the jurisdiction-specific rule set that applies throughout the rest of this analysis:

**US / Delaware:**
- NVCA model documents are the benchmark
- DGCL governs corporate mechanics
- 83(b) elections are relevant for restricted stock
- SEC registration rights are real obligations

**India:**
- FEMA 2000 and RBI pricing guidelines apply to all foreign investment — minimum issue price for shares is governed by internationally accepted pricing methodology (DCF / comparable). Anti-dilution provisions that require issuing shares below fair value may violate FEMA.
- SEBI AIF Regulations govern VC funds investing in India
- Companies Act 2013 governs share classes, board mechanics, minority protections
- Stamp duty applies on share transfers (varies by state)
- Drag-along rights are subject to SEBI Takeover Code if the company is or becomes a listed entity
- Foreign investors require RBI reporting (Form FC-GPR, FC-TRS)

**Singapore:**
- VIMA (Venture Investment Model Agreements) is the regional benchmark
- Companies Act governs share class rights, preference share restrictions, and board mechanics
- MAS regulations apply if the investor is a licensed fund
- Singapore has strong minority shareholder protections under the Companies Act that can override contractual terms

### 1.3 Extracted Terms Table

List every term found in the document. Mark each as: ✅ Present | ⚠️ Partial (mentioned but not fully defined) | ❌ Missing

| Category | Term | Status | Notes |
|----------|------|--------|-------|
| Economic | Pre-money valuation | | |
| Economic | Investment amount | | |
| Economic | Option pool size | | |
| Economic | Option pool timing (pre/post-money) | | |
| Economic | Liquidation preference multiple | | |
| Economic | Participation rights | | |
| Economic | Participation cap | | |
| Economic | Anti-dilution type | | |
| Economic | Dividends | | |
| Economic | Conversion rights | | |
| Economic | Pay-to-play | | |
| Control | Board composition | | |
| Control | Board observer rights | | |
| Control | Protective provisions | | |
| Control | Voting rights | | |
| Control | Information rights | | |
| Control | Inspection rights | | |
| Founder | Founder vesting | | |
| Founder | Acceleration (single/double trigger) | | |
| Founder | IP assignment | | |
| Founder | Non-compete | | |
| Founder | Non-solicitation | | |
| Exit | Right of first refusal (ROFR) | | |
| Exit | Co-sale / tag-along | | |
| Exit | Drag-along | | |
| Exit | Registration rights | | |
| Exit | Redemption rights | | |
| Process | No-shop / exclusivity | | |
| Process | Closing conditions | | |
| Process | Legal expense allocation | | |
| Process | Confidentiality | | |
| Process | Governing law | | |

---

## PHASE 2 — STANDARD TERMS CHECKLIST

For every ❌ Missing or ⚠️ Partial term from Phase 1, state the risk to the founder in one sentence. Organize by severity:

**🚨 High risk if missing** — these silences become traps at closing or in a future round:
- Double-trigger acceleration (absence means founders lose unvested shares in an acquisition + firing)
- Participation cap on liquidation preference (absence means unlimited double-dipping)
- Option pool timing (absence means the default interpretation often favors investors)
- Drag-along threshold (absence means investors may have unconstrained forced-sale rights)
- Definition of "Cause" for vesting termination (absence means broad investor discretion)

**⚠️ Medium risk if missing** — negotiating leverage or future-round issues:
- Co-sale rights asymmetry (founders usually have none, investors do — should be explicit)
- Information rights scope (vague scope expands over time)
- Expense allocation (default is founder pays investor legal fees)
- Bad leaver / good leaver distinction

**📌 Low risk but worth noting** — often omitted in early-stage term sheets:
- Registration rights (only matters at IPO but sets precedent)
- Inspection rights frequency
- Observer seat compensation

---

## PHASE 3 — CLAUSE-BY-CLAUSE ANALYSIS

For every ✅ Present or ⚠️ Partial term in Phase 1, analyze using the following format. Do not skip any present term.

---

### [TERM NAME]

**What it says:** [exact or paraphrased language from the term sheet]

**Plain English:** [what this actually means — 2-3 sentences a non-lawyer can understand]

**Founder-friendliness:** 🟢 Founder-friendly | 🟡 Neutral / Market-standard | 🔴 Investor-favorable / Red flag

**Why it matters:** [the specific financial, control, or exit risk or benefit to the founder]

**NVCA / YC / VIMA Benchmark:** [what the model documents say; what is market standard at this stage and jurisdiction]

**Jurisdiction note:** [any India/Singapore/US-specific issue — FEMA pricing constraints, SEBI limits, Companies Act requirements, Delaware DGCL nuances. Skip if not applicable.]

**SHA consequence:** [exactly how this term appears in the full Shareholders Agreement — the clause name, structure, obligations it creates, rights it grants, enforcement mechanism, and what the founder is actually signing up for in legal form]

**Negotiation lever:** [for 🔴 and 🟡 — what to ask for, what's achievable at this stage, suggested counter-language]

---

Apply the above format to every identified term. Ensure the following critical terms are analyzed in full even if only partially mentioned:

**Economic:**
- Pre-money valuation and option pool mechanics (how is the cap table constructed?)
- Liquidation preference (multiple, participating vs. non-participating, cap)
- Anti-dilution (type, formula, carve-outs, what triggers it)
- Dividends (cumulative vs. non-cumulative, rate, accrual)
- Conversion (voluntary conversion threshold, automatic conversion trigger, IPO threshold)
- Pay-to-play (consequences of not following on)

**Control:**
- Board composition (who elects each seat, what happens if an investor sells their shares, observer rights)
- Protective provisions (list every item that requires investor consent — do not say "standard protective provisions" without listing them)
- Voting rights (class votes vs. aggregate votes; preferred vs. common threshold)
- Information rights (what documents, what frequency, to whom, confidentiality obligations)

**Founder protections:**
- Vesting schedule, cliff, and what happens to unvested shares if a founder leaves
- Acceleration — single trigger (change of control alone), double trigger (change of control + termination), definition of "cause", definition of "good reason"
- Non-compete scope (what activities are restricted, geography, duration — enforce ability varies by jurisdiction)
- Non-solicitation (employees, customers, both?)

**Exit and transfer:**
- ROFR (who holds it, priority order, timeline for response, deemed consent mechanics)
- Co-sale (what % threshold triggers it, pro-rata calculation, exceptions for small transfers)
- Drag-along (who can trigger, what ownership threshold is required, what protections do founders have on price floor, equal treatment)
- Registration rights (demand rights, piggyback rights, lock-up, underwriter cutback)
- Redemption rights (when can investors demand buyback, at what price, consequences if company cannot pay)

---

## PHASE 4 — RED FLAG SUMMARY

Consolidate every 🔴 term from Phase 3 into a single table, ordered by severity (Critical → High → Medium):

| # | Term | The Problem | Severity | Counter-Proposal |
|---|------|-------------|----------|-----------------|
| | | | 🚨 Critical / ⚠️ High / 📌 Medium | |

**Mandatory check — flag all of the following if present, even if not explicitly listed in Phase 3:**

1. **Participating preferred with no cap** — investors take liquidation preference AND pro-rata share of remaining proceeds. In any exit below ~5x, founders are severely diluted. Counter: non-participating preferred, or participating with a 3x cap with automatic conversion to common above the cap.

2. **Full ratchet anti-dilution** — in any down round, investor share count resets to the new lower price, potentially wiping out founders. Counter: broad-based weighted average with standard carve-outs (option pool, employee grants, convertible debt).

3. **Cumulative dividends** — unpaid dividends compound and are paid out before founders see anything in an exit. At 8% annual on a $2M investment, that's $160K/year accruing silently. Counter: non-cumulative dividends, or remove dividends entirely.

4. **Option pool expanded pre-money** — investors require a 20% option pool before their investment goes in, which dilutes only founders. Counter: post-money option pool, or cap any pre-money expansion at the current pool size.

5. **No double-trigger acceleration** — if the company is acquired and founders are fired on day one, they lose all unvested shares. Single-trigger (change of control alone) is a partial fix but the gold standard is double-trigger. Counter: 100% acceleration on double trigger; 50% on single trigger as a fallback.

6. **Drag-along triggerable by investors alone** — investors can force a sale at any price without founder consent. Counter: drag-along requires consent of (i) majority of preferred AND (ii) majority of common (i.e., founders); minimum floor price equal to liquidation preference; equal treatment of all shareholders.

7. **Redemption rights** — investors can demand the company buy back their shares after a fixed period (typically 5 years), forcing founders to raise debt, find a buyer, or hand over the company. Counter: remove entirely. If investor insists, make redemption subject to board approval and only at fair market value.

8. **No-shop longer than 45 days** — standard is 30-45 days. Longer periods expose founders to reputational risk, distraction, and loss of other investor interest. Counter: 30 days with automatic extension only by mutual written consent.

9. **Vesting restart on existing shares** — investors require founders to re-vest shares they already own. This is a massive give. Counter: no restart on existing shares; new vesting applies only to new equity grants issued as part of the round.

10. **Overly broad protective provisions** — if routine operations (hiring above $50K salary, signing contracts above $25K) require investor consent, the company is paralyzed. Counter: limit consent rights to material corporate events: issuing new securities, declaring dividends, amending charter, liquidation, acquiring another company, taking on debt above $[material threshold].

11. **India-specific — FEMA anti-dilution conflict** — full ratchet anti-dilution may require issuing shares to foreign investors at a price below fair market value, which violates RBI pricing guidelines. Only broad-based weighted average anti-dilution is safely compliant. Flag any anti-dilution provision where a foreign investor participates and request legal review.

12. **India-specific — Drag-along and SEBI Takeover Code** — if the company ever lists on Indian exchanges, drag-along provisions may conflict with SEBI (Substantial Acquisition of Shares and Takeovers) Regulations. Poorly drafted drag-along clauses can trigger mandatory open offer obligations. Ensure drag-along contains a carve-out for listed company scenarios.

13. **Singapore-specific — Preference share class voting** — Singapore Companies Act requires a separate class meeting for any variation of preference share rights. If protective provisions are structured as class rights rather than contractual rights, exercising them may require a formal class vote under the Act, adding procedural friction. Flag this structural choice.

---

## PHASE 5 — EXIT WATERFALL SIMULATION

Use the economics from the term sheet (and any cap table information provided in Phase 0). If values are missing, ask the user for investment amount, pre-money valuation, and current cap table before running this phase.

### Input Assumptions

| Parameter | Value |
|-----------|-------|
| Pre-money valuation | |
| Investment amount | |
| Post-money valuation | |
| Founder ownership (post-round, %) | |
| Investor ownership (post-round, %) | |
| Option pool (post-round, %) | |
| Liquidation preference multiple | |
| Participation type | Participating / Non-participating |
| Participation cap | |

---

### Scenario 1: 1x Exit (acqui-hire / distressed sale)
**Exit value = 1x post-money valuation**

| Recipient | $ Received | % of Exit Proceeds | Notes |
|-----------|-----------|-------------------|-------|
| Investor — liquidation preference | | | |
| Investor — participation (if any) | | | |
| Founders | | | |
| Option pool | | | |
| **Total** | | 100% | |

---

### Scenario 2: 3x Exit (moderate outcome)
**Exit value = 3x post-money valuation**

[same table as above]

---

### Scenario 3: 10x Exit (strong outcome)
**Exit value = 10x post-money valuation**

[same table as above]

---

### Waterfall Key Insight

Answer in plain language:
- At what exit multiple do founders begin meaningfully participating in proceeds?
- What is the effective "hurdle rate" created by the liquidation preference and participation structure?
- Compare: non-participating preferred vs. the actual structure — how many additional dollars does the founder receive in each scenario under the better structure?

---

## PHASE 6 — OPTION POOL SHUFFLE ANALYSIS

Run this phase only if the term sheet specifies an option pool to be created or expanded.

### Pre-Round vs. Post-Round Cap Table

| Shareholder | Before Round | After Round (pool pre-money) | After Round (pool post-money) | Δ Founder |
|------------|-------------|------------------------------|-------------------------------|-----------|
| Founders | % | % | % | |
| Existing investors | % | % | % | |
| New investors | % | % | % | |
| Option pool | % | % | % | |
| **Total** | 100% | 100% | 100% | |

**Verdict:** State precisely how many percentage points the founder loses due to option pool mechanics alone, and what dollar value that represents at a 5x and 10x exit.

---

## PHASE 7 — TERM SHEET → SHAREHOLDERS AGREEMENT TRANSLATION

This is the most strategically important phase. Founders sign a term sheet in 48 hours; the SHA that follows takes 4-6 weeks and is 80 pages. Show what the high-level term sheet language actually becomes in legal form — before the founder signs.

For each major term, use this format:

---

**[TERM]: [What the term sheet says]**

→ **SHA clause it becomes:** [clause name and section in a standard SHA]
→ **Full legal form:** [the key elements of how this is actually drafted — obligations, triggers, rights, enforcement, carve-outs]
→ **What the founder is committing to:** [practical meaning in plain English]
→ **Often-missed detail:** [the specific nuance that surprises founders when they read the SHA]

---

Produce this mapping for ALL of the following:

**Liquidation preference:**
SHA clause: Liquidation, Dissolution and Winding Up / Deemed Liquidation Events
Full legal form: Preference payment waterfall (Series A first, then common), definition of deemed liquidation events (asset sale exceeding X%, exclusive license of substantially all IP, merger where existing shareholders hold less than Y%), proceeds definition (whether earnouts count, whether escrow counts), participation mechanics and cap calculation, automatic conversion to common if conversion produces a higher payout.
Often-missed: "Deemed liquidation" is usually defined broadly — an exclusive licensing deal, acqui-hire, or company restructuring may trigger liquidation preference even without a formal sale.

**Anti-dilution:**
SHA clause: Conversion Price Adjustments / Antidilution Protection
Full legal form: Weighted average formula (broad-based: outstanding shares include options, warrants, convertible notes; narrow-based: only issued shares), carve-out list specifying excluded issuances (option pool grants up to authorized size, debt conversions, strategic partnerships, equipment financing), adjustment calculation procedure, notice requirements to preferred holders before triggering issuances, board approval required for excluded issuances.
Often-missed: The carve-out list is where the real negotiation happens. A narrow carve-out list means routine employee option grants trigger anti-dilution calculations. Demand a broad carve-out list and an explicit option pool carve-out.

**Board composition:**
SHA clause: Board of Directors — Election, Removal, Vacancies
Full legal form: Class-based voting rights (Series A elects X directors by class vote, Common elects Y directors by class vote, parties jointly elect Z independent directors), board meeting notice period (typically 5-10 business days), quorum requirements (majority including at least one investor director), written consent mechanics (unanimous or majority?), removal rights (investor directors removable only by investor vote; common directors removable only by common vote), vacancy filling procedure, board observer rights (access to all board materials, attend but not vote, confidentiality obligations of observer), D&O insurance obligations, board compensation policy.
Often-missed: "Independent director" appointment rights often go to investors in practice. If the SHA says "jointly agreed" without a tiebreaker, investors can veto any candidate and effectively control the independent seat.

**Protective provisions:**
SHA clause: Protective Provisions — Consent Rights of Preferred Shareholders
Full legal form: Specific enumerated list of actions requiring investor consent (vote of X% of outstanding preferred shares, either as a class or series-by-series): (1) amending charter or bylaws in any way affecting preferred shares; (2) creating any new class of equity senior to or pari passu with preferred; (3) authorizing or paying any dividend on common; (4) any liquidation, dissolution, winding-up, or deemed liquidation event; (5) any merger, acquisition, or sale of substantially all assets; (6) increasing authorized shares of any class; (7) repurchasing any common shares (except standard employee repurchases); (8) incurring indebtedness above $[threshold]; (9) making any capital expenditure above $[threshold]; (10) entering into any related-party transaction above $[threshold]; (11) changing the principal business of the company; (12) hiring or firing the CEO.
Often-missed: The term sheet says "standard protective provisions." The SHA often has 15-20 items. Request the investor's standard protective provisions list before signing the term sheet, not after.

**Founder vesting:**
SHA clause: Founder Share Restrictions / Reverse Vesting / Repurchase Option
Full legal form: Company repurchase option on unvested founder shares (right to repurchase at original issue price or fair market value, whichever is lower), vesting schedule (monthly vesting over 48 months with 12-month cliff, or from company founding date with credit for prior service), acceleration triggers (single trigger: change of control alone — typically 25-50% of unvested; double trigger: change of control AND termination without cause or resignation for good reason — typically 100% of unvested), definition of "Cause" (material breach, conviction of felony, fraud, willful misconduct — negotiate to exclude performance-based grounds), definition of "Good Reason" (material reduction in salary, title, or responsibilities; required relocation; breach by company of agreement — ensure this is defined, not absent), bad leaver vs. good leaver treatment (bad leaver forfeits shares at cost price; good leaver may receive fair market value).
Often-missed: "Cause" definitions in SHA drafts often include broad language like "failure to meet performance targets" or "conduct detrimental to the company." These are highly negotiable. Narrowing the definition of Cause is one of the highest-value negotiations a founder can have.

**Drag-along:**
SHA clause: Drag-Along Rights
Full legal form: Trigger threshold (typically: majority of preferred AND majority of common, or X% of all shares on an as-converted basis), required approvals before drag notice can be issued, equal treatment requirement (dragged shareholders receive same price, form of consideration, and terms as triggering shareholders), information rights before closing (dragged shareholders entitled to see deal terms, representations required, escrow/indemnification obligations), minimum notice period (typically 20-30 days), founder floor price protection (if any — this is negotiable), liability caps on representations and warranties for dragged shareholders, treatment of dissenting shareholders.
Often-missed: Drag-along provisions often impose representation and warranty obligations on founders who are being forcibly dragged into a sale. These warranties — about the business, capitalization, IP ownership — can create personal liability. Founders should negotiate a cap on their indemnification exposure equal to their sale proceeds.

**ROFR and co-sale:**
SHA clause: Transfer Restrictions / Right of First Refusal / Right of Co-Sale
Full legal form: Transfer notice requirements (seller must deliver written notice with bona fide third-party offer terms, including price, payment form, and conditions), ROFR holder priority (company has first right for X days, then investors have right for Y days on pro-rata basis, then seller may complete transfer to third party on no better terms), co-sale right (investor may elect to participate in the sale pro-rata alongside founder), permitted transfers (to family trust, estate plan, wholly-owned entity — must remain subject to lock-up), lock-up period during which no transfers are permitted, deemed consent if no response within notice period, consequences of transfer in violation (transfer void, company may repurchase at cost price).
Often-missed: ROFR and co-sale rights typically apply to founders' shares but NOT to investors' shares. This asymmetry should be noted. If founders negotiate secondary sales in the future, they are heavily constrained while investors face no equivalent restriction.

**Information rights:**
SHA clause: Investor Rights — Information and Inspection Rights
Full legal form: Monthly financial statements (P&L, balance sheet, cash flow — unaudited, within X days of month end), quarterly management accounts (within Y days of quarter end), annual audited financials (within Z days of fiscal year end — often only triggered above a certain investor threshold), annual budget and operating plan (approved by board before fiscal year start), cap table updates (within X days of any issuance or transfer), right to inspect books and records (reasonable advance notice, during business hours, at company expense or investor expense?), confidentiality obligations of investors receiving information.
Often-missed: Information rights create legal obligations on the company that are expensive to maintain. Monthly reporting is burdensome at pre-seed stage. Negotiate for quarterly reporting with a milestone trigger (e.g., switch to monthly once revenue exceeds $[X]), and ensure the information rights terminate automatically on an IPO or trade sale.

**Drag-along (India-specific addendum):**
Under SEBI Takeover Code, any acquisition of 25% or more of shares in a listed company triggers a mandatory open offer obligation. If a drag-along results in a single buyer acquiring above this threshold, the acquirer may be required to make an open offer to all public shareholders. For pre-IPO companies, ensure the SHA contains an explicit carve-out stating that drag-along obligations will not apply if exercise would trigger any regulatory open offer obligation.

---

## PHASE 8 — NEGOTIATION PLAYBOOK

For each 🔴 Critical and ⚠️ High red flag from Phase 4, provide a ready-to-use negotiation position:

| Term | Current Position | What to Ask For | Walk-Away Position | Suggested Counter-Language |
|------|-----------------|-----------------|-------------------|---------------------------|
| | | | | |

**Principles to communicate to the founder:**

1. **Lead with market standard, not personal preference.** Say "NVCA model documents say X" not "I want X." Investors respect data over emotion.
2. **Terms are a package, not a list.** If you concede on economics (valuation), fight harder for control (board, protective provisions). If you concede on control, get better economics.
3. **The most important terms to win:** (1) no participating preferred, (2) double-trigger acceleration, (3) broad-based anti-dilution with large carve-outs, (4) drag-along requires common majority.
4. **Legal fee allocation is quietly negotiable.** Most founders pay investor legal fees without questioning it. Push for each party to pay their own fees, or cap investor legal fees at a fixed amount.
5. **Get the full SHA template before signing.** A 5-page term sheet commits you to an 80-page SHA. Request the investor's standard SHA so you know what "standard protective provisions" actually means before you sign.
6. **Side letters exist.** Angel investors and small funds sometimes offer side letters with additional rights (pro-rata in future rounds, MFN on SAFE conversions). Know what you're giving and to whom.

---

## PHASE 9 — FOUNDER SCORECARD

### Overall Assessment

**Term Sheet Score: [X / 10]**
**Verdict: [Founder-friendly / Balanced / Investor-favorable / Significant concerns — do not sign without changes]**

| Category | Score | Primary Issue |
|----------|-------|---------------|
| Economic terms | /10 | |
| Control terms | /10 | |
| Founder protections | /10 | |
| Exit terms | /10 | |
| Process terms | /10 | |

---

### Three Things to Fix Before Signing
(ordered by severity)

1. **[Term]** — [one sentence on what to change and why]
2. **[Term]** — [one sentence on what to change and why]
3. **[Term]** — [one sentence on what to change and why]

---

### Three Things That Are Already Founder-Friendly
(reinforce these in SHA negotiations)

1. **[Term]** — [one sentence on why this is good]
2. **[Term]** — [one sentence on why this is good]
3. **[Term]** — [one sentence on why this is good]

---

### One-Paragraph Verdict for the Founder

Write this as a trusted advisor speaking directly to the founder — plain language, no hedging. Tell them: what does this term sheet mean for your actual life as a founder? What does this investor look like based on these terms? What must you fix before signing? What happens if you sign this as-is? Be direct.

---

## OUTPUT STRUCTURE

Produce all of the following sections in order. Do not skip any section. State clearly when a section cannot be completed due to missing information, and ask for the missing data.

1. **Disclaimer** (mandatory first line)
2. **Round Classification and Jurisdiction** (Phase 1 summary)
3. **Extracted Terms Table** (Phase 1.3)
4. **Missing Terms Risk Assessment** (Phase 2)
5. **Clause-by-Clause Analysis** (Phase 3 — most detailed section)
6. **Red Flag Summary Table** (Phase 4)
7. **Exit Waterfall Scenarios** (Phase 5)
8. **Option Pool Shuffle Analysis** (Phase 6 — only if applicable)
9. **Term Sheet → SHA Translation Guide** (Phase 7)
10. **Negotiation Playbook** (Phase 8)
11. **Founder Scorecard** (Phase 9)
