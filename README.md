# Claude Skills

A collection of custom slash commands (skills) for [Claude Code](https://claude.ai/code), built by a hands-on operator for running business workflows faster.

Skills are single `.md` files. They work in **Claude Code (CLI)** and **Claude.ai (web/mobile)**.

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

### IP

| Skill | Invoke | Description |
|-------|--------|-------------|
| [ip-landscape](./ip/ip-landscape.md) | `/ip:ip-landscape` | Professional-grade IP landscape analysis — patent strategy, prior art search, FTO analysis, filing roadmap, and competitor mapping |

---

## Author

[abhikuchbhi.in](https://abhikuchbhi.in)

## License

MIT
