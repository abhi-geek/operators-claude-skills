# Claude Skills

A collection of custom slash commands (skills) for [Claude Code](https://claude.ai/code), built by a hands-on operator for running business workflows faster.

Skills are single `.md` files. They work in **Claude Code (CLI)** and **Claude.ai (web/mobile)**.

---

## Why this exists

I'm Abhishek — an engineer and operator who builds businesses around difficult science problems.

Every new problem I take on comes with a set of hard, research-heavy sub-problems that take real time to crack. But once I've cracked them, I don't want to solve them again. I want to write them down, systematize them, and move on to the next thing that actually needs my attention.

That's what this repo is. Every skill here started as a painful, manual task — something that required hours of research, cross-referencing, and domain knowledge to do well. I turned each one into a command so that the next time it comes up, for me or for anyone else, it takes minutes instead of days.

I use Claude heavily across every part of my work. I believe in automating solved problems so I can stay focused on the ones that still need research, creativity, and judgment. These skills are that automation layer for the business and legal side of building deep-tech companies.

If you're building something hard and running into the same kinds of operational problems, I hope this saves you some time.

I write about problems like these at **[The Operators](https://theoperators.substack.com/)**.

**PS:** If you can improve any of these skills, raise a PR — let's build this together.

---

---

## Installation

Skills are organized by category. Install a skill by copying its file to the right commands directory:

**Global** (available in any project):
```bash
cp <category>/<skill>.md ~/.claude/commands/<category>/<skill>.md
```

**Project-level** (available only in the current project):
```bash
cp <category>/<skill>.md .claude/commands/<category>/<skill>.md
```

Then invoke in Claude with `/<category>:<skill>` (e.g., `/legal:nda-review`).

---

## Skills

### Legal

| Skill | Invoke | Description |
|-------|--------|-------------|
| [nda-review](./legal/nda-review.md) | `/legal:nda-review` | Party-aware NDA analysis — surfaces red flags, non-standard terms, missing clauses, and jurisdiction-specific enforceability issues in a structured table |
| [term-sheet-analyzer](./legal/term-sheet-analyzer.md) | `/legal:term-sheet-analyzer` | Founder-first term sheet analysis — clause-by-clause scoring, red flag detection, exit waterfall simulation, option pool shuffle modeling, term sheet → SHA translation, and a negotiation playbook. Covers US/Delaware, India (FEMA/SEBI), and Singapore. Targets pre-seed, seed, and Series A rounds. |

### Intellectual Property

| Skill | Invoke | Description |
|-------|--------|-------------|
| [ip-landscape](./intellectual-property/ip-landscape.md) | `/intellectual-property:ip-landscape` | Professional-grade IP landscape analysis — patent strategy, prior art search, FTO analysis, filing roadmap, and competitor mapping |
| [trademark-clearance](./intellectual-property/trademark-clearance.md) | `/intellectual-property:trademark-clearance` | Comprehensive brand name clearance — 10-step screening across trademark registries (US, EU, UK, India, WIPO), domain availability, social handles, SEO visibility, meaning in foreign languages, misspelling variants, and government bans, with a full risk matrix and likelihood-of-confusion analysis |

---

## About

**Abhishek** — Engineer and Operator for deep science problems.

→ [abhikuchbhi.in](https://abhikuchbhi.in)
→ [The Operators — Substack](https://theoperators.substack.com/)

## License

MIT
