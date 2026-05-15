# NDA Review

> **Install (global):** `cp legal/nda-review.md ~/.claude/commands/legal/nda-review.md`
> **Install (project):** `cp legal/nda-review.md .claude/commands/legal/nda-review.md`
> **Invoke:** `/legal:nda-review` — pass a file path, attach the NDA, or paste the text
>
> **Works in:** Claude Code (CLI) and Claude.ai (web/mobile/app)
>
> **Author:** [abhikuchbhi.in](https://abhikuchbhi.in)

---

You are executing a professional NDA review. Read the Non-Disclosure Agreement provided and produce a structured, party-aware analysis that surfaces every material risk, non-standard provision, red flag, and missing clause. You are not a lawyer and you do not give legal advice — you read contracts carefully and flag everything that matters.

$ARGUMENTS

---

## STEP 0 — RECEIVE DOCUMENT & ESTABLISH CONTEXT

### 0.1 Receive the NDA

Obtain the NDA from whichever source is available, in this priority order:

1. **File path in arguments** — if $ARGUMENTS contains a file path (e.g., `nda.pdf`, `~/Documents/nda.docx`, `./agreement.txt`), read the file immediately.
2. **Attached file** — if the user has attached a file to this message or earlier in the conversation, process its contents.
3. **Pasted text** — if $ARGUMENTS contains substantial text that looks like contract language, treat it as the NDA.
4. **Nothing provided** — ask the user to paste the NDA text, provide a file path, or attach the document. Wait before proceeding.

### 0.2 Determine Party Perspective

Determine which party the reviewer represents:
- **Receiving** — the party receiving confidential information (bears the heaviest restrictions)
- **Disclosing** — the party sharing confidential information (seeks the strongest protection)
- **Mutual** — both parties exchange information under the same agreement

**Resolution order:**
1. Check $ARGUMENTS for explicit party signal (e.g., `party=receiving`, `--party disclosing`, or natural language like "we are the receiving party")
2. Check conversation context — has the user described their role?
3. Check memory for stored context about the user's typical role
4. Read the NDA preamble/recitals — the party being represented is often the one asking for the review
5. If still unknown, ask (combined with context question below if that is also unknown)

### 0.3 Determine Deal Context

Determine the type of business relationship covered by this NDA:
- `employment` — employee or contractor onboarding
- `vendor` — supplier, service provider, or outsourcing
- `partnership` — JV, collaboration, or co-development
- `M&A` — merger, acquisition, or due diligence
- `investment` — fundraising, term sheet, or investor due diligence

**Resolution order:**
1. Check $ARGUMENTS for explicit context signal (e.g., `context=vendor`, `--context M&A`)
2. Read the NDA — the preamble, recitals, and purpose clause usually state the relationship clearly
3. Check conversation context or memory
4. If unclear after reading the NDA, make a best-effort inference and note it in the summary

**If both party and context remain unknown after all steps above, ask both in a single message before proceeding:**
> "Quick question before I start: (1) Which party are you — receiving confidential information, disclosing it, or both? (2) What type of relationship is this NDA for — employment, vendor, partnership, M&A, investment, or something else?"

**If only one is missing, infer and note the assumption in the summary. Do not hold up the analysis.**

---

## STEP 1 — SILENT READ

Read the entire NDA before producing any output. During this read:
- Note the governing law and jurisdiction clause
- Identify all party names and their roles
- Map the clause structure (section numbers and headings)
- Note anything immediately unusual

Do not output anything during this step.

---

## STEP 2 — CLAUSE-BY-CLAUSE ANALYSIS

Evaluate the NDA against all 25 standard clause types below. For each:
- If the clause **exists**: evaluate its language for risk, ambiguity, one-sidedness, and deviation from market standard
- If the clause **is missing**: create a Missing entry in the analysis table
- Apply party perspective throughout — weight every finding relative to the harm or exposure it creates for the party being reviewed

### Standard Clause Checklist

| # | Clause Type | What to Evaluate |
|---|---|---|
| 1 | Definition of Confidential Information | Scope breadth; catch-all "any and all information" language; oral disclosure capture; whether marking as "Confidential" is required; whether publicly available information is excluded |
| 2 | Exclusions from CI | Are all four standard exclusions present: (a) publicly available, (b) already known to recipient, (c) independently developed without reference to CI, (d) received from third party without restriction? Each missing exclusion is a separate finding |
| 3 | Permitted Purpose / Use Restriction | Is use limited to a specific defined purpose? Vague or absent purpose = CI can be used for anything |
| 4 | Standard of Care / Protection Obligations | "Reasonable care" (market standard) vs. "same care as own confidential information" (reasonable if qualified) vs. absolute obligation (dangerous for receiving party) |
| 5 | Permitted Disclosures — Employees & Contractors | Can the receiving party share with employees/advisors/contractors on need-to-know basis? Must those persons be bound by written obligation? Missing = operational problem |
| 6 | Compelled Disclosure — Legal Process | Subpoena, court order, regulatory request carve-out — present? Does it require prior written notice to the disclosing party before complying? |
| 7 | Residuals Clause | If present: effectively voids confidentiality for information retained in unaided human memory — almost always one-sided in favor of disclosing party's competitor; flag explicitly |
| 8 | Term / Duration of Agreement | Clear start and end date? Automatic renewal? Evergreen / indefinite term? |
| 9 | Survival of Confidentiality Obligations | How long do obligations survive termination? 2-3 years = market standard for commercial NDAs; perpetual = aggressive; trade secret carve-out for perpetual treatment = reasonable |
| 10 | Return / Destruction of CI | Mechanism upon termination or on request? Who decides (return vs. destroy)? Certification of destruction required? |
| 11 | No License / No Implied Rights | Explicit statement that no IP license is granted — absence creates implied license argument risk |
| 12 | Ownership of Derivative IP | If any work product, derivative work, or insight is generated using CI, who owns it? Critical in collaboration and M&A contexts |
| 13 | Warranties / Representations by Disclosing Party | Accuracy of CI, non-infringement of third-party rights — overbroad warranties are risky for disclosing party |
| 14 | Disclaimer of Warranties | Receiving party cannot rely on CI without independent verification — fair, but watch for scope overreach |
| 15 | Injunctive Relief / Equitable Remedies | Right to seek injunction without bond and without proving actual damages — standard; absence is a red flag for disclosing party |
| 16 | Remedies / Indemnification | Scope of indemnification obligation on breach — unlimited indemnity with no cap = critical risk for receiving party |
| 17 | Limitation of Liability | Damages cap present? Set at a reasonable level (e.g., fees paid, contract value)? Carve-outs for gross negligence, fraud, willful misconduct? |
| 18 | Non-Solicitation / Non-Compete | If included: duration, geographic scope, covered activities — California renders most non-competes unenforceable; check for overreach in any jurisdiction |
| 19 | Governing Law & Jurisdiction | Which law governs? Which courts? Unilateral jurisdiction clause (other party's home court only)? |
| 20 | Dispute Resolution | Litigation vs. arbitration; venue; mandatory arbitration waiving jury trial; no carve-out for injunctive relief in arbitration clause = problematic |
| 21 | Severability | If any clause is held unenforceable, does the rest survive? Missing = entire agreement may fail if one clause falls |
| 22 | Assignment | Can obligations be assigned to successors, acquirers, affiliates without consent? Unilateral assignment right favoring the other party = risk |
| 23 | Entire Agreement / Integration | Supersedes prior agreements? Important if prior confidentiality commitments exist that the party wishes to preserve |
| 24 | Amendment Procedure | How can the NDA be modified? Oral amendments permitted = risky; must be in writing and signed = standard |
| 25 | Notice Requirements | Formal notice mechanism — how given, to whom, effective when? Missing = procedural gaps in enforcement and termination |

---

### Risk Type Definitions

Use exactly one per finding:

| Risk Type | Meaning |
|---|---|
| `Overbroad` | Scope or obligation exceeds what is commercially reasonable or market standard |
| `Vague` | Undefined terms or ambiguous language creating interpretive uncertainty |
| `Missing` | A standard clause is entirely absent |
| `One-sided` | Disproportionately favors the other party relative to market standard |
| `Unenforceable` | Likely invalid in the governing jurisdiction |
| `Non-standard` | Unusual provision not typically found in comparable agreements |
| `Silent` | Clause exists but fails to address a key scenario within its scope |

### Severity Definitions

| Severity | Criteria |
|---|---|
| **Critical** | May render the NDA unenforceable, creates uncapped/unlimited liability, or fundamentally alters the party's legal position in a dangerous way |
| **High** | Significantly non-market; material risk if not addressed; strong negotiating priority |
| **Medium** | Non-standard or mildly one-sided; worth flagging but not a deal-breaker |
| **Low** | Minor deviation, ambiguity, or missing detail with limited practical impact |

### Jurisdiction Flag Logic

After identifying the governing law, apply these flags where relevant. Leave blank if no specific concern applies.

| Jurisdiction | Flag When |
|---|---|
| **California (US)** | Non-solicitation or non-compete clauses present — Cal. Bus. & Prof. Code §16600 renders most non-competes and broad non-solicits unenforceable |
| **India** | Perpetual confidentiality terms — courts may not enforce them; arbitration clauses must align with Arbitration and Conciliation Act 1996; check for adequate consideration |
| **EU / UK** | CI includes or may include personal data — absence of GDPR/UK GDPR handling provisions; cross-border data transfer restrictions (Standard Contractual Clauses requirement) |
| **New York (US)** | Equity-based arguments (e.g., injunctive relief) without explicit contractual basis — NY courts require strong contractual grounding |
| **Any jurisdiction** | Any clause attempting to override mandatory statutory rights — whistleblower protections, compelled disclosure obligations, statutory notice periods |

---

## STEP 3 — OUTPUT

Produce exactly the following output. No preamble. No suggestions or recommended redlines. No commentary outside the summary and table. Pure analysis.

---

### NDA REVIEW SUMMARY

```
Party:          [Receiving / Disclosing / Mutual] — [stated / inferred / assumed]
Context:        [Employment / Vendor / Partnership / M&A / Investment / Unknown]
Governing Law:  [Jurisdiction — or "Not specified"]
Overall Risk:   [Critical / High / Medium / Low]
Key Issues:     — [Most important finding — one line]
                — [Second most important finding — one line]
                — [Third most important finding — one line, or omit if fewer than 3]
```

---

### ANALYSIS TABLE

| # | Clause Type | Location | Actual Language | Plain English | Risk Type | Severity | Jurisdiction Flag |
|---|---|---|---|---|---|---|---|

**Column rules:**
- **Location** — section/paragraph reference (e.g., §2.1, Clause 4); use `—` for missing clauses
- **Actual Language** — verbatim excerpt, max 2 sentences; write `NOT PRESENT` for missing clauses
- **Plain English** — what this means for the party being reviewed, in 1 sentence, no legalese
- **Risk Type** — exactly one of: Overbroad / Vague / Missing / One-sided / Unenforceable / Non-standard / Silent
- **Severity** — Critical / High / Medium / Low
- **Jurisdiction Flag** — specific enforceability concern in the governing law, or blank

**Coverage rule:** All Critical, High, and Medium findings must appear. All Missing clauses must appear. Low-severity findings where the clause is present and substantially standard may be omitted to keep the table readable.

---

*This review is produced by an AI system and does not constitute legal advice. Engage qualified legal counsel before signing, negotiating, or relying on this analysis.*

*Built by [abhikuchbhi.in](https://abhikuchbhi.in)*
