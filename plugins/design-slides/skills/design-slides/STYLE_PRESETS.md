# Style Presets

Use these as starting points for interview decks. Adapt them to the actual case material and any reference images Tony provides.

## Selection Rule

Choose the quietest style that still supports the story. The deck should make screenshots, design reasoning, and spoken narrative easier to follow.

## 1. Product Review

**Best for:** SaaS, mobile app, dashboard, workflow, and product design cases.

**Tone:** Clear, mature, structured, interview-safe.

**Typography:**

- Display: `Manrope` 700/800
- Body: `Source Sans 3` 400/600

**Colors:**

```css
:root {
  --bg: #f7f7f4;
  --surface: #ffffff;
  --ink: #151515;
  --muted: #686b70;
  --line: #d9d8d2;
  --accent: #1f6feb;
  --accent-soft: #dbeafe;
}
```

**Signature elements:**

- White or off-white canvas
- Thin dividers and precise spacing
- Screenshot frames with small labels
- Short evidence tags such as `Research`, `Constraint`, `Decision`, `Impact`

## 2. Editorial Case

**Best for:** Story-heavy case studies, service design, research-led projects, and reflective interview narratives.

**Tone:** Thoughtful, crafted, calm.

**Typography:**

- Display: `Fraunces` 700/900
- Body: `IBM Plex Sans` 400/500

**Colors:**

```css
:root {
  --bg: #fbf7ef;
  --surface: #fffdf8;
  --ink: #1f1b16;
  --muted: #746d64;
  --line: #e1d7c8;
  --accent: #b64b2b;
  --accent-soft: #f1d9cc;
}
```

**Signature elements:**

- Strong editorial section titles
- Pull quotes for user insight or design principle
- Warm accent rules and numbered moments
- Large screenshots paired with concise commentary

## 3. Systems Walkthrough

**Best for:** Design systems, AI/agent flows, data products, complex workflows, or cross-platform cases.

**Tone:** Analytical, precise, modern.

**Typography:**

- Display: `Archivo` 700/800
- Body: `DM Sans` 400/500
- Mono labels: `JetBrains Mono` 400

**Colors:**

```css
:root {
  --bg: #101418;
  --surface: #171d23;
  --ink: #f4f7fa;
  --muted: #9aa6b2;
  --line: #2b3540;
  --accent: #58c4dd;
  --accent-soft: rgba(88, 196, 221, 0.16);
}
```

**Signature elements:**

- Dark canvas with restrained cyan accents
- Flow diagrams, system maps, and decision matrices
- Monospace metadata labels
- High-contrast screenshot containers

## 4. Portfolio Critique

**Best for:** Visual craft reviews, brand/product moments, high-fidelity UI walkthroughs, and before/after comparisons.

**Tone:** Polished, confident, design-forward.

**Typography:**

- Display: `Satoshi` 700/900
- Body: `Satoshi` 400/500

**Colors:**

```css
:root {
  --bg: #111111;
  --surface: #1b1b1b;
  --ink: #f6f2eb;
  --muted: #aaa39a;
  --line: #34302b;
  --accent: #e6b35a;
  --accent-soft: rgba(230, 179, 90, 0.18);
}
```

**Signature elements:**

- Full-bleed or large framed visuals
- Small captions that explain what changed and why
- Before/after grids with disciplined spacing
- Minimal decorative layers

## Anti-Patterns

- Generic purple/blue gradient hero slides
- Repeating card grids when screenshots or decisions should lead
- Decorative blobs, heavy glassmorphism, and random floating shapes
- Tiny screenshots with unreadable UI
- Large process diagrams without project-specific evidence
