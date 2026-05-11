# Design Slides

Personal Codex/Claude skill for creating interview-ready design case-study decks.

This repo is tuned for Tony's design interview workflow: take Obsidian project notes, optional text/images/reference visuals, and a user-provided deck framework, then produce a polished HTML presentation for self-introduction and design case walkthroughs.

## What It Does

- Audits source material before making claims
- Follows the deck framework you provide instead of forcing a generic template
- Compresses project notes into clear slide messages
- Emphasizes concrete UI decisions, tradeoffs, iterations, and impact
- Generates a self-contained HTML deck with responsive viewport-safe slides
- Optionally deploys the deck to Vercel for a shareable interview link

## What It Does Not Do By Default

- Convert PPT files
- Export PDFs
- Add browser-based inline editing
- Create general-purpose pitch decks for broad audiences

## Core Files

| File | Purpose |
| --- | --- |
| `SKILL.md` | Main skill instructions and workflow |
| `STYLE_PRESETS.md` | Interview-appropriate visual directions |
| `html-template.md` | Required HTML deck architecture |
| `viewport-base.css` | Viewport fitting rules for every generated deck |
| `scripts/deploy.sh` | Optional Vercel deployment helper |

The plugin-packaged copy under `plugins/design-slides/` should stay in sync with the root skill files.

## Usage

Use the skill when you need to turn design interview materials into a deck:

```text
Use design-slides to turn these Obsidian notes and screenshots into a 10-slide interview case-study deck. Follow my outline exactly.
```

The skill should first inspect the materials, identify evidence strength and gaps, then generate the deck only after the structure and claims are clear.

## Deployment

To deploy a finished HTML deck:

```bash
bash scripts/deploy.sh ./my-case-deck/
```

The folder should contain `index.html` and any local assets referenced by the deck.
