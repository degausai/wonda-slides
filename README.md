<p align="center">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="assets/logo/dark.svg">
    <img alt="Wonda Slides" src="assets/logo/light.svg" width="320">
  </picture>
</p>

<p align="center">
  <strong>One-shot branded slide decks from your notes. Built for agents.</strong>
</p>

<p align="center">
  <img src="assets/demo.gif" alt="Notion notes turned into a branded deck in one prompt" width="100%">
</p>

<p align="center">
  <a href="LICENSE"><img alt="MIT License" src="https://img.shields.io/badge/license-MIT-blue.svg"></a>
  <a href="https://agentskills.io"><img alt="agentskills.io compatible" src="https://img.shields.io/badge/agentskills.io-compatible-7c3aed.svg"></a>
  <img alt="Claude Code" src="https://img.shields.io/badge/Claude%20Code-ready-d97757.svg">
  <img alt="Cursor" src="https://img.shields.io/badge/Cursor-ready-000.svg">
  <img alt="Codex" src="https://img.shields.io/badge/Codex-ready-10a37f.svg">
  <img alt="Gemini CLI" src="https://img.shields.io/badge/Gemini%20CLI-ready-4285f4.svg">
  <a href="https://wonda.sh"><img alt="Powered by Wonda" src="https://img.shields.io/badge/powered%20by-wonda.sh-ff5cb1.svg"></a>
</p>

---

## Quick start

Install the skill into any [agentskills.io](https://agentskills.io)-compatible host. Then prompt your agent.

#### Claude Code

```bash
git clone https://github.com/degausai/wonda-slides ~/.claude/skills/wonda-slides
```

#### Cursor

```bash
git clone https://github.com/degausai/wonda-slides .cursor/rules/wonda-slides
```

#### Codex / Gemini CLI / OpenCode / Goose / others

The pattern is the same: clone into your host's skills directory. Per-host paths at [agentskills.io/clients](https://agentskills.io/clients).

```bash
git clone https://github.com/degausai/wonda-slides <your-host-skills-dir>/wonda-slides
```

#### Via Wonda CLI

Also gets you image generation, video generation, and 12 other content skills.

```bash
npm i -g @degausai/wonda
wonda skill install --all -o .claude/        # or -o .cursor/rules/
```

### Then prompt your agent

```
Make me a 6-slide deck from ./notes.md branded like https://lovable.dev
```

```
Regenerate slide 3 with the bullet-list template
```

```
Export as 1080×1080 for Instagram
```

---

## Why this exists

- One-shots fully branded decks from notes that already exist (Notion, Google Docs, Granola, codebase markdown). No template store, no theme picker.
- Pulls real brand tokens from any URL. Not a "color palette" mode. Real CSS extraction with type tokens, pattern stack, hero-asset detection, font self-host detection.
- 50% fewer tokens than `claude design`. Agents can run it many times in a single session without burning context.
- Output is plain HTML, so it renders cleanly to PDF and PNG at any target resolution: 1920×1080, 1080×1080, 9:16, OG card, 2560×1440 retina.

---

## How it works

1. **Design system.** Extract real brand tokens from a URL via the bundled [dembrandt](https://github.com/dembrandt/dembrandt) CLI loop, or read them from a local theme file if your codebase already has one.
2. **Content.** Pull slide copy from Notion (REST API), Google Docs (Drive MCP or public-link export), or any markdown source. Outline before HTML so iteration stays cheap.
3. **Render.** HTML to Playwright to PDF + PNG, at exactly the target resolution. One file per slide, no SaaS export step.

Full skill instructions live at [`slide-generation-system/SKILL.md`](slide-generation-system/SKILL.md).

---

## For other content skills, use Wonda

Slides are one skill. Wonda ships 12 more for AI agents that make content.

- `ugc-reaction-batch` · Batch TikTok-native UGC reaction videos with viral strategy
- `creative-static-ads` · Single-frame static ads, 6 conversion pillars × 8 archetypes × 8 hooks
- `premium-static-ads` · Higher-fidelity creative static ad pipeline
- `twitter-influencer-search` · Find X influencers and amplifiers from competitor or niche keywords
- `tiktok-ugc-pipeline` · Scrape viral reel, generate 5 UGC videos, post as drafts
- `tiktok-slideshow-carousel` · 3-slide TikTok carousel (hook, bridge, product reveal)
- `marketing-brain` · Marketing strategy brain (hooks, visuals, ads)
- `reddit-subreddit-intel` · Scrape top posts, analyze virality, generate ideas
- `ugc-talking` · Talking-head UGC (single, two-angle PIP, B-roll variants)
- `ugc-dance-motion` · Dance and motion transfer
- `image-edit` · img2img, background removal, crop, text overlay, vectorize
- `product-video` · Product or scene video, full prompt library across categories

```
npm i -g @degausai/wonda  ·  brew tap degausai/tap && brew install wonda  ·  https://wonda.sh
```

---

## How it compares

|                       | Wonda Slides                      | Claude design          | Manual (Slides / PPT / Figma) | Gamma / Beautiful.AI |
| --------------------- | --------------------------------- | ---------------------- | ----------------------------- | -------------------- |
| Brand fidelity        | Real CSS tokens from any URL      | Theme picker           | You design every pixel        | Template themes      |
| Source ingestion      | Notion, Google Docs, Markdown     | Paste                  | Paste                         | Paste, some imports  |
| Agent-native          | Yes (agentskills.io)              | Yes                    | No                            | No                   |
| Output formats        | HTML + PDF + PNG, any resolution  | In-app only            | App-locked formats            | App-locked formats   |
| Customization         | Full HTML and CSS edit            | Constrained            | Full but manual               | Template-constrained |
| Cost per deck         | Your tokens, no extra fee         | Your tokens            | Your time                     | Subscription         |

---

## Status

`v0.1` · battle-tested on real sales decks, investor decks, and internal pitches. Issues and PRs welcome. Open an issue first for big changes.

## License

[MIT](LICENSE)

## Credits

Inspired by [HeyGen HyperFrames](https://github.com/heygen-com/hyperframes), which proved that HTML-as-source-of-truth plus agent-native UX can win.

Built on top of [Wonda CLI](https://wonda.sh).
