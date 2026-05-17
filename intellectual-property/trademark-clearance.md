# Trademark Clearance

> **Install (global):** `cp intellectual-property/trademark-clearance.md ~/.claude/commands/intellectual-property/trademark-clearance.md`
> **Install (project):** `cp intellectual-property/trademark-clearance.md .claude/commands/intellectual-property/trademark-clearance.md`
> **Invoke:** `/intellectual-property:trademark-clearance` — pass a name, or run with no arguments to be interviewed
>
> **Works in:** Claude Code (CLI) and Claude.ai (web/mobile/app)
>
> **Author:** [abhikuchbhi.in](https://abhikuchbhi.in)

---

You are executing a **comprehensive trademark and brand name clearance screening** — a multi-step check that surfaces conflicts, risks, and availability signals across trademark registries, the open web, domain registrars, social platforms, and regulatory databases before a name is adopted or filed.

$ARGUMENTS

---

## IMPORTANT: SEARCH APPROACH & LIMITATIONS

This skill uses **web search and publicly indexed data**. Direct access to USPTO TSDR, EUIPO eSearch, WIPO Global Brand Database, IP India, and UK IPO is blocked to automated tools (CAPTCHA, 403, JS-only interfaces). All trademark data is retrieved via structured web searches that surface indexed records from Justia Trademarks, Trademarkia, USPTO.report, and official database search-result snippets.

**This is a preliminary screening — not a formal clearance opinion.** It does not replace a full professional trademark search using Derwent, CompuMark, or direct database access by a qualified trademark attorney. Design marks (logos) cannot be searched with this tool. Always engage counsel before filing.

---

## PHASE 0 — STARTUP INTERVIEW

Ask the following in a single message. Wait for all answers before proceeding.

1. **Mark name** — the exact word(s) or phrase being evaluated (spell it exactly as intended)
2. **What it is for** — is this a company name, product name, service name, or personal brand?
3. **Goods / services description** — 2–4 sentences: what does the company/product/service do?
4. **Target markets** — which countries/regions matter most? (e.g., US, UK, EU, India, Canada, Australia — list all that apply)
5. **Entity type** — Startup / SME / Large Enterprise / Individual — affects which regulatory prohibitions apply
6. **Industry** — pick the closest: Technology / Finance / Healthcare / Consumer Goods / Food & Beverage / Media & Entertainment / Education / Legal / Real Estate / Other
7. **Nice class hint (optional)** — if you already know which trademark class(es) you're targeting, state them; otherwise leave blank and the skill will determine them

**Store all answers in memory for the full session. Reference them throughout every step.**

---

## NICE CLASS DETERMINATION

Before Step 1, determine the applicable Nice Classification classes based on the goods/services description and industry provided.

Use this reference to identify the 1–3 most relevant classes:

| Class | Covers |
|---|---|
| 9 | Software, apps, hardware, electronic devices, downloadable content |
| 16 | Printed materials, books, publications, stationery |
| 25 | Clothing, footwear, headgear |
| 35 | Business services, advertising, retail, SaaS (business-facing), HR services |
| 36 | Financial services, insurance, banking, payments, fintech |
| 38 | Telecommunications, messaging, streaming infrastructure, internet services |
| 41 | Education, training, entertainment, publishing, media content |
| 42 | Software-as-a-service (tech-facing), IT services, cloud, R&D, cybersecurity, AI/ML |
| 44 | Healthcare, medical services, telemedicine |
| 45 | Legal services, security services, social networking (personal) |

**Document determined classes** — these anchor every trademark search in Step 7.

---

## OUTPUT STRUCTURE

Produce output in this exact sequence:

1. **Executive Summary** (generated last, presented first)
2. Step 1 through Step 10 findings, in order
3. **Final Risk Matrix**
4. **Recommended Actions**

---

## STEP 1 — BRAND DISTINCTIVENESS ASSESSMENT

Before searching for conflicts, assess whether the name is inherently protectable.

### 1.1 Distinctiveness Scale

Classify the mark on this scale. Classification affects how strongly to weight conflicts found later.

| Category | Definition | Protectability | Example |
|---|---|---|---|
| **Fanciful** | Invented word with no prior meaning in any language | Strongest — broadest protection | KODAK, XEROX, HÄAGEN-DAZS |
| **Arbitrary** | Real word with no logical connection to the goods/services | Strong | APPLE (computers), AMAZON (retail) |
| **Suggestive** | Hints at a quality without directly describing it; requires imagination to connect | Good | NETFLIX, UBER, SLACK |
| **Descriptive** | Directly describes a feature, quality, or characteristic of the goods/services | Weak — only registrable with proof of acquired distinctiveness (secondary meaning) | SPEEDY (for courier), COLD AND CREAMY (for ice cream) |
| **Generic** | The common name for the goods or services themselves | Cannot be registered | BICYCLE (for bicycles), SOFTWARE (for software) |

**Run this search to check if the word exists in standard English or another language:**
- WebSearch: `"[MARK]" meaning definition dictionary`
- WebSearch: `"[MARK]" word origin etymology`

### 1.2 Compound / Stylized Marks

If the mark is two or more words combined:
- Assess each component word individually
- Assess the combined phrase as a whole
- Note if any component is disclaimed (generic elements cannot be owned exclusively)

### 1.3 Step 1 Output

```
DISTINCTIVENESS ASSESSMENT
Mark: [MARK]
Classification: Fanciful / Arbitrary / Suggestive / Descriptive / Generic
Rationale: [1–2 sentences]
Registrability Signal: Strong / Moderate / Weak / Not Registrable
Key Risk: [If descriptive or generic, flag clearly]
```

---

## STEP 2 — MEANING & CULTURAL SENSITIVITY ANALYSIS

A name that is neutral in English may be offensive, vulgar, generic, or legally restricted in another language. This step is critical for international brands.

### 2.1 Languages to Check

Always check the following, plus any language dominant in the user's target markets:

| Language | Check When |
|---|---|
| Spanish | Always (US Hispanic market, Latin America, Spain) |
| French | Always (Canada, France, Belgium, West Africa) |
| Mandarin Chinese | Target market includes China, Taiwan, Singapore, or any tech/consumer market |
| Hindi | Target market includes India |
| Arabic | Target market includes Middle East or North Africa |
| Portuguese | Target market includes Brazil or Portugal |
| German | Target market includes Germany, Austria, Switzerland |
| Japanese | Target market includes Japan or East Asia |
| Russian | Target market includes Russia, Eastern Europe |
| Korean | Target market includes South Korea |

### 2.2 Search Protocol

For each relevant language, run:
- WebSearch: `"[MARK]" meaning [language]`
- WebSearch: `"[MARK]" translation [language]`
- WebSearch: `"[MARK]" [language] slang OR offensive OR vulgar`

### 2.3 Cultural Sensitivity Checks

Beyond literal translation, check:
- Does the name resemble a taboo word in any target language? (homophones, near-homophones)
- Does it have religious or political connotations in any region?
- Does it reference a sensitive historical event, figure, or symbol?
- Is the name associated with a negative brand, scandal, or crisis in any market?

WebSearch: `"[MARK]" controversial OR offensive OR problematic [region/country]`

### 2.4 Step 2 Output

```
MEANING & CULTURAL ANALYSIS
```

| Language / Region | Meaning / Translation | Flag? | Notes |
|---|---|---|---|
| English | [meaning or "no standard meaning"] | — | |
| Spanish | [translation if any] | 🔴 / 🟡 / ✅ | |
| French | [translation if any] | 🔴 / 🟡 / ✅ | |
| Mandarin | [translation if any] | 🔴 / 🟡 / ✅ | |
| Hindi | [translation if any] | 🔴 / 🟡 / ✅ | |
| [other relevant languages] | | | |

🔴 = Offensive, vulgar, or severely negative  
🟡 = Mildly negative, ambiguous, or generic in that language  
✅ = Neutral or positive

---

## STEP 3 — MARKET PRESENCE & COMMON LAW SEARCH

Common law trademark rights exist through USE, not registration. A prior user of the same name for similar goods/services has priority in common law jurisdictions (US, UK, Canada, Australia, India) even without a registered mark.

### 3.1 Exact Name Searches

Run all of the following:

- WebSearch: `"[MARK]" company`
- WebSearch: `"[MARK]" startup`
- WebSearch: `"[MARK]" brand`
- WebSearch: `"[MARK]" product`
- WebSearch: `"[MARK]" service`
- WebSearch: `"[MARK]" [industry from startup interview]`

For each result that appears to be a business or product using this name: record the name, what they do, jurisdiction, and how long they appear to have been operating (check founding year, domain age, earliest web references).

### 3.2 Phonetic Variants

Generate and search for the 4–6 most likely phonetically similar names. Think: same sound, different spelling.

Examples: LYFT → LIFT, KWIL → QUILL, FLAIR → FLAYR → FLAER

- WebSearch: `"[PHONETIC-VARIANT]" company OR brand OR startup`

For each phonetic variant that returns a real business in the same industry — flag it.

### 3.3 Visual / Structural Similarity

Generate 3–4 visually similar names (same letter pattern, one letter changed, common abbreviation):

- WebSearch: `"[VISUAL-VARIANT]" [industry] company`

### 3.4 News & Press Coverage

- WebSearch: `"[MARK]" founded OR launched OR raised OR startup news`
- WebSearch: `"[MARK]" [industry] [year range: last 10 years]`

### 3.5 Step 3 Output

```
MARKET PRESENCE FINDINGS
```

| Name Found | Type | Industry | Jurisdiction | Est. Operating Since | Conflict Risk | Source |
|---|---|---|---|---|---|---|
| [name] | Exact / Phonetic / Visual | | | | High / Medium / Low | [URL] |

Flag any business operating in the same or adjacent industry as **High risk**.

---

## STEP 4 — SEO VISIBILITY & MISSPELLING VARIANTS

### 4.1 Search Engine Dominance

Who owns the search results for this name? If a competitor owns page 1, the brand name has a discoverability problem even if there is no trademark conflict.

- WebSearch: `[MARK]` (plain search, no quotes — assess top 10 results)
- WebSearch: `[MARK] [industry]`

Record: who dominates the top results? Are they a direct competitor? Is the name strongly associated with another brand?

### 4.2 Common Misspellings

Generate the 5–8 most likely misspellings or typos of the mark. Think: double letters, transpositions, phonetic respellings, missing letters.

For each misspelling:
- WebSearch: `"[MISSPELLING]"` — does a real business come up?
- Note if a misspelling resolves to a competitor, controversial entity, or blocked term

### 4.3 Autocomplete & Related Searches

- WebSearch: `[MARK] is` — what does Google autocomplete suggest?
- WebSearch: `[MARK] reviews` — is the name already associated with a product people review?
- WebSearch: `[MARK] scam OR fraud` — any negative association?

### 4.4 Step 4 Output

```
SEO & MISSPELLING ANALYSIS
```

| Variant | Type | Search Result | Risk | Notes |
|---|---|---|---|---|
| [MARK] (exact) | Exact | [who dominates] | High / Med / Low | |
| [misspelling 1] | Typo | | | |
| [phonetic variant] | Phonetic | | | |

---

## STEP 5 — DOMAIN AVAILABILITY

### 5.1 Primary Domain (.com)

`.com` is the gold standard. If it is taken, assess:
- Who owns it? Is it a direct competitor, a squatter, or an unrelated business?
- Is it actively used (live website) or parked?
- Is it listed for sale? If so, at what approximate price?

Searches:
- WebSearch: `[mark].com` — does it resolve to an active website?
- WebSearch: `who owns [mark].com`
- WebSearch: `[mark].com for sale` — is it being sold?
- WebFetch: `https://[mark].com` — try to fetch; if it loads, it's in use

### 5.2 Important Secondary TLDs

Check the following, flagging any that are taken and in active use:

| TLD | Priority | When Most Important |
|---|---|---|
| .com | Critical | Always |
| .co | High | Tech startups, global brands |
| .io | High | Tech / developer tools |
| .ai | High | AI / machine learning products |
| .app | Medium | Mobile applications |
| .net | Medium | Infrastructure, networking |
| .org | Medium | Nonprofits, open source |
| .co.uk | High | UK market |
| .in | High | India market |
| .de | Medium | Germany market |
| .com.au | Medium | Australia market |
| .ca | Medium | Canada market |
| .eu | Medium | EU market |

For each TLD in the user's target markets, run:
- WebSearch: `[mark].[tld]` — check if it resolves to an active site
- WebSearch: `"[mark].[tld]" domain`

### 5.3 Step 5 Output

```
DOMAIN AVAILABILITY
```

| Domain | Status | Current Owner / Use | Risk | Notes |
|---|---|---|---|---|
| [mark].com | ✅ Available / 🔴 Taken — Active / 🟡 Taken — Parked | | | |
| [mark].co | | | | |
| [mark].io | | | | |
| [mark].ai | | | | |
| [mark].co.uk | | | | |
| [mark].in | | | | |
| [relevant TLDs] | | | | |

---

## STEP 6 — SOCIAL MEDIA HANDLE AVAILABILITY

> **⚠️ CONDITIONAL STEP:** Run this step **only if** the mark is a **brand name or company name**. If the user stated in Phase 0 that this is a **product name**, skip this step entirely and proceed directly to Step 7. Social media handle availability is only relevant when the mark will represent a public-facing identity (company, personal brand, or service brand), not when it is a product name sold through OEM or distribution channels.

### 6.1 Platform Checks

For each platform, check whether the exact handle `@[mark]` (or `/[mark]` for LinkedIn) is taken.

**Search approach per platform:**

| Platform | Search Query | Direct URL to try (WebFetch) |
|---|---|---|
| X / Twitter | `@[mark] twitter OR x.com` | `https://x.com/[mark]` |
| Instagram | `@[mark] instagram` | `https://www.instagram.com/[mark]/` |
| LinkedIn Company | `[mark] company linkedin` | `https://www.linkedin.com/company/[mark]/` |
| YouTube | `[mark] youtube channel` | `https://www.youtube.com/@[mark]` |
| TikTok | `@[mark] tiktok` | `https://www.tiktok.com/@[mark]` |
| Facebook | `[mark] facebook page` | `https://www.facebook.com/[mark]` |
| GitHub | `[mark] github organization` | `https://github.com/[mark]` |
| Reddit | `r/[mark] subreddit` | `https://www.reddit.com/r/[mark]/` |

For each: try WebFetch on the URL. If it returns a real profile/page, the handle is taken. If 404, it may be available (not guaranteed — platforms don't expose availability directly).

Also run the WebSearch query for any platform where WebFetch fails.

### 6.2 Handle Squatting

If a handle is taken but appears inactive (no posts, default avatar, created years ago), note it — handle squatters can sometimes be reported to the platform if a trademark is registered.

### 6.3 Step 6 Output

```
SOCIAL MEDIA HANDLE AVAILABILITY
```

| Platform | Handle | Status | Active? | Followers / Activity | Risk |
|---|---|---|---|---|---|
| X / Twitter | @[mark] | ✅ Available / 🔴 Taken / ❓ Unknown | Yes / No / Unknown | | |
| Instagram | @[mark] | | | | |
| LinkedIn | /company/[mark] | | | | |
| YouTube | @[mark] | | | | |
| TikTok | @[mark] | | | | |
| Facebook | /[mark] | | | | |
| GitHub | /[mark] | | | | |

---

## STEP 7 — TRADEMARK SCREENING

This is the core legal search. Search for registered and pending trademarks that are identical or similar to the mark, in the user's target jurisdictions and Nice classes.

**Search philosophy:** Run multiple query variations per jurisdiction. Trademark databases are indexed differently across third-party aggregators — one query is not enough.

### 7.1 US Trademark Search (USPTO)

Run all of the following searches:

```
WebSearch: "[MARK]" trademark USPTO
WebSearch: "[MARK]" trademark serial number registration class
WebSearch: "[MARK]" trademark "IC 0[CLASS]" registered OR pending
WebSearch: "[MARK]" trademark owner registered active
WebSearch: site:trademarks.justia.com "[MARK]"
WebSearch: site:uspto.report "[MARK]" trademark
WebSearch: "[MARK]" trademark "United States" class [CLASS NUMBER]
```

For each registration or application found, record:

| Field | Record |
|---|---|
| Serial Number | SN XXXXXXXX |
| Registration Number | RN XXXXXXX (if granted) |
| Mark | Exact text of the mark |
| Owner | Registrant name |
| Status | Live/Active / Pending / Abandoned / Expired / Cancelled |
| Nice Classes | IC 0XX |
| Goods / Services | Description of covered goods/services |
| Filing Date | |
| Registration Date | (if granted) |
| Expiry / Renewal Due | |

### 7.2 EU Trademark Search (EUIPO)

```
WebSearch: "[MARK]" trademark EUIPO "European Union"
WebSearch: "[MARK]" EUTM registration class [CLASS]
WebSearch: "[MARK]" trademark EUIPO owner status
WebSearch: "[MARK]" trademark "European Union Trade Mark"
```

### 7.3 UK Trademark Search (UKIPO)

```
WebSearch: "[MARK]" trademark "UK IPO" OR "Intellectual Property Office" UK
WebSearch: "[MARK]" trademark UK registered class [CLASS]
WebSearch: "[MARK]" trademark "United Kingdom" registration owner
```

### 7.4 India Trademark Search (IP India)

```
WebSearch: "[MARK]" trademark India "Trade Marks Registry" OR "IP India"
WebSearch: "[MARK]" trademark registered India class [CLASS]
WebSearch: "[MARK]" trademark "Intellectual Property India" owner
WebSearch: "[MARK]" brand trademark India registration
```

### 7.5 WIPO / Madrid International

```
WebSearch: "[MARK]" trademark WIPO Madrid international registration
WebSearch: "[MARK]" international trademark "Madrid Protocol"
WebSearch: "[MARK]" trademark WIPO class [CLASS] owner
```

### 7.6 Canada (CIPO)

```
WebSearch: "[MARK]" trademark Canada CIPO registered
WebSearch: "[MARK]" trademark "Canadian Intellectual Property Office"
```

### 7.7 Australia (IP Australia)

```
WebSearch: "[MARK]" trademark Australia "IP Australia" registered
WebSearch: "[MARK]" trademark Australia class [CLASS]
```

### 7.8 China (CNIPA)

```
WebSearch: "[MARK]" trademark China CNIPA registered
WebSearch: "[MARK]" trademark China registered owner class
```

### 7.9 Additional Jurisdictions

For any other jurisdiction in the user's target markets, run:
```
WebSearch: "[MARK]" trademark [COUNTRY] registered OR pending
WebSearch: "[MARK]" trademark [COUNTRY] owner class [CLASS]
```

### 7.10 Conflict Classification

For every trademark found, classify the conflict level:

| Conflict Level | Criteria |
|---|---|
| 🔴 **Blocking** | Active/registered mark; same or highly similar name; same or overlapping Nice class; same or adjacent industry |
| 🟠 **High Risk** | Active/registered mark; same name; different class but adjacent industry OR similar name in same class |
| 🟡 **Watch** | Pending application (not yet registered); or same name in a clearly different class/industry; or mark in a jurisdiction outside user's target markets |
| 🟢 **Low / Informational** | Abandoned, cancelled, or expired mark; or very different name with minor similarity; or no overlap in class or goods |

### 7.11 Step 7 Output

```
TRADEMARK SCREENING RESULTS
Nice Classes Searched: [list determined classes]
```

| # | Mark | Owner | Jurisdiction | Status | Classes | Goods / Services | Conflict Level | Notes |
|---|---|---|---|---|---|---|---|---|
| 1 | | | | | | | | |

---

## STEP 8 — LIKELIHOOD OF CONFUSION ANALYSIS

For every 🔴 Blocking or 🟠 High Risk mark found in Step 7, run a likelihood-of-confusion analysis. This is the legal test used by trademark offices worldwide to determine whether two marks are too similar to coexist.

### 8.1 The DuPont Factors (US) / Global Equivalents

Assess each of these factors for each conflicting mark:

| Factor | Question to Answer | Weight |
|---|---|---|
| **Similarity of marks** | How similar are the marks in appearance, sound, and meaning? (all three are assessed) | High |
| **Similarity of goods/services** | How similar are the goods/services covered? Same class is a strong indicator but not dispositive — different classes can still overlap | High |
| **Channels of trade** | Would consumers encounter both marks in the same places (same stores, same websites, same events)? | High |
| **Consumer sophistication** | Are the buyers expert professionals (lower confusion risk) or general consumers (higher confusion risk)? | Medium |
| **Strength of the cited mark** | Is the existing mark famous (e.g., Apple, Google) or weak (generic, descriptive)? Famous marks get wider protection | High |
| **Actual confusion evidence** | Any documented instances of consumers confusing the two marks? (Usually N/A at clearance stage) | High (if found) |
| **Crowded field** | Are there many similar marks in this space? If so, individual marks get narrower protection | Medium |
| **Intent** | Was the applicant aware of the existing mark when adopting the name? | Medium |

### 8.2 Confusion Assessment Output

For each High Risk or Blocking mark, produce:

```
LIKELIHOOD OF CONFUSION — [CITED MARK] vs. [USER'S MARK]

Cited Mark: [mark name]
Owner: [owner]
Jurisdiction: [jurisdiction]
Status: [status]
Classes: [classes]

Similarity Assessment:
  — Appearance: [Identical / Highly Similar / Similar / Dissimilar] — [reason]
  — Sound: [Identical / Highly Similar / Similar / Dissimilar] — [reason]
  — Meaning: [Identical / Similar / Dissimilar / No meaning] — [reason]

Goods / Services Overlap: [High / Medium / Low / None] — [reason]
Channel Overlap: [High / Medium / Low] — [reason]
Strength of Cited Mark: [Strong / Moderate / Weak]

Overall Confusion Risk: 🔴 High / 🟠 Moderate / 🟡 Low

Available Options:
  1. [Design-around option if any]
  2. [Coexistence argument if any — different class, different geography]
  3. [Counsel recommendation]
```

---

## STEP 9 — COMPANY NAME REGISTRY CHECK

Trademark registration and company name registration are separate. Even if a name clears trademark screening, the exact company name may be taken in the incorporation registry.

### 9.1 US — State-Level (Delaware & Home State)

```
WebSearch: "[MARK] Inc" OR "[MARK] LLC" Delaware registered corporation
WebSearch: "[MARK]" Delaware corporation entity registered
WebSearch: "[MARK] Inc" [user's home state] corporation LLC registered
```

Delaware is the default for US startups. Also check the state where the company will operate.

### 9.2 UK — Companies House

```
WebSearch: "[MARK]" "Companies House" UK registered company
WebSearch: "[MARK] Ltd" OR "[MARK] Limited" UK registered
```

### 9.3 India — MCA (Ministry of Corporate Affairs)

```
WebSearch: "[MARK]" MCA India registered company "Ministry of Corporate Affairs"
WebSearch: "[MARK] Private Limited" OR "[MARK] Ltd" India registered
```

### 9.4 Other Jurisdictions

For each target jurisdiction, run:
```
WebSearch: "[MARK]" [company registry name] [country] registered entity
```

### 9.5 Step 9 Output

```
COMPANY NAME REGISTRY CHECK
```

| Jurisdiction | Registry | Name Searched | Status | Notes |
|---|---|---|---|---|
| US (Delaware) | Delaware Division of Corporations | [MARK] Inc / LLC | Available / Taken | |
| UK | Companies House | [MARK] Ltd | Available / Taken | |
| India | MCA | [MARK] Private Limited | Available / Taken | |

---

## STEP 10 — GOVERNMENT BANS & PROHIBITED TERMS

Certain words are prohibited or restricted by law from use in company names, trademarks, or branding. Filing a trademark application containing a prohibited term will result in refusal.

### 10.1 Universal Prohibited Categories

Always check if the mark contains or implies any of the following:

| Category | Examples | Why Prohibited |
|---|---|---|
| **National symbols** | Flag, coat of arms, official seal, national emblem | Cannot be monopolized by private parties |
| **Royal / government terms** | Royal, Crown, Imperial, Federal, National, State, Municipal | Restricted in most jurisdictions |
| **Financial / banking terms** | Bank, Banker, Banking, Deposit, Savings, Trust, Insurance | Regulated — require license to use in a name |
| **Medical / pharmaceutical** | Hospital, Clinic, Pharmacy, Medicine, Drug, Prescription | Require regulatory approval in most countries |
| **Legal profession** | Attorney, Solicitor, Barrister, Notary, Law Firm | Reserved for licensed legal professionals |
| **Olympic / Paralympic** | Olympic, Paralympic, Olympiad, and related symbols | Protected globally by the International Olympic Committee |
| **Red Cross / Red Crescent** | Red Cross, Red Crescent, Red Crystal | Protected by Geneva Conventions |
| **Generic geographic terms** | The sole use of a country or city name as a trademark is generally refused |
| **Deceptive terms** | Any term that falsely implies an official government affiliation |
| **Obscene / scandalous matter** | Any immoral, deceptive, or scandalous term | Refused on public policy grounds |

### 10.2 Jurisdiction-Specific Prohibitions

**United States (USPTO)**
```
WebSearch: "[MARK]" USPTO refusal OR "Section 2(a)" OR "Section 2(b)" prohibited trademark
```
Key grounds for refusal: scandalous matter (§2a), geographic deception (§2e), primarily merely a surname (§2e4), disparaging marks.

**United Kingdom (UKIPO)**
```
WebSearch: "[MARK]" UK trademark refused OR prohibited OR "absolute grounds"
```
Check: marks contrary to public policy, deceptive marks, marks without distinctive character, state emblems (Paris Convention Article 6ter).

**European Union (EUIPO)**
```
WebSearch: "[MARK]" EUIPO refused OR "absolute grounds" OR "public policy"
```
EUTM Regulation Article 7: marks devoid of distinctive character, descriptive marks, customary marks, shapes, public order/morality.

**India (Trade Marks Act 1999)**
```
WebSearch: "[MARK]" trademark India refused OR prohibited OR "Section 9" OR "Section 11"
```
Key grounds: Section 9 (absolute grounds — no distinctive character, descriptive, customary, deceptive, contrary to law, scandalous, religious sensitivity); Section 11 (relative grounds — conflict with earlier marks). India additionally restricts names that hurt religious sensibilities.

**Canada (CIPO)**
```
WebSearch: "[MARK]" Canada trademark refused OR "clearly descriptive" prohibited
```

**Australia (IP Australia)**
```
WebSearch: "[MARK]" Australia trademark refused OR "not inherently adapted" prohibited
```

### 10.3 Paris Convention Article 6ter

All Paris Convention member countries (180+) prohibit trademark registration of:
- State emblems, flags, and official signs of member countries
- Armorial bearings, flags of intergovernmental organizations (UN, WHO, NATO, etc.)

If the mark resembles any national flag, coat of arms, or intergovernmental organization symbol — flag it here.

```
WebSearch: "[MARK]" national symbol OR flag OR emblem resemblance
```

### 10.4 Step 10 Output

```
GOVERNMENT BANS & PROHIBITED TERMS
```

| Jurisdiction | Prohibition Category | Applies? | Details | Risk |
|---|---|---|---|---|
| All / Universal | National symbols | Yes / No | | 🔴 / ✅ |
| All / Universal | Olympic / Red Cross | Yes / No | | 🔴 / ✅ |
| US | Scandalous / deceptive (§2a) | Yes / No | | 🔴 / ✅ |
| US | Financial / banking terms | Yes / No | | 🔴 / ✅ |
| UK | Public policy / morality | Yes / No | | 🔴 / ✅ |
| EU | Absolute grounds (Art. 7) | Yes / No | | 🔴 / ✅ |
| India | Religious sensitivity (§9) | Yes / No | | 🔴 / ✅ |
| India | Contrary to law (§9) | Yes / No | | 🔴 / ✅ |
| [Other target jurisdictions] | | | | |

---

## FINAL OUTPUT — EXECUTIVE SUMMARY & RISK MATRIX

Generate this section first in the output (even though it is compiled last from all steps).

### EXECUTIVE SUMMARY

```
═══════════════════════════════════════════════════════
TRADEMARK CLEARANCE SCREENING REPORT
═══════════════════════════════════════════════════════
Mark:               [MARK]
Purpose:            [company / product / service / personal brand]
Industry:           [industry]
Nice Classes:       [list]
Target Markets:     [list]
Date:               [date]
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
OVERALL RISK RATING: 🔴 HIGH / 🟡 MODERATE / 🟢 LOW
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

KEY FINDINGS:
  ✦ [Most critical finding — 1 sentence]
  ✦ [Second finding]
  ✦ [Third finding]
  ✦ [Fourth finding if needed]

TOP 3 RISKS:
  1. [Highest risk item — mark, jurisdiction, why]
  2. [Second risk]
  3. [Third risk]

QUICK VERDICT:
  [2–3 sentences: can they proceed, what must they fix first, what
   needs attorney review before filing]
═══════════════════════════════════════════════════════
```

### FULL RISK MATRIX

| Check | Step | Finding | Risk Level | Action Required |
|---|---|---|---|---|
| Brand Distinctiveness | 1 | [classification] | 🔴 / 🟡 / 🟢 | |
| Meaning & Cultural | 2 | [summary] | | |
| Market Presence | 3 | [# conflicts found] | | |
| SEO / Misspellings | 4 | [summary] | | |
| .com Domain | 5 | Available / Taken | | |
| Other Domains | 5 | [# taken] | | |
| Social Handles | 6 | [# unavailable] | | |
| US Trademarks | 7 | [# conflicts] | | |
| EU Trademarks | 7 | [# conflicts] | | |
| UK Trademarks | 7 | [# conflicts] | | |
| India Trademarks | 7 | [# conflicts] | | |
| WIPO / Madrid | 7 | [# conflicts] | | |
| Likelihood of Confusion | 8 | [summary] | | |
| Company Name Registry | 9 | [summary] | | |
| Govt Bans / Prohibited | 10 | [any hits] | | |

### RECOMMENDED ACTIONS

Produce a numbered, prioritized action list:

```
IMMEDIATE (before adopting the name):
  1. [Most urgent action — e.g., "Engage attorney to clear [conflicting mark]"]
  2. [Second action]

SHORT-TERM (before filing a trademark application):
  3. [e.g., "Register [mark].com — currently available"]
  4. [e.g., "Claim @[mark] on X/Twitter and Instagram"]

BEFORE FILING:
  5. [e.g., "Commission a full TESS search for phonetic variants in Class 42"]
  6. [e.g., "Obtain formal FTO/clearance opinion from trademark counsel"]

DESIGN MARK NOTE:
  If you intend to file a logo or stylized mark in addition to the word mark,
  a separate visual/design trademark search is required using specialized tools
  (Corsearch, Thomson CompuMark, or attorney-conducted image search). This skill
  covers word marks only.
```

---

## EXECUTION RULES

Follow these rules throughout all steps:

1. **Complete every step for every run.** Do not skip a step because you expect it to return no results — the absence of results is itself a finding.

2. **Real data only.** Never invent trademark serial numbers, registration numbers, or company names. If a search returns no results, state "No results found for this query" — that is a valid finding.

3. **Multiple search queries per step.** Run all listed queries. A single query is not sufficient — trademark data is indexed inconsistently across sources.

4. **Flag early, not late.** If a critical conflict appears in Step 3 or 7, surface it immediately in a brief note before completing the full analysis. Do not bury findings in the final summary.

5. **Distinguish registered from pending from abandoned.** A pending application is not a registered mark — it creates a risk but not a certain block. An abandoned mark creates prior art but not an infringement risk. Be precise.

6. **Jurisdiction precision.** A US trademark does not block use in India. Be specific about which conflict applies in which jurisdiction.

7. **Nice class precision.** A trademark in Class 9 (software) does not automatically block a filing in Class 35 (business services). Assess class overlap carefully.

8. **Honest about coverage gaps.** At the end of Step 7, note: "This search is based on publicly indexed web data. Official database access (USPTO TSDR, EUIPO eSearch, WIPO Brand DB, IP India) requires direct database tools or professional search. Engage a trademark attorney for exhaustive clearance."

9. **Lean toward caution.** When in doubt between Low Risk and Watch — choose Watch. When in doubt between Watch and High Risk — choose High Risk. Overclaiming safety is worse than overclaiming risk.

10. **Always end with the attorney referral.** No screening report replaces professional counsel. Make this explicit in every report.

---

## RISK RATING DEFINITIONS

| Rating | Criteria |
|---|---|
| 🔴 **HIGH RISK** | Active registered trademark in same class in a key target jurisdiction; likelihood of confusion is high; government prohibition applies; name is generic/not registrable |
| 🟡 **MODERATE RISK** | Pending application in same class; active mark in adjacent class or non-target jurisdiction; phonetic/visual conflict exists; domain or social handle taken by a competitor |
| 🟢 **LOW RISK** | No material conflicts found in target jurisdictions and classes; minor watch items noted; name appears available and distinctive |

**Overall risk = the highest risk level found across any single step.**

---

## LEGAL DISCLAIMER

> This trademark clearance screening is prepared for preliminary internal planning purposes only and **does not constitute legal advice**. It is not a formal trademark clearance opinion or freedom-to-operate assessment. Search results are based on publicly indexed web data and may not capture all registered marks, pending applications, common law rights, or design marks. Trademark rights, legal status, registration details, and Nice class coverage must be verified by a qualified trademark attorney using official database access before any name adoption, trademark filing, or commercialization decision. This document does not create an attorney-client relationship. **Engage a qualified trademark attorney before adopting or filing the mark.**

---

*Built by [abhikuchbhi.in](https://abhikuchbhi.in)*
