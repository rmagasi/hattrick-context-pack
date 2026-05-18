# Contributing to Hattrick Context Pack

Thanks for thinking about contributing. This repository is a community-maintained knowledge pack about Hattrick.org mechanics, and it gets better when more managers help keep it accurate, complete, and up to date.

## How to contribute

You can contribute in three ways, from lightest to heaviest:

1. **Open an issue** describing what's wrong, missing, or out of date. Use the issue templates (rule change, missing topic, correction). This is the right path if you've spotted a problem but don't have time to write the fix yourself.

2. **Submit a Pull Request** with the change. Use the PR template. This is the right path for small fixes (typos, number corrections, clarifications) or larger additions you've already drafted.

3. **Add a new language pack** following the pattern in `skills/hattrick/references/languages/hungarian.md`. See "Language packs" below.

## Style rules

These keep the knowledge pack consistent and legally safe to redistribute.

**Write in your own words.** Don't copy verbatim text from Hattrick.org, the official rulebook, the wiki, or any other Hattrick-controlled source. The CHPP Product License Agreement (rule 7.2) explicitly forbids reusing Hattrick's site text without permission. Reading the rulebook to understand a mechanic and then explaining it in your own words is fine, that's what most of the existing skill is. Pasting a rulebook paragraph in directly is not.

Verbatim is fine for **facts**: numbers (prize money, formulas, thresholds), proper names (skill levels, formation codes, country names), and short technical terms. Those aren't creative expression, they're game data.

**Cite non-obvious sources.** If you add a fact that isn't on the surface of the rulebook (e.g., something from a devblog post, a community study, a forum thread), include a source link or a short attribution. The existing skill content shows the pattern.

**Keep edits paragraph-sized.** Large structural rewrites are harder to review than focused changes. If you want to overhaul a whole section, open an issue first to discuss.

**Match the existing tone.** The skill is written for an AI assistant to read, not a human, so it's dense and factual. Bullet points and tables are encouraged where they make information scannable. Avoid filler ("it's important to note that...") and avoid editorial voice ("you should always...").

## Language packs

Hattrick is played in dozens of languages. Each language pack is one file at `skills/hattrick/references/languages/<language>.md`. Use `hungarian.md` as the template, it covers:

- Skill / rating level names
- Form, leadership, formation XP scales
- Mood scales (sponsor, supporter, expectations, season goals)
- Team / player attributes (Team Spirit, Confidence, agreeability, honesty, aggressiveness)
- Common Hattrick terms (player, coach, training, transfer, etc.)
- Country-specific cup names
- Currency notation

Sourced from **Appendix 2 of the rulebook in the target language**. Keep the structure consistent across language packs so the bundle assembler can include them interchangeably.

## What kinds of changes are most useful

- **Rule changes**: when Hattrick announces a mechanic change (devblog post, news item), the relevant section here should be updated within a few days. Issues tagged "rule change" are the highest priority.
- **Missing topics**: corners-from-anyone scoring math, IFK conversion details, set-piece training math, etc. Anything where the current skill says "approximately" or "roughly" and a real number exists.
- **Corrections**: outdated numbers, formulas superseded by newer Live-data studies, typos, broken links.
- **New language packs**: see above.

## What kinds of changes don't fit here

- **Tactical opinions** ("3-5-2 is always better than 4-4-2"). The skill is meant to give the AI factual game knowledge so it can reason with the user, not pre-bake tactical preferences.
- **Personal scenarios** ("for my team specifically..."). The pack is for everyone, no individual examples.
- **Tools and external services** unless they're widely-used community resources (HO, Foxtrick, Hattrick Youthclub, etc.).
- **Hattrick site UI walkthroughs** ("click here, then here..."). The pack describes game mechanics, not the website's interface.

## Review process

The repository maintainer reviews PRs. Expect a few days for response, possibly longer during busy weeks. Maintainer might ask for changes before merging. After merge, the version in `.claude-plugin/plugin.json` gets bumped, and downstream consumers (Claude plugin installations, the Hattrick AI Context web service when it ships) pick up the change on their next refresh.

## Code of conduct

Be useful and kind. Hattrick is a small community, we all know each other in some form. Disagreements on rules interpretation happen, resolve them with citations not insults.

## Questions

If you're not sure whether a change belongs here or how to format it, open an issue with the "Question" label and ask. No edit is too small to discuss first.
