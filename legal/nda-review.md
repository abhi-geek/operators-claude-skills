# NDA Review

> **Install (global):** `cp legal/nda-review.md ~/.claude/commands/nda-review.md`
> **Install (project):** `cp legal/nda-review.md .claude/commands/nda-review.md`
> **Invoke:** `/nda-review` — attach the NDA file, paste the text, or pass a file path
>
> **Author:** [abhikuchbhi.in](https://abhikuchbhi.in)

---

You are executing a professional NDA review. Read the Non-Disclosure Agreement provided and produce a structured, party-aware analysis that surfaces every material risk, non-standard provision, red flag, and missing clause.

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
1. Check $ARGUMENTS for an explicit signal (e.g., `party=receiving`, `--party disclosing`, or natural language like "we are the receiving party")
2. Check conversation context — has the user described their role?
3. Check memory for stored context about the user's typical role
4. If still unknown, ask (combine with the context question below if that is also unknown)

### 0.3 Determine Deal Context

Determine the type of business relationship covered by this NDA:
- `employment` — employee or contractor onboarding
- `vendor` — supplier, service provider, or outsourcing
- `partnership` — JV, collaboration, or co-development
- `M&A` — merger, acquisition, or due diligence
- `investment` — fundraising, term sheet, or investor due diligence

**Resolution order:**
1. Check $ARGUMENTS for an explicit signal (e.g., `context=vendor`, `--context M&A`)
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
- Weight every finding relative to the harm or exposure it creates for the party being reviewed

### Standard Clause Checklist

| # | Clause Type | What to Evaluate |
|---|---|---|
| 1 | Definition of Confidential Information | Scope breadth; catch-all "any and all information" language; oral disclosure capture; whether marking as "Confidential" is required; whether publicly available information is excluded |
| 2 | Exclusions from CI | Are all four standard exclusions present: (a) publicly available, (b) already known to recipient, (c) independently developed without reference to CI, (d) received from third party without restriction? Each missing exclusion is a separate finding |
| 3 | Permitted Purpose / Use Restriction | Is use limited to a specific defined purpose? Vague or absent purpose = CI can be used for anything |
| 4 | Standard of Care / Protection Obligations | "Reasonable care" (market standard) vs. "same care as own confidential information" (acceptable if qualified) vs. absolute obligation (dangerous for receiving party) |
| 5 | Permitted Disclosures — Employees & Contractors | Can the receiving party share with employees, advisors, or contractors on a need-to-know basis? Must those persons be bound by written obligation? Missing = operational problem |
| 6 | Compelled Disclosure — Legal Process | Subpoena, court order, or regulatory request carve-out — present? Does it require prior written notice to the disclosing party before complying? |
| 7 | Residuals Clause | If present: allows the receiving party's employees to retain and use any information they can remember without reference to written materials — effectively removes protection for internalized knowledge; dangerous for the disclosing party |
| 8 | Term / Duration of Agreement | Clear start and end date? Automatic renewal? Evergreen or indefinite term? |
| 9 | Survival of Confidentiality Obligations | How long do obligations survive termination? 2–3 years = market standard for commercial NDAs; perpetual = aggressive; a carve-out for trade secrets with perpetual treatment = reasonable |
| 10 | Return / Destruction of CI | Mechanism upon termination or on request? Who decides — return vs. destroy? Certification of destruction required? |
| 11 | No License / No Implied Rights | Explicit statement that no IP license is granted — absence creates an implied license argument risk |
| 12 | Ownership of Derivative IP | If any work product, derivative work, or insight is generated using CI, who owns it? |
| 13 | Warranties / Representations by Disclosing Party | Accuracy of CI, non-infringement of third-party rights — overbroad warranties create risk for the disclosing party |
| 14 | Disclaimer of Warranties | Receiving party cannot rely on CI without independent verification — fair, but watch for scope overreach |
| 15 | Injunctive Relief / Equitable Remedies | Right to seek injunction without bond and without proving actual damages — standard; absence is a red flag for the disclosing party |
| 16 | Remedies / Indemnification | Scope of indemnification on breach — unlimited indemnity with no cap = critical risk for the receiving party |
| 17 | Limitation of Liability | Damages cap present? Set at a reasonable level (e.g., fees paid or contract value)? Carve-outs for gross negligence, fraud, and wilful misconduct? |
| 18 | Non-Solicitation / Non-Compete | If included: duration, geographic scope, covered activities — California renders most non-competes unenforceable; check for overreach in any jurisdiction |
| 19 | Governing Law & Jurisdiction | Which law governs? Which courts have jurisdiction? Unilateral jurisdiction clause (other party's home court only)? |
| 20 | Dispute Resolution | Litigation vs. arbitration; venue; mandatory arbitration waiving jury trial; no carve-out for injunctive relief in an arbitration clause = problematic |
| 21 | Severability | If any clause is held unenforceable, does the rest survive? Missing = entire agreement may fail if one clause falls |
| 22 | Assignment | Can obligations be assigned to successors, acquirers, or affiliates without consent? Unilateral assignment right = risk |
| 23 | Entire Agreement / Integration | Supersedes prior agreements? Important if prior confidentiality commitments exist that the party wishes to preserve |
| 24 | Amendment Procedure | How can the NDA be modified? Oral amendments permitted = risky; must be in writing and signed by both parties = standard |
| 25 | Notice Requirements | Formal notice mechanism — how given, to whom, effective when? Missing = procedural gaps in enforcement and termination |

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
| `Silent` | Clause exists but fails to address a key scenario within its scope (e.g., a return/destruction clause that says nothing about cloud-stored copies) — distinct from `Vague`, which is about unclear language |
| `Conflicting` | Two or more clauses directly contradict each other, creating legal ambiguity |

### Severity Definitions

| Severity | Criteria |
|---|---|
| **Critical** | May render the NDA unenforceable, creates uncapped or unlimited liability, or fundamentally alters the party's legal position in a dangerous way |
| **High** | Significantly non-market; material risk if not addressed; strong negotiating priority |
| **Medium** | Non-standard or mildly one-sided; worth flagging but not a deal-breaker |
| **Low** | Minor deviation, ambiguity, or missing detail with limited practical impact |

### Jurisdiction Flag Logic

After identifying the governing law, apply the relevant flags below. Leave blank if no specific concern applies.

| Jurisdiction | Flag When |
|---|---|
| **California (US)** | Non-solicitation or non-compete clauses present — Cal. Bus. & Prof. Code §16600 renders most non-competes and broad non-solicits unenforceable; any geographic or activity restriction on employees or contractors is presumptively void |
| **India** | (a) Non-compete or non-solicit clauses — Section 27 of the Indian Contract Act renders agreements in restraint of trade void, including overbroad CI restrictions framed as trade restraints; (b) Perpetual confidentiality terms — Indian courts scrutinise these; (c) Arbitration clause must comply with the Arbitration and Conciliation Act 1996 — check seat, institution, and applicable rules; (d) Adequate consideration must exist for the NDA to be binding — flag if consideration is unclear or nominal |
| **EU / UK** | (a) CI includes or may include personal data — absence of GDPR or UK GDPR data processing provisions; (b) Cross-border data transfers outside the EEA or UK require Standard Contractual Clauses or equivalent safeguards; (c) Post-Brexit: UK and EU are now separate regimes — a single NDA covering both must address each separately |
| **New York (US)** | Injunctive relief or other equitable remedies without explicit contractual basis — NY courts require strong contractual grounding; flag any clause relying purely on equitable arguments |
| **Singapore** | (a) Non-compete or non-solicit clauses — Singapore applies a reasonableness test (not California's blanket ban); geographic scope, duration, and activities must be proportionate to a legitimate business interest; (b) CI involving personal data — Personal Data Protection Act 2012 (PDPA) applies; transfers to third parties require notification or consent obligations |
| **UAE / Dubai** | (a) Non-compete clauses — Federal Decree-Law No. 33 of 2021 limits post-employment non-competes to a maximum of 2 years and requires a legitimate employer interest; (b) Arbitration clauses referencing UAE — must comply with UAE Federal Arbitration Law No. 6 of 2018; flag if DIFC courts vs. mainland UAE courts jurisdiction is ambiguous (they operate under different legal systems: common law vs. civil law) |
| **Any jurisdiction** | Any clause attempting to override mandatory statutory rights — whistleblower protections, compelled disclosure obligations, statutory notice periods, or employment law protections |

---

## STEP 3 — INTERNAL CONSISTENCY CHECK

After completing the clause-by-clause analysis, run a second pass to find cross-clause conflicts. The goal is to identify places where two clauses, each acceptable in isolation, together create ambiguity, contradiction, or an unintended loophole.

Check every pair below. For each conflict found, add a row to the analysis table with Risk Type `Conflicting` and both section references in the Location column (e.g., `§1.2 ↔ §8.1`).

| Conflict Pair | What to Check |
|---|---|
| Definition of CI ↔ Exclusions | Do the exclusions so broadly exempt information that the CI definition is effectively gutted? Conversely, is the CI definition so narrow that key disclosures fall into an exclusion unintentionally? |
| Term / Duration ↔ Survival | Is the survival duration logically consistent with the agreement term? A 5-year survival on a 1-year NDA creates 6 years of total obligation — intended or a drafting error? |
| Standard of Care ↔ Remedies / Indemnification | If standard of care is "reasonable efforts" but indemnification is unlimited on any breach, the indemnity clause makes the standard of care meaningless — a minor lapse becomes uncapped liability |
| Injunctive Relief ↔ Dispute Resolution | Does a mandatory arbitration clause eliminate or restrict the right to seek injunctive relief? If so, the injunctive relief clause may be illusory — courts in many jurisdictions will not grant injunctions outside the agreed dispute mechanism |
| Permitted Disclosures ↔ Return / Destruction | The receiving party may have legitimately shared CI with contractors. Does the return/destruction clause compel recovery from those third parties? If silent, the return obligation may be practically unenforceable |
| Assignment ↔ Governing Law | If the agreement can be assigned to successors in a cross-border acquisition, does the governing law clause still apply sensibly? A domestic governing law clause on a globally assignable NDA may create conflict-of-laws problems |
| Entire Agreement / Integration ↔ Referenced Documents | Does the NDA reference external documents (exhibits, schedules, master agreements, prior LOIs) that are not provided or are inconsistent? The integration clause may inadvertently override obligations established elsewhere |
| No License ↔ Permitted Purpose | Does the permitted purpose clause implicitly grant a license (e.g., "may use CI to evaluate a potential transaction") that functionally contradicts the no-license clause? |
| Amendment Procedure ↔ Any Other Clause | Does any clause give one party the unilateral right to modify terms — directly contradicting a bilateral written amendment requirement? |
| Permitted Disclosures ↔ Standard of Care | If employees and contractors are permitted recipients but there is no requirement to bind them in writing, and the standard of care is "same as own CI," is the party actually meeting that standard by sharing without written obligations on those recipients? |

---

## STEP 4 — OUTPUT

Produce exactly the following output. No preamble. No suggestions or recommended redlines. No commentary outside the summary and table.

---

### NDA REVIEW SUMMARY

```
Party:          [Receiving / Disclosing / Mutual] — [stated / inferred / assumed]
Context:        [Employment / Vendor / Partnership / M&A / Investment / Unknown]
Governing Law:  [Jurisdiction — or "Not specified"]
Overall Risk:   [Critical / High / Medium / Low] — [#] Critical / [#] High / [#] Medium / [#] Low
Key Issues:     — [Most important finding — one line]
                — [Second most important finding — one line]
                — [Third most important finding — one line, or omit if fewer than 3]
```

---

### ANALYSIS TABLE

| # | Clause Type | Location | Actual Language | Plain English | Risk Type | Severity | Jurisdiction Flag |
|---|---|---|---|---|---|---|---|

**Column rules:**
- **Location** — section or paragraph reference (e.g., §2.1, Clause 4); use `—` for missing clauses and `§X ↔ §Y` for conflicts
- **Actual Language** — verbatim excerpt, max 2 sentences; write `NOT PRESENT` for missing clauses
- **Plain English** — what this means for the party being reviewed, in 1 sentence, no legalese
- **Risk Type** — exactly one of: Overbroad / Vague / Missing / One-sided / Unenforceable / Non-standard / Silent / Conflicting
- **Severity** — Critical / High / Medium / Low
- **Jurisdiction Flag** — specific enforceability concern in the governing law, or blank

**Coverage rule:** All Critical, High, and Medium findings must appear. All Missing and Conflicting entries must appear. Low-severity findings where the clause is present and substantially standard may be omitted.

---

*This review is produced by an AI system and does not constitute legal advice. Engage qualified legal counsel before signing, negotiating, or relying on this analysis.*

*Built by [abhikuchbhi.in](https://abhikuchbhi.in)*
