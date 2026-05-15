# Claude Skills

A collection of custom slash commands (skills) for [Claude Code](https://claude.ai/code).

## Installation

Each skill is a single `.md` file. To install:

**Global** (available in any project):
```bash
cp <skill>.md ~/.claude/commands/<skill>.md
```

**Project-level** (available only in the current project):
```bash
cp <skill>.md .claude/commands/<skill>.md
```

Then invoke with `/<skill-name>` inside Claude Code.

## Skills

| Skill | Description |
|-------|-------------|
| [ip-landscape](./ip-landscape.md) | Professional-grade IP landscape analysis — patent strategy, prior art, filing roadmap, and competitor mapping |

## Author

[abhikuchbhi.in](https://abhikuchbhi.in)

## License

MIT
