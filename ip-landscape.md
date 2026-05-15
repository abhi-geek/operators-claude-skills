# IP Landscape Skill

> **How to install:** Drop this file into `~/.claude/commands/ip-landscape.md` (global — works in any project) or `.claude/commands/ip-landscape.md` (project-level). Then invoke with `/ip-landscape`.
>
> **Author:** [abhikuchbhi.in](https://abhikuchbhi.in)

---

You are executing a **professional-grade IP Landscape Analysis** — the same quality of work produced by specialist IP law firms (e.g., Clairvolex, Clarivate, Dennemeyer). This is a complete, multi-phase workflow. Follow every step in sequence. Do not skip steps. Generate all output files as specified. Use all listed sources.

$ARGUMENTS

---

## PHASE 0 — STARTUP INTERVIEW

Ask the user all of the following in a single message before doing any work. Wait for all answers before proceeding.

1. **Organization / Company name** — for report headers and IP naming prefix
2. **Product / technology name** — the core technology being analyzed (e.g., "AcmeDB", "NanoSense", "VectorEngine")
3. **Technology description** — 3-5 sentences: what it does, what problem it solves, what makes it novel
4. **Home jurisdiction** — country where the company is registered (affects filing strategy, official fees, rebates, compliance rules)
5. **Company profile** — choose one: Startup/MSME (<500 employees), Large Enterprise (>500), University/Research Institute, Individual Inventor
6. **IP input format** — which do you have?
   - (a) A specification/tech document I can analyze
   - (b) An Excel/CSV/text list of inventions or features
   - (c) A raw description of what the product does
   - (d) Multiple of the above — tell me which files
7. **Target filing jurisdictions** — which markets matter most for IP protection? (e.g., India, US, EU/EP, China, Japan, South Korea — pick the ones that apply)
8. **IP naming prefix** — 3-4 letter code for IP item IDs (e.g., NOVA for NovaTech, ACME for Acme Corp, XYZ for your company)
9. **Competitor names** — list 3-7 known competitors or adjacent players in this technology space
10. **Key product milestones** — when does public disclosure / product launch / first beta / shipping happen? (This determines urgency of provisional filings)
11. **Approximate annual IP budget** — USD, or "unknown" — used only for scenario planning

**IMPORTANT:** Store all answers in memory for this session. Reference them throughout all steps.

---

## PHASE 0.5 — OUTPUT DIRECTORY SETUP

Before starting Step 1, create the following directory structure. Use the product name, lowercased and hyphenated, as the root folder name.

```
[product-name]-ip-landscape/
├── DOSSIER.md                         ← master executive entry point (created last)
├── _report/
│   └── IP_Landscape_Report.md         ← Clairvolex-style shareable report (created last)
├── _meta/
│   ├── step1_ip_classification.md     ← created in Step 1
│   ├── step2_prior_art_summary.md     ← created in Step 2
│   ├── step3_taxonomy.md              ← created in Step 3
│   ├── step4_bibliographic_insights.md ← created in Step 4
│   ├── step5_technology_insights.md   ← created in Step 5
│   ├── step6_fto_summary.md           ← created in Step 6
│   ├── step7_filing_strategy.md       ← created in Step 7
│   ├── cost_model.md                  ← created in Step 7
│   ├── action_list.md                 ← created last
│   └── search_log.md                  ← maintained throughout (log every search)
├── utility-patent/                    ← one .md file per utility patent candidate
├── trade-secret/                      ← one .md file per trade secret
├── copyright/                         ← one .md file per copyright work
├── defensive-publication/             ← one .md file per defensive pub
├── trademark/                         ← one .md file per trademark
├── design-registration/               ← one .md file per design
└── know-how/                          ← one .md file per know-how item
```

Create `search_log.md` immediately with header row: `| Timestamp | Step | Database | Query | Results | Key Finds |`

---

## STEP 1 — IP IDENTIFICATION & CLASSIFICATION

### 1.1 Technology Domain Research

Before processing the IP list, build foundational domain knowledge. This makes classification accurate and prior art searches precise.

**Execute all of the following:**

1. **Google Scholar** — search for 3-5 recent survey/review papers in this domain. Fetch abstracts. Identify: key technical sub-areas, standard approaches, landmark papers.

2. **arXiv** — search for recent preprints (last 3 years) using domain keywords. Especially relevant for CS, EE, life sciences, AI/ML, and materials science.

3. **Lens.org** — keyword search to find the 5-10 most-cited patents in this domain. Note their CPC classes — these classes will anchor your systematic search in Step 2.

4. **Standards bodies** — based on the technology, check relevant standards organizations:
   | Technology Area | Standards to Check |
   |---|---|
   | Semiconductors / Chips | JEDEC (jedec.org), PCIe (pcisig.com), IEEE 802 series |
   | Networking / Protocol | IETF RFCs (rfc-editor.org), IEEE (ieeexplore.ieee.org) |
   | Wireless / Telecom | ETSI (etsi.org), 3GPP (3gpp.org), ITU (itu.int) |
   | Software / Web | W3C (w3.org), IETF |
   | Medical Devices | FDA 510(k) database, ISO 13485 |
   | Automotive | SAE International, AUTOSAR |
   | AI / ML | No formal standards, but check MLCommons, MLPerf |

5. **GitHub** — search for open-source implementations of similar technology. Note: OSS code can be prior art and may create freedom-to-operate obligations depending on license (GPL, LGPL, Apache, MIT, BSD).

6. **Competitor websites** — web-fetch each competitor listed in startup interview. Read product pages, technical white papers, patents pages, press releases.

**Output in `_meta/step1_ip_classification.md` Section 1 — Domain Overview:**
- 1-2 paragraph domain summary
- Key technical sub-areas (this becomes the basis for taxonomy in Step 3)
- Known players and their focus areas
- Relevant CPC/IPC class candidates (will be refined in Step 2)
- OSS dependency notes

---

### 1.2 IP Intake & Processing

Process the user's IP list using the format they provided:

**If spec/tech document:** Systematically read every section. For each functional block, feature, mechanism, or method described, ask:
- Is this a novel mechanism not found in standard domain knowledge?
- Is the combination of elements non-obvious?
- Does it solve a specific technical problem in a new way?
- Is it better/different enough from existing approaches to warrant a patent?
Extract every "yes" answer as a candidate IP item.

**If Excel/CSV:** Each row = one IP candidate. Read all rows.

**If text description:** Extract each distinct inventable concept as a separate item.

**If multiple sources:** Process all, deduplicate, merge related items.

**Assign each IP item a unique ID:** `[PREFIX]-[3-digit-number]` using the prefix from startup interview.
Example: XYZ-001, XYZ-042, XYZ-107 — where XYZ is your chosen prefix.

---

### 1.3 IP Classification

Classify every IP item into one of these 10 categories. Apply the criteria strictly.

| Category | When to Use | Example |
|---|---|---|
| **Utility Patent** | Novel, non-obvious process/machine/composition/improvement. Has claims potential. Provides at least 20-year exclusivity. | A new routing algorithm; a novel data compression method; an improved ML training technique |
| **Trade Secret** | Valuable confidential information. Not suitable for public disclosure. Protection lasts as long as secret is maintained. | Proprietary training datasets, internal calibration recipes, manufacturing process parameters |
| **Copyright** | Original expression: source code, firmware, design files, documentation, databases, test suites. Automatic — exists on creation. | Source code, firmware, technical documentation, training datasets, CAD files |
| **Defensive Publication** | Novel but not worth patenting (too narrow, too implementation-specific, or prior art too close). Publish to block competitors from patenting it. | A specific optimization not worth full prosecution; a method disclosed to establish prior art |
| **Trademark** | Brand name, product name, logo, tagline, distinctive trade dress. | Product name, product line name, company logo, distinctive UI elements |
| **Design Registration** | Ornamental or aesthetic design of a product. Non-functional. | Product enclosure shape, UI visual design, product industrial design |
| **Know-How** | Tacit organizational knowledge, process expertise, embedded skills. Cannot be formalized but has value. | Team expertise in specific workflows, undocumented process tricks, calibration know-how |
| **Controlled Disclosure** | Planned public disclosures (blog posts, conference talks, demos, open-source releases, white papers) timed to establish prior art before competitor filings. Risky — get counsel advice on timing. | A carefully timed technical blog post disclosing a concept before filing; conference demo; targeted open-source component release |

**For every utility patent candidate, also assign:**

**Technology Cluster** — group by functional area relevant to your product domain (e.g., Core Algorithm, Data Processing, User Interface, Security & Privacy, Networking, Developer Tools, Platform Integration, etc.)

**Priority Tier:**
| Tier | Meaning | When to File |
|---|---|---|
| P0★ | URGENT — active competitor race in this exact space | Immediately (M0) |
| P0 | High value, clear FTO, file before product disclosure | M0–M3 |
| P1 | Important, somewhat crowded space, file before product launch | M3–M12 |
| P2 | Valuable but not urgent, no immediate competitive threat | M12–M24 |
| P3 | Strategic reserve — file if resources allow | M24+ or Defensive Pub |

**Filing Flag:** File Patent / Defensive Publication / Trade Secret / Hold (pending FTO opinion)

**Section 35 / Dual-Use Flag (applies to technology with defense/national security implications):**
Flag items that involve: encryption, dual-use technology, defense-applicable systems, secure communications, satellite/aerospace, nuclear/radiological, or advanced materials. These may require export control review before foreign filing (SCOMET in India, EAR in US, EU Dual-Use Regulation in Europe).

---

### 1.4 Individual IP Files

Create one `.md` file per IP item in the appropriate category directory.

**Filename format:** `[ID]-[kebab-case-title].md` (e.g., `XYZ-001-adaptive-routing-algorithm.md`)

**File template:**

```markdown
---
id: [ID]
title: [Short descriptive title, max 60 chars]
category: utility-patent | trade-secret | copyright | defensive-publication | trademark | design-registration | know-how | controlled-disclosure
priority: P0★ | P0 | P1 | P2 | P3
filing_flag: file-patent | defensive-pub | trade-secret | hold
technology_cluster: [cluster name]
section35_flag: true | false
oss_gate: [OSS library name if applicable, else none]
---

## Description
[2-3 sentences describing the invention/IP in plain English. What does it do?]

## Technical Problem Solved
[What specific problem does this solve? Why does this matter?]

## Novel Element
[What makes this novel vs. prior art? What is the key inventive step?]

## Claims Summary (Utility Patents Only)
[Draft 1-2 independent claim concepts: "A method of X comprising: step A, step B, wherein C..."]

## Step 2: Prior Art Search
[Filled in Step 2]

## Step 3: Taxonomy Placement
[Filled in Step 3]

## Step 4: Competitive Landscape Position
[Filled in Step 4]

## Step 5: Technology Insights
[Filled in Step 5]

## Step 6: FTO Analysis
[Filled in Step 6]

## Step 7: Filing Strategy & Cost
[Filled in Step 7]
```

---

### 1.5 Step 1 Summary Output

Write `_meta/step1_ip_classification.md` with:

1. **Domain Overview** (from 1.1)
2. **Portfolio Summary Table:**
   | Category | Count | Key Items |
   |---|---|---|
3. **Priority Tier Breakdown:**
   | Tier | Count | Items |
   |---|---|---|
4. **Technology Cluster Map** — which clusters have the most IP?
5. **OSS Dependency Register** — any OSS components used + their licenses
6. **Section 35 / Dual-Use Flagged Items** — list with reason
7. **Classification Rationale Notes** — any borderline cases and how they were decided

**Report to user:** "Step 1 complete. Identified [N] IP items across [X] categories. [Y] utility patent candidates. [Z] P0★/P0 priority items. Proceeding to Step 2."

---

## STEP 2 — PRIOR ART SEARCH

Prior art search determines what exists in the field. It is the foundation for FTO analysis, claim scope, and filing strategy. Be thorough — missed prior art discovered post-filing is expensive.

### 2.1 Search Strategy Per Utility Patent

For each utility patent candidate, define a search strategy before executing:
- **Keyword Set 1**: Primary technical terms (exact terminology)
- **Keyword Set 2**: Synonyms and equivalent terms
- **Keyword Set 3**: Application/problem-space terms (what it does, not how)
- **CPC/IPC Classes**: Identify 2-4 relevant classifications using Google Patents CPC browser or Espacenet's classification search
- **Key Assignees**: Competitors + any others identified in domain research

Document all search strategies in `search_log.md`.

---

### 2.2 Primary Patent Databases — MUST SEARCH ALL

#### TIER 1 — Comprehensive Coverage (search every IP item)

| Database | URL | How to Use | Strength |
|---|---|---|---|
| **Google Patents** | patents.google.com | Full-text keyword + CPC + assignee + date filter. Use Advanced Search. Try multiple query formulations. | Best full-text search; widest coverage; real-time |
| **Espacenet** | worldwide.espacenet.com | CPC classification search + keyword. Use "Smart search". Excellent for family data and legal status. | Best for EP/WO; CPC tree browser; family view |
| **WIPO PatentScope** | patentscope.wipo.int | PCT application search + CLIR (cross-lingual search finds prior art in other languages). Search by IPC. | Best for PCT applications; multilingual |
| **Lens.org** | lens.org | Combined patent + scholarly. Citation network. FOSS patent searching. Free analytics. | Best for citation analysis; academic + patent combined |
| **USPTO Full-Text** | ppubs.uspto.gov | US patent full-text search (pre-1976 images only). Supplement with Google Patents. | Definitive for US |

#### TIER 2 — Jurisdiction-Specific (search based on technology domain relevance)

| Database | URL | When to Use |
|---|---|---|
| **India IPO InPASS** | iprsearch.ipindia.gov.in | Always if filing in India; Indian applicants; competitors operating in India |
| **J-PlatPat** (Japan) | j-platpat.inpit.go.jp | Consumer electronics, robotics, automotive, materials, optics — Japan is major filer |
| **CNIPA** (China) | pss-system.cponline.cnipa.gov.cn | Any technology domain — China files heavily in almost every tech area post-2015 |
| **KIPRIS** (Korea) | engdoc.kipris.or.kr | Semiconductors, displays, memory, consumer electronics, EV batteries |
| **DEPATISnet** (Germany) | depatisnet.dpma.de | Automotive, industrial machinery, chemicals, mechanical engineering |
| **FreePatentsOnline** | freepatentsonline.com | Quick claim comparison; US/EP/WO; good for independent claim text |
| **ETSI IPR Database** | ipr.etsi.org | Telecom standards (3G/4G/5G/Wi-Fi) — Standard Essential Patents (SEPs) |
| **IEEE IPR Database** | standards.ieee.org/ipr | IEEE standard SEPs (802.11, 802.3, etc.) |

#### TIER 3 — Non-Patent Literature (NPL)

Non-patent literature counts as prior art and can invalidate patent claims if predates the priority date.

| Source | URL | Search Strategy |
|---|---|---|
| **Google Scholar** | scholar.google.com | Keyword search + date range. Download key papers. Note publication dates carefully. |
| **arXiv** | arxiv.org | Use relevant subject areas (cs.*, eess.*, q-bio.*, stat.*, cond-mat.* etc.) for your technology domain. Preprints often predate patents. |
| **Semantic Scholar** | semanticscholar.org | Citation-aware search. Good for finding influential papers. |
| **IEEE Xplore** | ieeexplore.ieee.org | Conference papers across all IEEE domains. Abstracts free. Search by keywords and conference name. |
| **ACM Digital Library** | dl.acm.org | CS/software papers. Partial free access. |
| **IETF RFC Archive** | rfc-editor.org | Protocol/networking prior art. RFC = definitive prior art for internet protocols. |
| **W3C Technical Reports** | w3.org/TR | Web standards. Definitive prior art for web/browser technology. |
| **GitHub** | github.com | Search code + commit history. OSS code + README = prior art from commit date. |
| **Product documentation** | Various | Product manuals, data sheets, white papers — if publicly available, they are prior art. |

---

### 2.3 Search Execution Protocol

For **each utility patent candidate**, execute in this sequence:

1. **Google Patents keyword search** — use Keyword Set 1, then Set 2. Apply CPC filter. Record top 10 results.
2. **Google Patents CPC search** — search by CPC class alone, sorted by relevance. Look for patterns in top results.
3. **Google Patents assignee search** — search competitor names as assignees, filtered to relevant CPC classes.
4. **Espacenet CPC search** — cross-check against Espacenet's classification. Often surfaces EP/WO patents missed by Google.
5. **WIPO PatentScope** — search for PCT applications, especially recent ones (last 3 years).
6. **Lens.org** — search + check citation network of any blocking hits.
7. **Google Scholar + arXiv** — NPL search for the specific technical concept.
8. **Japan/China/Korea** (if technology relevant) — search CNIPA/J-PlatPat/KIPRIS.

**For each significant hit (High or Medium relevance), record:**
- Patent number / Publication number
- Title
- Primary assignee (current owner if possible)
- Priority date (not filing or publication date)
- CPC/IPC classes
- Jurisdiction(s) filed
- Legal status: Granted / Pending / Expired / Abandoned
- Relevance: High (reads directly on our concept) / Medium (related approach) / Low (background)
- Why relevant: what does it teach that's close to our IP?

Log every search in `search_log.md`.

---

### 2.4 Supplementary Searches

After completing per-item searches:

**A. Competitor Portfolio Sweep**
For each competitor in the startup interview list:
1. Google Patents assignee search: `assignee:[Competitor Name]` + relevant CPC class
2. Count their total portfolio size in this domain
3. Identify their 5-10 strongest/most-cited patents
4. Note which technology sub-areas they are most active in

**B. Key Inventor Sweep**
For the top 3-5 inventors found across competitor searches:
1. Search their complete portfolio on Google Patents: `inventor:[Name] assignee:[Company]`
2. Identify if they have individual patents (signals independent R&D activity)

**C. Citation Chain Analysis**
For any Blocking or Conflict-Narrow patents found:
1. On Lens.org or Espacenet: fetch forward citations (who has cited this patent)
2. Fetch backward citations (what prior art this patent builds on)
3. This reveals: (a) patent families derived from the blocking art; (b) prior art that could invalidate the blocking patent

**D. Standard Essential Patent Check**
If the technology implements or is adjacent to any standard:
1. Check ETSI IPR database for 3GPP/ETSI standards
2. Check IEEE IPR database for IEEE standards
3. Check WIPO/OIN for declared SEPs in the relevant standard
4. Note: SEPs must be licensed on FRAND (Fair, Reasonable, And Non-Discriminatory) terms

**E. Defensive Pool Check**
Search these pools — membership or patent donations affect FTO:
| Pool | URL | Covers |
|---|---|---|
| Open Invention Network (OIN) | openinventionnetwork.com | Linux-adjacent software |
| LOT Network | lotnet.com | Broad cross-licensing for members |
| Unified Patents | unifiedpatents.com | Sector-specific challenges to NPE patents |
| FRAND declaration databases | ETSI, IEEE | Standard-essential patent licensing |

---

### 2.5 Prior Art Documentation Per IP Item

Update each individual IP file's `## Step 2: Prior Art Search` section:

```markdown
## Step 2: Prior Art Search

### Search Queries Used
| Database | Query | Results Count |
|---|---|---|
| Google Patents | [query] | [N] |
| Espacenet CPC | [CPC class] + [keyword] | [N] |
| WIPO | [query] | [N] |
| Google Scholar | [query] | [N] |

### Key Prior Art Found
| ID | Title | Assignee | Priority Date | Jurisdiction | Legal Status | Relevance | Notes |
|---|---|---|---|---|---|---|---|
| USxxxxxxx | ... | ... | YYYY-MM-DD | US | Active | High | Teaches [X]; differs because [Y] |

### Preliminary FTO Signal
- **Closest Reference**: [patent ID and why]
- **Distinguishing Features of Our IP**: [what makes ours distinct]
- **Initial FTO Signal**: Clear / Watch / Conflict-Narrow / Blocking
- **Counsel Review Needed?**: Yes / No / Maybe
```

---

### 2.6 Step 2 Summary Output

Write `_meta/step2_prior_art_summary.md`:

1. **Search Coverage Table** — how many databases searched per IP item
2. **Blocking Patents Registry** — all patents rated Blocking or Conflict-Narrow, with full details
3. **Top 10 Competitor Patent Portfolios** — assignee, count in domain, sub-areas
4. **Key Inventors Map** — top inventors found, their affiliation
5. **Expiring Patents of Interest** — any relevant patents expiring in 1-5 years (creates freedom)
6. **FTO Signal Distribution:**
   | Signal | Count | Items |
   |---|---|---|
   | Clear | | |
   | Watch | | |
   | Conflict-Narrow | | |
   | Blocking | | |
7. **Gaps in Search Coverage** — any areas where results were sparse (note for manual follow-up)

**PAUSE:** If any Blocking patents were found, present them to the user before proceeding. Explain what they block and what the options are (design-around, narrow claims, IPR challenge, license, hold). Get user acknowledgment before proceeding.

**Report to user:** "Step 2 complete. Searched [N] databases for [M] utility patent items. Found [X] blocking references, [Y] conflict-narrow, [Z] watch, [W] clear. Proceeding to Step 3."

---

## STEP 3 — PATENT DATA SEGMENTATION & TAXONOMY

Taxonomy is the analytical backbone of a professional patent landscape. It converts a mass of patents into a structured map of the technology space.

### 3.1 Build Technology Taxonomy

Using: (a) your IP items, (b) the prior art corpus from Step 2, (c) domain knowledge from Step 1.

Construct a 3-level taxonomy:

- **Level 1 (Domains)**: 4-8 broad technology areas. Should cover the entire technology space, not just your IP. Examples for a software platform: Data Ingestion, Processing Engine, User Interface, Security, Integration & APIs, Developer Tools.
- **Level 2 (Sub-domains)**: 3-6 sub-areas per Level 1 domain. Examples under Processing Engine: Query Optimization, Scheduling, Caching, Fault Tolerance.
- **Level 3 (Concepts)**: Specific technical mechanisms at the leaf level. Examples under Query Optimization: cost-based planning, adaptive execution, predicate pushdown, vectorized evaluation.

Present the taxonomy as a structured markdown tree.

**Taxonomy mapping:** For every IP item (yours) AND every significant prior art patent (High/Medium relevance from Step 2), assign it to 1-3 taxonomy nodes. Record mapping in a table.

### 3.2 Assignee × Taxonomy Matrix

Build a matrix:
- Rows: Technology sub-areas (Level 2 nodes)
- Columns: Top 8-10 assignees (by patent count in this domain)
- Cell value: Number of patents this assignee has in this sub-area

This reveals:
- Where competitors are concentrated (threat clusters)
- Which sub-areas are contested by multiple players
- Which sub-areas are dominated by a single player

### 3.3 Whitespace Analysis

For each taxonomy node (especially Level 2 and Level 3), assess:

| Factor | How to measure |
|---|---|
| **Patent density** | Count of active patents in this node |
| **Recency** | % of patents filed in last 3 years (momentum) |
| **Legal status** | % active vs expired |
| **Your coverage** | Do you have IP in this node? |
| **Whitespace score** | Low density + few active patents + no blocking assignee = HIGH opportunity |

**Whitespace rating:**
- **Crowded**: >10 active patents, multiple assignees, recent filings
- **Contested**: 5-10 active patents, 1-2 dominant assignees
- **Emerging**: <5 patents, recent filings (watch closely)
- **Whitespace**: 0-2 active patents in this specific area
- **Expired/Free**: Patents exist but mostly expired — freedom is available

### 3.4 Step 3 Summary Output

Write `_meta/step3_taxonomy.md`:

1. **Full Taxonomy Tree** (markdown tree format)
2. **Patent-to-Taxonomy Mapping Table** (all IP items + key prior art)
3. **Assignee × Taxonomy Matrix**
4. **Whitespace Heatmap** — taxonomy table with whitespace rating per node
5. **Top 10 Whitespace Opportunities** — specific sub-areas where filing first gives strong position
6. **Top 5 Crowded Areas to Avoid** — where filing costs more for less coverage
7. **Expiring Opportunities** — taxonomy nodes where key patents expire within 3 years

**Report to user:** "Step 3 complete. Taxonomy has [L1] Level-1 domains, [L2] sub-areas, [L3] concept nodes. Identified [X] whitespace opportunities, [Y] crowded areas. Top whitespace: [list top 3]. Proceeding to Step 4."

---

## STEP 4 — BIBLIOGRAPHIC INSIGHTS

Professional-grade analysis of the patent corpus. This section produces the data behind the charts in a Clairvolex-style landscape report.

### 4.1 Priority vs. Filing Year Trend

From the prior art corpus (all High + Medium relevance patents):
- Count patents by priority year (not filing or publication year — priority year shows true innovation timeline)
- Note the filing year too (publication lag is typically 18 months)
- Identify: When did filings start? When was peak? Is the trend growing, plateauing, or declining?
- What % of filings are from the last 5 years?

Present as a year-by-year table with narrative interpretation.

### 4.2 Top IP Owners

- List top 15 assignees by patent family count in this domain
- For each: count, assignee type (Company / University / Individual / Joint), primary technology focus
- Overall breakdown: what % is Company / University / Individual / Joint?
- Identify if any are Non-Practicing Entities (NPEs/patent trolls)
- Note geographic concentration of top filers

### 4.3 Emerging Players (Last 2-3 Years)

- Organizations that first filed in this domain in the last 2-3 years
- For each: organization name, country, number of filings, technology focus
- Why does this matter: signals where new competition is entering

### 4.4 Technology Collaboration (Company + University)

- Identify joint patents where a company AND a university are co-assignees
- List: company name, university name, patent number, focus area
- This reveals: which universities are doing practical R&D in this field + which companies fund it

### 4.5 Technology Innovation Country

- Count patent families by priority country (where the IP was first filed — signals origin of innovation)
- Top 10 innovation countries with patent family counts
- Note: which countries' companies are most active in your target sub-areas?

### 4.6 Jurisdiction Spread

- Count filings by publication/grant country (where protection was sought)
- Preferred jurisdictions (most filings): signals where the market value is considered highest
- Emerging jurisdictions (started filing in last 5-10 years): signals expanding market interest

### 4.7 Legal Status Analysis

For the full corpus:
- **Granted patents**: Active grants (have full protection)
- **Pending published applications**: Filed, not yet granted (potential future protection)
- **Expired/Lapsed**: Protection lapsed (free to use — verify each case)
- **Alive families**: Patent family has at least one active member
- **Dead families**: All members expired or abandoned

Implication: patents in the corpus that are expired are prior art but not an infringement risk.

### 4.8 Top CPC/IPC Classifications

- List top 15-20 CPC classes across the corpus
- For each: class code, human-readable description, count of patents
- Identify: which CPC classes are growing (high recent filing count)?
- Which classes does your IP predominantly fall under?

**CPC reference:** Use EPO's CPC website (cooperativepatentclassification.org) to look up class definitions if needed.

### 4.9 Key Inventor Analysis

- Top 15 inventors by patent family count in this domain
- For each: name, affiliation (current), number of families, technology focus
- Are any prolific inventors independent (not tied to a single company)?
- Have any key inventors recently moved employers? (signals technology transfer)

### 4.10 Step 4 Summary Output

Write `_meta/step4_bibliographic_insights.md` with all 9 sections above. Each section should include:
- A data table
- 3-5 bullet points of key takeaways / strategic interpretation
- Any alerts (e.g., a competitor suddenly accelerating filings = competitive threat)

**Report to user:** "Step 4 complete. Analyzed [N] patent families. Top assignee: [name]. Peak filing year: [year]. [X]% filings from last 5 years. Proceeding to Step 5."

---

## STEP 5 — TECHNOLOGY INSIGHTS & WHITESPACE

This goes deeper than Step 4's bibliographic data — it analyzes the technical content and identifies strategic opportunities.

### 5.1 Technology Focus Mapping

For each taxonomy Level 1 domain:
- Total patent family count
- Top 3 assignees in this area
- % of filings from last 5 years (momentum indicator)
- Is this area growing, stable, or maturing?
- What are the key technical innovations appearing in recent filings?

### 5.2 Sub-Technology Breakdown

For each taxonomy Level 2 node:
- Patent family count
- Top assignees + their count
- Innovation intensity: **High** (>10 active patents, recent filings) / **Medium** (5-10, mixed activity) / **Low** (1-4, aging) / **Whitespace** (0-1)
- Most-cited patents in this node (the "blocking art" to be aware of)

### 5.3 Application Areas (if applicable)

If the technology has multiple application domains (e.g., a computer vision system could apply to: autonomous vehicles, industrial inspection, medical imaging, retail analytics):
- Map patents to application areas
- Count patent families per application area
- Identify which applications are most contested vs. underexplored

### 5.4 Correlation Analysis (Key Insights)

Produce observations on key pairings:

1. **Technology Focus × Assignee Type**: Are companies vs. universities filing in different sub-areas?
2. **Technology Focus × Country**: Which countries dominate which sub-areas?
3. **Sub-technology × Legal Status**: Which areas have mostly active vs. expired patents?
4. **Sub-technology × Filing Year**: Which areas are growing vs. declining?
5. **Your IP × Competitive Density**: For each of your utility patents, how dense is the competitive landscape in that exact taxonomy node?

### 5.5 Competitive Position of Your IP Portfolio

For each utility patent candidate in your portfolio:
| IP ID | Taxonomy Node | Competitive Density | Position | Key Differentiator | FTO Signal |
|---|---|---|---|---|---|
| [ID] | [Level2/Level3] | Low/Med/High | Leader/Follower/Fast-follower/Whitespace | [1 sentence] | Clear/Watch/Conflict-Narrow/Blocking |

Position definitions:
- **Leader**: You are first or strongest in this specific taxonomy node — file immediately, broad claims
- **Follower**: Established area, competitors have broad patents — file narrow/dependent claims, design around
- **Fast-follower**: Active, growing area — file now with differentiated angle before it crowds further
- **Whitespace**: No significant competition in this specific node — opportunity for broad independent claims

### 5.6 Strategic Observations (Executive Level)

Synthesize 8-12 key strategic insights from the full analysis. Each should be actionable:

Format each insight as:
> **[INSIGHT TITLE]**: [2-3 sentence observation with data backing]. **Strategic implication**: [what should the IP owner do?]

Categories of insights to cover:
- Whitespace opportunities (file here to establish position)
- Crowded areas (focus on narrow/dependent claims)
- Expiring patents creating freedom (note when)
- Competitor acceleration signals (be aware)
- Technology gaps in competitor portfolios (potential licensing leverage)
- Cross-domain opportunities (your IP applies to market X where competition is sparse)
- Defensive publication candidates (publish before competitor filings)
- Licensing/cross-licensing opportunities

### 5.7 Step 5 Summary Output

Write `_meta/step5_technology_insights.md` with all 6 sections. Include:
- Technology landscape summary (paragraph)
- Sub-technology breakdown table
- Correlation analysis observations
- Your IP competitive position table
- Strategic observations list (numbered, actionable)
- **Priority Recommendations Table:**
  | Recommendation | Action | Priority | Rationale |
  |---|---|---|---|

**Report to user:** "Step 5 complete. Identified [X] whitespace opportunities, [Y] areas where you have leadership position, [Z] crowded areas to navigate carefully. Top strategic recommendation: [brief summary]. Proceeding to Step 6."

---

## STEP 6 — FREEDOM-TO-OPERATE (FTO) ANALYSIS

FTO analysis answers: "Can we commercialize this product/technology without infringing active third-party patents?"

**IMPORTANT DISCLAIMER — include this at the top of all FTO outputs:**

> This is a **preliminary FTO assessment** based on free public databases. It does not constitute a legal opinion and is not a substitute for a formal FTO opinion from qualified patent counsel. The analysis may not capture all relevant patents, particularly those in languages other than English or in less-indexed jurisdictions. Engage a patent attorney for any Blocking or Conflict-Narrow items before commercialization.

### 6.1 FTO Scope Definition

Before running FTO, define the **product/technology claim space**: what exactly is being commercialized? List the key technical features of the product in claim-like language. This is what you are checking FTO against.

### 6.2 For Each Utility Patent Candidate — Claim Mapping

For the 2-3 highest-relevance prior art patents per item (especially those rated Watch or above):

1. **Fetch the independent claims** — use Google Patents or Espacenet full text. Independent claims are those not referencing another claim number ("A method of X comprising...").

2. **Element-by-element mapping:**
   - List each element of the independent claim
   - For each element: Does your product practice this element? (Yes / No / Partially / Design-around possible)
   - If ALL elements of a claim are practiced → infringement risk
   - If ANY element is NOT practiced → no infringement of that claim (but check dependent claims for narrower version you do practice)

3. **Verify legal status:**
   | Action | Source |
   |---|---|
   | US patent active? | USPTO Patent Center: patentcenter.uspto.gov → "Patent" tab → status |
   | EP patent active? | EPO Register: register.epo.org → enter EP number → Legal Status |
   | WO/PCT active? | WIPO PatentScope → national phase entries + status |
   | Patent family global status | Lens.org → patent view → families tab |
   | Expiry calculation | Priority date + 20 years = maximum term (check for maintenance fee gaps) |

4. **Note jurisdiction-specific status** — a patent expired in the US may still be active in Europe. Check all jurisdictions where you plan to sell/manufacture.

### 6.3 FTO Risk Ratings

Apply these ratings consistently:

| Rating | Criteria | Required Action |
|---|---|---|
| **Clear** | No active patents with claims reading on our implementation in relevant jurisdictions | File with broad claims; proceed |
| **Watch** | Active patents exist; claims are narrow or differ on key elements; risk is manageable | File with claims designed to avoid; monitor for new filings in area |
| **Conflict-Narrow** | Active broad claims with partial overlap; our implementation practices some but not all elements; design-around is possible | Narrow claims to avoid overlap; consult counsel; consider continuation strategy |
| **Blocking** | Active patent with independent claims that clearly read on our implementation; all elements present | HOLD — do not file broad claims; consult counsel immediately; options: design-around, IPR/PGR challenge, license negotiation |

### 6.4 Assignee Risk Landscape

Assess each major assignee in the prior art corpus:
- **Risk level**: High (active enforcement history, NPE/troll) / Medium (large corp, tends to cross-license) / Low (university, often licenses readily; startup; inactive)
- **Enforcement history**: Have they sued in this domain? (search "[Company name] patent lawsuit" + technology domain)
- **Cross-licensing possibilities**: Is this a company you could approach for cross-license?
- **Defensive pool membership**: Are they in OIN or LOT Network? (reduces risk)

### 6.5 Design-Around Analysis

For every Conflict-Narrow or Blocking item:
- **Describe 1-2 concrete design-around options** — alternative implementations that avoid the problematic claim elements
- **Assess viability**: Is the design-around technically feasible? Does it degrade performance? Is it worth the engineering cost?
- **Continuation strategy**: File narrow/dependent claims first; retain broad claims for continuation after FTO is resolved

### 6.6 FTO Summary Table

| IP ID | Title | Closest Blocking Reference | Reference Status | Reference Expiry | Our FTO Risk | Recommended Action |
|---|---|---|---|---|---|---|

### 6.7 Step 6 Summary Output

Write `_meta/step6_fto_summary.md` with:
1. Disclaimer (always)
2. FTO scope definition
3. Risk distribution summary table
4. Blocking patents registry (full details for each)
5. Assignee risk landscape
6. Design-around options for flagged items
7. Defensive pool memberships (OIN, LOT, Unified) — recommended to join
8. Items requiring paid-DB verification (Derwent Innovation, PatSnap, Questel Orbit — mention these as next steps for counsel)

**PAUSE:** For every Blocking-rated item, present to user: the blocking patent, the specific claim element that reads on the technology, the design-around options, and the counsel referral. Get user acknowledgment before moving to Step 7.

**Report to user:** "Step 6 complete. FTO summary: [X] Clear, [Y] Watch, [Z] Conflict-Narrow, [W] Blocking. [W] items require counsel review before filing. Proceeding to Step 7."

---

## STEP 7 — FILING STRATEGY & COST MODEL

### 7.1 Filing Disposition (All IP Items)

Confirm final filing disposition for every IP item based on Steps 1-6:

| Disposition | Description |
|---|---|
| **File Patent — Broad Claims** | Clear FTO, whitespace or leader position — file with broad independent claims |
| **File Patent — Narrow Claims** | Watch/Conflict-Narrow FTO — file with narrowed claims designed to avoid conflict |
| **File Dependent Claims Only** | Conflict-Narrow — file only as dependent claim on a related broader filing |
| **Hold — Counsel FTO Opinion Required** | Blocking FTO — do not file until attorney clears the blocking art |
| **Defensive Publication** | Novel but crowded or low commercial value — publish to block competitors |
| **Trade Secret** | Valuable but protection through secrecy is better than patent |
| **Copyright Registration** | Source code, design files, documentation |
| **Trademark Filing** | Brand names, product names |
| **Design Registration** | Ornamental product designs |
| **Controlled Disclosure** | Publish or present strategically to establish prior art; counsel review on timing required |

### 7.2 Bundle Strategy

Group utility patents into **filing bundles** — one provisional application can cover multiple related claims:

**Bundling criteria:**
- Technical relatedness (same functional block or architecture layer)
- Claims that can be organized as independent + dependent
- Strategic benefit of joint filing (e.g., all items in one technology cluster)

**Bundle naming:** FB-[TECH-CLUSTER]-[NN] (e.g., FB-CORE-01, FB-SEC-01, FB-API-01)

For each bundle:
- List constituent IP items
- Define the core independent claim (the broadest, most defensible concept)
- List dependent claims derived from narrower IPs
- Note whether to use decoy embodiments (describe alternative implementations to dilute examiner attention from core claim)

### 7.3 Filing Calendar (M0–M36+)

| Milestone | Month from Now | Actions |
|---|---|---|
| **M0 — Immediate** | Now | P0★ provisionals (competitor-race items); trademark filings in home country; copyright batch registrations; defensive publication submissions |
| **M3** | +3 months | All P0 provisionals; begin P1 provisional drafts; design registration prep |
| **M6** | +6 months | P1 provisionals; PCT decision for M0 batch (should file PCT within 12 months of earliest priority) |
| **M12** | +12 months | PCT filing for M0 batch (deadline: 12 months from provisional priority date); P2 provisional consideration |
| **M18** | +18 months | PCT filing for M1-M3 batch; P1 PCT decisions |
| **M24–M30** | +24-30 months | National phase entry (US, EP, target markets) for M0 batch |
| **M30–M36** | +30-36 months | National phase entry for M6-M12 batch; full prosecution begins |

**IMPORTANT jurisdiction-specific deadlines:**
- India to PCT: file PCT within 12 months of Indian provisional priority date
- PCT to national phase: 30 months from earliest priority date (EP: 31 months)
- Paris Convention: 12 months from first filing to claim priority in other countries

### 7.4 Section 35 / Dual-Use / Export Control Checks

For items flagged in Step 1 (defense, dual-use, encryption, controlled technology):
- **India (SCOMET)**: Items in Schedule 2 of SCOMET require export license before foreign filing. Engage SCOMET counsel before PCT national phase entry into US, Israel, or other controlled jurisdictions.
- **US (EAR)**: Technology controlled under Export Administration Regulations may require license. Check ECCN classification.
- **EU (EU Dual-Use Regulation)**: Category 3 (electronics), Category 5 Part 1 (telecom), Category 5 Part 2 (information security) may be controlled.
- File in home country first; always obtain legal opinion before foreign filing of flagged items.

### 7.5 OSS Gate Resolution

For any items with an OSS gate (from Step 1):
- Document the OSS dependency, its license, and what obligation it creates
- Specify what must happen before the patent can be filed (e.g., required foundation/consortium membership, contributor attribution, GPL compliance audit)
- Include in action list

### 7.6 Cost Model

**Calculate estimated costs using these fee schedules:**

**Home Jurisdiction Fee Schedules:**

*India (IPO — as of 2024; apply MSME/startup 80% rebate if applicable):*
| Action | MSME/Startup | Large Entity |
|---|---|---|
| Provisional application | ₹1,600 | ₹8,000 |
| Complete specification (non-PCT) | ₹4,000 | ₹16,000 |
| Request for examination | ₹4,000 | ₹20,000 |
| Annual renewal (Yr 2-6) | ~₹800/yr | ~₹4,000/yr |
| Annual renewal (Yr 7-11) | ~₹2,400/yr | ~₹12,000/yr |
| Annual renewal (Yr 12-20) | ~₹4,000/yr | ~₹20,000/yr |

*PCT (WIPO fees in USD, 2024):*
| Action | Fee |
|---|---|
| International filing fee | ~$1,450 (≤30 pages) + $16/page over 30 |
| Search fee (USPTO as ISA) | ~$2,080 |
| Search fee (EPO as ISA) | ~$1,970 |
| Transmittal fee | ~$200 |

*USPTO (US, small entity):*
| Action | Small Entity | Micro Entity |
|---|---|---|
| Provisional | $320 | $160 |
| Non-provisional (filing) | $820 | $410 |
| National phase entry | $320 | $160 |
| Issue fee | ~$1,000 | ~$500 |
| Maintenance 3.5yr/7.5yr/11.5yr | $400/$900/$1,850 | $200/$450/$925 |

*EPO (European, in EUR):*
| Action | Fee |
|---|---|
| Filing fee | €1,350 |
| Search fee | €1,460 |
| Examination fee | ~€1,880 |
| Grant fee | ~$925 |
| Designation fee | €685 per country (use EPC validation states) |
| Annual renewal (Yr 3-20) | €520–€1,640/yr |

*Attorney cost estimates (indicative; verify with local counsel):*
| Activity | Estimated Cost (USD) |
|---|---|
| India provisional drafting (Indian firm) | $300–$800 |
| PCT preparation (Indian/US firm) | $2,000–$5,000 |
| US national phase prosecution (full) | $5,000–$15,000 |
| EP prosecution (full) | €5,000–€15,000 |
| Trademark filing (per jurisdiction) | $800–$2,500 |
| Copyright registration batch | $50–$200 per work |

**Cost offset and savings opportunities (check for each jurisdiction):**
| Scheme | Jurisdiction | What it Offers |
|---|---|---|
| TIFAC PFP (Patent Facilitation Programme) | India | Reimburses attorney fees up to ₹5L per PCT family |
| Startup India – IPR Scheme | India | 80% rebate on IPO fees for DPIIT-registered startups |
| MSME 80% rebate | India | Automatic 80% rebate on IPO official fees |
| iDEX PRIME | India | Defence innovation funding (if defense-applicable) |
| Section 115BBF Patent Box | India | 10% tax on patent royalties (vs 30% corporate rate) |
| USPTO fee reduction | US | 60% reduction for small entity; 80% for micro entity |
| EPO SME support | EU/EP | Fee reductions for SMEs in some EPC states |
| Open Invention Network | Global | Free membership = protection from OIN member suits in Linux/OSS space |
| LOT Network | Global | Free to join; protects against troll patent suits from other members |

**Scenarios:**
| Scenario | Description | Notes |
|---|---|---|
| **A — Home country only** | File provisionals + complete spec in home country only; no PCT | Cheapest; weakest protection |
| **B — PCT + Top 3 markets** | Home country provisional → PCT → national phase in 3 key markets | Recommended for most startups |
| **C — Aggressive global** | Home country → PCT → 5+ jurisdictions national phase | Maximum protection; highest cost |
| **D — M0–M12 only** | File all provisionals now to lock priority dates; decide PCT at M12 based on traction | Low upfront cost; preserves optionality |

Calculate total 20-year portfolio cost for each scenario. Show year-by-year cash flow if possible.

### 7.7 Step 7 Summary Output

Write `_meta/step7_filing_strategy.md` with:
1. Filing disposition table (all items)
2. Bundle strategy (all bundles)
3. M0–M36 filing calendar
4. Section 35 / export control action items
5. OSS gate checklist

Write `_meta/cost_model.md` with:
1. Fee schedule assumptions (jurisdiction, entity type, FX rate used)
2. Per-item cost estimate (utility patents)
3. Non-patent IP cost summary (TM, ©, design registrations, defensive pubs)
4. Scenario A/B/C/D comparison table
5. Year-by-year cash flow (Scenario B as baseline)
6. Cost offset opportunities and estimated savings
7. Total portfolio cost (20-year lifecycle, all scenarios)

---

## FINAL OUTPUT GENERATION

### DOSSIER.md (Master Entry Point)

Create `DOSSIER.md` as the single-entry master document:

```markdown
# [Product Name] IP Portfolio — Master Dossier

**Prepared:** [Date]
**Classification:** Confidential — Attorney-Client Privilege Intended
**Status:** Steps 1–7 Complete — Ready for Counsel Briefing
**One-liner:** [Company] holds [N] distinct IP items across [X] categories for [Product]; 
[M] utility patent applications proposed in [B] bundles; 
20-year portfolio lifecycle ~$[cost]; 
file [top priority item] this week.

---
[LEGAL DISCLAIMER]

---
## How to Use This Document
[Brief guide to navigating the folder structure]

## 1. Portfolio At a Glance
[Table: Category × Items × 20yr Cost × Priority × Proposed Action]

## 2. Analysis Abstracts
[One paragraph per step, linking to meta files]

## 3. Complete IP Catalogue
[Table: ID × Title × Category × Priority × Filing Flag × FTO Risk — with links to individual files]

## 4. Top Priority Actions
[Numbered, dated, assignable action list — M0 items first]

## 5. FTO Risk Summary
[Table + paragraph on blocking items]

## 6. Budget Summary
[Scenario comparison table + recommended scenario]
```

### Executive Landscape Report (_report/IP_Landscape_Report.md)

Create a professional, shareable report modeled on the Clairvolex structure:

```markdown
# [Product Name] — IP Landscape Analysis
**Prepared by:** [Company] Internal IP Team using Claude Code IP Landscape Skill
**Date:** [Date]
**Classification:** [Confidential / Public]

[LEGAL DISCLAIMER]

---
## Research Methodology
[5-step process description: Technology Search → Prior Art Search → Taxonomy & Segmentation → 
Bibliographic Insights → Technology Insights & Whitespace]
[What databases were searched, what scope was covered]

## Key Insights (Executive Summary)
[8-12 bullet points — the most important strategic findings. Each should be specific and data-backed.]

## Technology Taxonomy
[Taxonomy tree + description of how it was built]

## Patent Landscape Analysis

### Priority vs. Filing Trend
[Year-by-year table + interpretation]

### Top IP Owners
[Table + key observations]

### Emerging Players (Last 2-3 Years)
[Table + commentary]

### Technology Collaboration (Company + University)
[Table]

### Technology Innovation Countries
[Table + map description]

### Jurisdiction Spread
[Preferred + emerging jurisdictions table]

### Legal Status Distribution
[Alive/dead families; granted/pending/expired breakdown]

### Top CPC/IPC Classifications
[Top 15-20 classes with definitions]

### Key Inventors
[Top 10-15 inventors]

## Technology Insights

### Technology Focus Areas
[Per-cluster analysis]

### Sub-Technology Breakdown & Whitespace Heatmap
[Table with whitespace ratings]

### Application Areas
[If applicable]

### Correlation Analysis — Key Observations
[4-5 cross-dimensional insights]

## Your IP Portfolio — Competitive Position

### Portfolio at a Glance
[Table: Category × Count × Cost × Priority]

### FTO Risk Distribution
[Clear/Watch/Conflict-Narrow/Blocking breakdown with implications]

### Competitive Position per IP Item
[Table: ID × Taxonomy Node × Position × Differentiator]

## Filing Strategy Overview
[M0–M36 calendar summary; bundle count; scenario recommendation]

## Cost Summary
[Scenario A/B/C/D table; recommended scenario with rationale]

## Appendix
### A. Out-of-Scope References
### B. CPC Class Definitions (Top 20)
### C. All Search Queries Used (from search_log.md)
### D. Complete IP Catalogue
### E. Databases Used
```

### Action List (_meta/action_list.md)

Create a numbered, dated, and assignable action list:

```markdown
# Priority Action List

## IMMEDIATE (M0 — This Week)
1. [Action] — Owner: [role] — Deadline: [date] — Rationale: [why urgent]

## SHORT-TERM (M0–M3)
...

## MEDIUM-TERM (M3–M12)
...

## LONG-TERM (M12+)
...
```

---

## EXECUTION RULES

Follow these rules throughout all steps:

1. **Search log first.** Before any external search, add a row to `search_log.md`. After the search, update with results count and key finds.

2. **Real data only.** Never invent patent numbers, assignee names, or prior art. If search returns no results, say "No results found for this query" — that is a valid (and sometimes positive) finding.

3. **Update individual files incrementally.** After each step, update the relevant section in each individual IP item's file. Do not wait until the end.

4. **Pause for user decisions on:**
   - Any Blocking FTO items (before Step 6 finalizes)
   - Any ambiguous classification (2 equally valid options — ask user)
   - Any IP item where the user's technology description is unclear
   - Budget scenario selection (Scenario A/B/C/D)

5. **Flag legal risks explicitly.** Section 35 / SCOMET / EAR / OSS license obligations — don't bury these. Surface them prominently in the action list.

6. **Be conservative on FTO.** When in doubt between Clear and Watch, choose Watch. When in doubt between Watch and Conflict-Narrow, choose Conflict-Narrow. Overclaiming safety is worse than overclaiming risk.

7. **Jurisdiction-specific details.** Adapt fee schedules, rebate calculations, and compliance requirements to the home jurisdiction provided in startup interview. For India: apply MSME/startup 80% rebate if applicable. For US: apply small/micro entity fees. For EU: apply EPO SME rules.

8. **Step-end reporting.** At the end of each step, send user a brief summary: what was completed, key numbers, any blocking issues found, and confirm you are proceeding to next step.

9. **Never skip a utility patent.** Even if a prior art search returns many results for one item, complete the search for all utility patent candidates. Depth may vary but coverage must not.

10. **OSS licenses are FTO issues.** GPL/LGPL code in your product = FTO risk for your product IP. Apache/MIT = generally permissive. Flag GPL and LGPL explicitly.

---

## LEGAL DISCLAIMER (USE IN ALL OUTPUTS)

```
LEGAL DISCLAIMER: This IP landscape analysis is prepared for internal planning purposes only and 
does not constitute legal advice. It is not a formal Freedom-to-Operate opinion or patentability 
assessment. Prior art search results are based on free public databases and may not be exhaustive. 
Patent families, legal status, and claim scope must be verified by qualified patent counsel before 
any filing, licensing, or enforcement decisions. CPC classification searches and keyword searches 
have inherent coverage gaps. All cost estimates are indicative only and exclude attorney and 
professional service fees unless otherwise noted. Engage a qualified patent attorney before any 
commercialization, filing, or licensing decision. This document is not privileged attorney-client 
communication unless prepared under the direction of licensed legal counsel.
```

---

*Built by [abhikuchbhi.in](https://abhikuchbhi.in)*
