---
name: design-slides
description: Create polished HTML presentation decks for Tony's design interviews, especially self-introduction and design case-study walkthroughs. Use when turning Obsidian project notes, case-study drafts, screenshots, reference visuals, or a user-provided deck framework into a clear, interview-ready design presentation with optional Vercel deployment.
---

# Design Slides

Create interview-ready HTML decks for design case studies. The default audience is a hiring panel evaluating product thinking, design craft, communication clarity, and business/user impact.

## Operating Principles

1. **Evidence first** - Read the provided notes, drafts, screenshots, and references before writing claims. If evidence is thin, qualify or omit the claim.
2. **Follow the user's framework** - If Tony provides a slide outline or content framework, use it as the primary structure. Only propose a structure when none is provided.
3. **Interview clarity over spectacle** - Visual design should support spoken storytelling. Avoid decorative complexity that competes with the case.
4. **Concrete design thinking** - Prefer specific UI decisions, tradeoffs, iterations, constraints, and outcomes over generic process language.
5. **No cramming** - Each slide must fit in one viewport with no scrolling. Split dense material into multiple slides.

## Default Workflow

### 1. Intake

Collect and inspect the available materials:

- Obsidian project notes or case-study notes
- Existing self-introduction or portfolio copy
- Screenshots, Figma exports, mockups, diagrams, or reference visuals
- Job description, company context, or interview format when provided
- Tony's requested deck framework, slide count, visual direction, and delivery need

If the requested deck structure is unclear, ask once for the missing decision. Do not invent a fixed case-study outline when the user has supplied one.

### 2. Evidence Audit

Before drafting slides, summarize the usable evidence:

- Strong evidence: facts, artifacts, metrics, screenshots, research findings, direct project notes
- Weak evidence: inferred claims, vague impact, unclear ownership, missing before/after proof
- Gaps: important story points that need user confirmation

Use this audit to keep the deck honest. Avoid overclaiming ownership, impact, technical scope, or research depth.

### 3. Narrative Compression

Transform source material into presentation-ready slide messages:

- One main takeaway per slide
- Short slide titles that state the point, not just the topic
- Dense notes become selective bullets, diagrams, comparison tables, or annotated screenshots
- Keep speaker-support details in comments or presenter notes only if the output format supports them
- Highlight design decisions through this pattern: context -> options/tradeoff -> choice -> refinement -> user/business effect

When no framework is supplied, use this fallback sequence:

1. Opening / role positioning
2. Self-introduction snapshot
3. Case context and problem
4. Users, constraints, and goal
5. Key design decision 1
6. Key design decision 2 or iteration
7. Final solution / visual walkthrough
8. Outcome, learning, and why it matters

### 4. Visual Direction

Choose a visual direction from `STYLE_PRESETS.md` only after reviewing the material and any reference images. Start with a restrained professional direction unless Tony provides a stronger reference.

The deck should feel:

- Clear enough for a live interview walkthrough
- Designed enough to show craft and taste
- Consistent across typography, spacing, screenshot treatment, and transitions
- Adapted to the case subject rather than a generic template

### 5. HTML Generation

Create a self-contained HTML deck unless the user asks for a different format.

Before generating, read:

- `html-template.md` for required deck architecture
- `viewport-base.css` for viewport fitting rules
- `STYLE_PRESETS.md` for visual directions

Requirements:

- Single `index.html` or clearly named `.html` file
- Inline CSS and JavaScript
- External fonts are allowed through Google Fonts or Fontshare
- Local images should use relative paths and live beside the deck or under `assets/`
- Every `.slide` must be exactly one viewport high with `overflow: hidden`
- Use `clamp()` for type and spacing
- Include keyboard navigation and touch-friendly navigation
- Keep motion subtle and purposeful; support `prefers-reduced-motion`

Do not add inline editing, PPT conversion, PDF export, or extra deployment systems unless the user explicitly asks.

### 6. Verification

Verify before delivery:

- The deck opens locally
- Slides fit at 1280x720 and a narrow mobile viewport
- No text overlaps, clips awkwardly, or requires scrolling
- Screenshots and local images load
- Navigation works with arrow keys
- The final story follows the user's framework and does not contain unsupported claims

For substantial decks, use browser screenshots when available.

### 7. Optional Deployment

Only deploy when the user asks for a shareable URL.

Use:

```bash
bash scripts/deploy.sh <path-to-slide-folder-or-html>
```

Prefer deploying a folder containing `index.html` plus its assets. After deployment, verify the live URL loads and all images appear.

## What To Avoid

- Generic portfolio slogans without evidence
- Overly broad UX process slides that say nothing specific
- Visual effects that distract from screenshots or decision logic
- Dense research/process walls
- Reusing the same screenshot without a new point
- Purple-gradient generic AI aesthetics
- Adding retired general-presentation behaviors by default
