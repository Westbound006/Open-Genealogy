---
name: wikitree
version: 1.0.0
license: MIT
---

# WikiTree Skill

Query WikiTree profiles, explore ancestor and descendant trees, find
research gaps, and search for people — all from within Claude Code.

Uses the [WikiTree API](https://github.com/wikitree/wikitree-api)
(read-only, public profiles, no key required).

## Installation

```bash
cp -r skills/wikitree ~/.claude/skills/wikitree
```

Restart Claude Code. The skill is available via `/wikitree` or natural
language.

## What It Does

| Command | Example |
| ------- | ------- |
| Look up a profile | "look up Philpott-1879" |
| Explore ancestors | "show my ancestors to 3 generations" |
| Find research gaps | "find gaps in my WikiTree tree" |
| Search by name | "search WikiTree for Mary Philpott born 1850" |
| Explore descendants | "show descendants of Adams-35" |

## Requirements

- Claude Code
- Internet access (calls `api.wikitree.com`)
- `curl` (available on macOS/Linux by default)
- No WikiTree account needed for public profiles

## Default Profile

This skill is configured with `Philpott-1879` as the default WikiTree ID.
Saying "my profile" or "my ancestors" will use this ID automatically.

To use a different default, edit the **User Defaults** section in
`SKILL.md`.

## Notes

- WikiTree is a collaborative tree — data may contain errors. Always
  verify important findings against primary sources.
- Private and living-person profiles return limited data without
  authentication. Full authenticated access is not currently supported
  by this skill.
- The WikiTree API is free and does not require an API key for public
  data.
