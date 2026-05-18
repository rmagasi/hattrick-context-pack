# Hattrick Context Pack

A community-maintained Hattrick.org knowledge pack for AI assistants. Drop it into Claude, ChatGPT, Gemini, or any other AI client to give it deep understanding of Hattrick game mechanics: training, match tactics, formations, economy, youth academy, cups, national teams.

This repo exists because mainstream AI assistants only know Hattrick at a surface level. With this knowledge pack in the conversation, an AI can give specific, game-aware advice on training paths, formation matchups, set-piece scoring, salary tax progression, and the other game-specific details that managers actually care about.

## What's here

The repository is a Claude plugin marketplace plus a portable knowledge pack:

```
.claude-plugin/plugin.json    plugin manifest for Claude Code / Cowork
skills/hattrick/
    SKILL.md                  the main knowledge file
    references/               deep reference material per topic
        training-detail.md
        tactics-detail.md
        match-engine-deep.md
        position-contributions.md
        economy-detail.md
        xp-form-loyalty.md
        tournaments-cups.md
        languages/
            hungarian.md      optional Hungarian terminology pack
```

The same content is consumable in several ways:

- **As a Claude plugin** - install this repository as a marketplace in Claude Code or Claude desktop (Cowork), the skill auto-loads when you ask Hattrick questions.
- **As a standalone knowledge pack for any AI** - paste `SKILL.md` and any relevant `references/` files into your AI's prompt, or upload as files.
- **Via Hattrick AI Context** (planned) - a hosted web service that bundles this knowledge with your live CHPP team data and exports it as a single Markdown file for any AI.

## Installing as a Claude plugin

In Claude Code or Cowork: Settings, Plugins, Add Marketplace, paste this repository's URL (`https://github.com/rmagasi/hattrick-context-pack`). Install the `hattrick-context-pack` plugin from the marketplace card.

## Contributing

This is a community knowledge pack. Rule changes, additions, corrections, new language packs, all welcome. See `CONTRIBUTING.md` for the contribution flow and style guidelines. Two important rules upfront:

1. Write in your own words. Don't copy verbatim text from Hattrick.org or the official rulebook - the CHPP Product License Agreement (rule 7.2) forbids reusing Hattrick's site content without explicit permission.
2. Cite sources for non-obvious factual claims (devblog post, forum thread, wiki page).

Use the GitHub Issues templates for proposing changes you don't want to write yourself, and Pull Requests for changes you want to submit directly.

## Sources

The knowledge in this pack is sourced from:

- **Official Hattrick rulebook**: <https://www.hattrick.org/Help/Rules/Complete.aspx>
- **The "Unwritten Manual #15"** by LA-Alpa et al. (Hattrick Global English forum thread 17665541), the primary community-curated mechanics reference.
- **Hattrick Developer Blog**: <https://devblog.hattrick.org/>
- **Hattrick Wiki**: <https://wiki.hattrick.org/>
- **Live-data studies** by community members (nickarana, Schum, bigpapy, ciscouf, WesselV1, others)

Full source list per topic is in `skills/hattrick/SKILL.md` under "Sources".

## Maintainer

Created and currently maintained by Robert Magasi (`robi_` on Hattrick). Open to additional maintainers as the project grows.

## License

MIT - see `LICENSE`.
