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

In Claude Code or Cowork: Settings, Plugins, Add Marketplace, paste this repository's URL (`https://github.com/rmagasi/hattrick-context-pack`). Install the `hattrick-context-pack` plugin from the marketplace card. The skill auto-loads when you ask Hattrick-related questions.

## Installing in other AI tools

The knowledge pack is just Markdown. Any AI tool that lets you provide a long system prompt, a project rules file, or upload a document can use it. Pick the recipe that matches your tool.

### ChatGPT - Custom GPT (recommended for repeated use)

This is the cleanest option if you use ChatGPT regularly for Hattrick.

1. Open <https://chatgpt.com/gpts/editor> and click **Create**.
2. Give it a name (e.g. "Hattrick Coach") and a short description.
3. In the **Instructions** field, paste the contents of `skills/hattrick/SKILL.md`.
4. Under **Knowledge**, upload every `.md` file from `skills/hattrick/references/` (training-detail.md, tactics-detail.md, etc.). Upload the relevant `references/languages/*.md` if you play Hattrick in a non-English language.
5. Save. The custom GPT now has the full pack and auto-loads it on every chat.

### ChatGPT - one-off conversation

1. Start a new chat.
2. Drag and drop `skills/hattrick/SKILL.md` AND the references you might need into the conversation.
3. As your first message, say: "Use the attached Hattrick knowledge pack for everything that follows. Cite specific tables and sections when you answer."

Faster than the Custom GPT route, but you have to re-upload each conversation.

### Google Gemini

1. Open <https://gemini.google.com> and start a new chat.
2. Click the file attachment icon and upload `skills/hattrick/SKILL.md` and the relevant `references/` files.
3. First message: "Use the attached Hattrick knowledge pack as your authoritative reference. Cite sections when answering."

For Gemini Pro / Gemini Advanced users with Gems (custom assistants), the recipe is the same as ChatGPT's Custom GPT, paste `SKILL.md` into the system instructions and upload references as knowledge files.

### Cursor (AI coding editor)

Cursor lets you pin context files for an entire workspace.

1. Clone this repo somewhere on your machine.
2. In your Cursor project, open Settings → Rules.
3. Reference the skill file with `@skills/hattrick/SKILL.md` or copy its contents into your project's `.cursorrules` file.
4. The skill is now available to Cursor's chat / inline AI within that workspace.

Same pattern works for Continue.dev, Cline, Aider, and other code-assistant tools that support a rules / context file.

### Anthropic API / OpenAI API / any LLM API

Paste `SKILL.md` into your **system prompt**. For longer conversations, also include the relevant `references/*.md` files. Modern models (Claude 3.5+, GPT-4o, Gemini 1.5 Pro+) handle the combined ~50-100KB system prompt without trouble.

```python
# Pseudo-code, applies to any chat completion API
system_prompt = open("skills/hattrick/SKILL.md").read()
system_prompt += "\n\n" + open("skills/hattrick/references/training-detail.md").read()
# ... include whichever references the conversation needs
```

### Generic fallback for any tool

If your AI tool doesn't have a structured way to load knowledge files, you can always:

1. Concatenate the files you need into one big Markdown blob:

   ```bash
   cat skills/hattrick/SKILL.md skills/hattrick/references/*.md > hattrick-knowledge.md
   ```

2. Paste the contents at the start of your conversation, prefixed with: "Use the following Hattrick knowledge pack as authoritative reference for everything that follows:".

This works in chat-only tools, browser-based LLMs, internal chatbots, anything that accepts text input.

### Which references to include

`SKILL.md` is the main file and covers 80% of common questions. The `references/` files are deep dives, load them when your question touches that area:

| File | Load when asking about |
|------|------------------------|
| `training-detail.md` | Training speed, skill pops, stamina tables |
| `tactics-detail.md` | Ratings formulas, CA/LS/AOW math, formation matchups |
| `match-engine-deep.md` | Special events, man marking, corners, chance distribution |
| `position-contributions.md` | Per-position skill contribution percentages (the Unwritten Manual tables) |
| `economy-detail.md` | Player wages, sponsor maths, staff costs, currency conversion |
| `xp-form-loyalty.md` | XP, form, loyalty contributions, TSI formula |
| `tournaments-cups.md` | League fixture matrix, cup prizes, NT format |
| `languages/hungarian.md` | Hungarian terminology (skills, moods, attributes) |

When in doubt, include them all, the total is well under any modern LLM's context window.

## Pairing the skill with HRF files

The knowledge pack on its own answers general Hattrick questions ("what's the LS tactic formula?", "how does formation XP work?"). The real power comes from combining it with your own team's data, which lives in HRF files (HO's local team export format).

### What an HRF is

An HRF is a plain-text INI-style snapshot of one team, full skill levels for own teams, public-visible skills for opponents, plus league standing, match history, finances (own teams only), and more. Hattrick Organizer (HO!) generates them automatically when you click File → Download for any team. Each download is a fresh point-in-time snapshot.

### Getting your HRFs

If you already use HO! on your desktop:

1. Open HO! and log in.
2. File → Download for your team. HO! fetches the latest data via CHPP and writes an HRF to its configured HRF folder.
3. To scout an opponent, repeat for the opponent's team ID. HO! detects you're not the owner and writes a public-skills-only HRF.

Default HRF folder locations:

- Windows: `%APPDATA%\HO\HRF\` (e.g. `C:\Users\<you>\AppData\Roaming\HO\HRF\`)
- macOS: `~/Library/Application Support/HO/HRF/`
- Linux: `~/.HO/HRF/` (varies by HO! distribution)

HO!'s own settings panel shows the configured HRF path, override it there if you want them written somewhere your AI tool can read easily.

### Connecting an HRF to the AI

How you feed the HRF to the AI depends on the tool:

- **Claude Desktop / Cowork**: drag the .hrf file into the chat, or give Claude folder access via the file tool / a Filesystem MCP, then ask it to read the latest HRF.
- **ChatGPT (web)**: drag the .hrf into the chat as an attachment, ChatGPT reads plain text files.
- **Custom GPT**: same as above per conversation, or pre-upload a representative HRF to the GPT's knowledge if you want it always available.
- **Gemini**: attach the .hrf via the upload button.
- **Cursor / Continue / Cline**: keep the HRFs in a folder inside your project, the agent can read them via its file tools.

### Example prompts

Once the skill is installed AND your HRF is attached, you can ask team-specific questions:

```
I've attached my latest HRF for Hetvehely. Using the Hattrick context pack,
recommend a starting XI for our next league match. We're at home, weather
forecast is sunny.
```

```
Two HRFs attached, mine (Hetvehely) and the opponent's (FC Bombázók) from
this week. Scout the opponent, identify their weak sectors, and suggest
formation + tactic.
```

```
HRF attached. We just lost 0-5 and team spirit dropped from Walking on
Clouds to Irritated. What does the data say about the cause, and what
should we change for next week (training, lineup, staff)?
```

The skill gives the AI the rules, the HRF gives it your actual team state. Together they produce specific, game-aware advice instead of generic Hattrick wisdom.

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
