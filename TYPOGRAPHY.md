---
name: Substrate Typography
description: Type system for Syntropic. Geist Sans + Geist Mono, single family, restraint.
parent: DESIGN.md

fonts:
  sans:
    family: "Geist"
    stack: "Geist, Inter, system-ui, sans-serif"
    source: "vercel.com/font · npm: geist · Google Fonts · SIL OFL (free)"
    type: "variable, weights 100–900"
  mono:
    family: "Geist Mono"
    stack: "Geist Mono, JetBrains Mono, SFMono-Regular, monospace"
    type: "variable"

scale:
  wordmark:   { font: sans, size: "1.4rem",                       weight: 700, tracking: "0.18em", leading: 1,    transform: uppercase }
  display:    { font: sans, size: "clamp(3.2rem, 6.2vw, 5.4rem)", weight: 500, tracking: "-0.02em", leading: 1.04 }
  headline:   { font: sans, size: "clamp(2.2rem, 3.6vw, 3.0rem)", weight: 600, tracking: "-0.015em", leading: 1.08 }
  title:      { font: sans, size: "1.18rem",                      weight: 500, leading: 1.35 }
  body-large: { font: sans, size: "1.18rem",                      weight: 400, leading: 1.65 }
  body:       { font: sans, size: "1.02rem",                      weight: 400, leading: 1.7 }
  small:      { font: sans, size: "0.9rem",                       weight: 400, leading: 1.6 }
  eyebrow:    { font: mono, size: "0.72rem",                      weight: 500, tracking: "0.2em",  transform: uppercase }
  mono:       { font: mono, size: "0.84rem",                      weight: 400, tracking: "0.02em" }
  tagline:    { font: sans, size: "0.92rem",                      weight: 500, tracking: "0.15em", transform: uppercase }
---

# Substrate — Typography (TYPOGRAPHY.md)

One family for everything: **Geist Sans** for all text, **Geist Mono** for scientific
markers and data. Both free, variable, no licensing concern. The single-family choice
keeps a consistent intellectual-grotesque voice across every surface — contrast comes
from weight, not from mixing typefaces.

Geist is premium and modern without the familiarity-tax of Inter (which now reads as
"default SaaS font" because AI tooling defaults to it). Inter remains in the stack as a
fallback only.

## The scale

| Role | Font | Size | Weight | Tracking | Leading | Use |
|---|---|---|---|---|---|---|
| **Wordmark** | Geist | 1.4rem | 700 | 0.18em | 1 | `SYNTROPIC` lockup only — flat, uppercase |
| **Display (h1)** | Geist | clamp(3.2–5.4rem) | 500 | −0.02em | 1.04 | Hero statements, page openers |
| **Headline (h2)** | Geist | clamp(2.2–3.0rem) | 600 | −0.015em | 1.08 | Section anchors |
| **Title (h3)** | Geist | 1.18rem | 500 | — | 1.35 | Component / card headings |
| **Body Large** | Geist | 1.18rem | 400 | — | 1.65 | Editorial / Substack-style lead copy |
| **Body** | Geist | 1.02rem | 400 | — | 1.7 | Default body copy |
| **Small** | Geist | 0.9rem | 400 | — | 1.6 | Captions, fine print |
| **Eyebrow** | Geist Mono | 0.72rem | 500 | 0.2em | — | Uppercase markers above sections |
| **Mono** | Geist Mono | 0.84rem | 400 | 0.02em | — | Data, citations, measurements |
| **Tagline** | Geist | 0.92rem | 500 | 0.15em | — | Uppercase, tracked — tagline framework |

> Sizes are `rem`-based for accessibility (respect user font scaling). `display` and
> `headline` use `clamp()` for fluid responsive scaling — no separate mobile sizes needed.

## Presentation scale (pptxgenjs / Keynote)

For decks, scale up and keep the same family:
- **Hero display:** 96pt+, tracking tight
- **Headline:** 48pt
- **Body:** 24pt
- **Mono / data captions:** 18pt

Deep violet substrate backgrounds, `cream` text, `emission` for single accents only.

## Rules

- **The wordmark is flat.** `SYNTROPIC` is always Geist Bold (700), uppercase, tracked
  0.18em. No 3D, no bevel, no chrome, no drop shadow, no glow. (Spot-UV gloss exists
  only as a physical print finish, never as a digital effect.)
- **One family.** Geist for sans, Geist Mono for mono. No third typeface. Need contrast?
  Use weight (e.g., display 300 vs body 500), not a different face.
- **Display stays sentence case.** h1/h2 are sentence case or initial-cap — never all
  caps. All-caps display reads as energy-drink shouting.
- **Tracked caps stay short.** Eyebrow / tagline / badge are 1–5 words max. Never set a
  sentence in tracked uppercase — it stops being readable past one line.
- **Body needs air.** Body line-height 1.65–1.8; prose width ≤ 68ch. Dark surfaces
  fatigue the eye without vertical breathing room.
- **Mono carries science.** Geist Mono is for data labels, citations (`Babcock et al.,
  2024`), and measurements (`~340nm`) — never for headlines or body (reads as terminal).
- **Variable axis for fine control.** Use the variable weight axis when a specific weight
  helps; ship one variable font, not many static files.

## Loading

**Next.js (recommended):**
```tsx
// app/layout.tsx
import { GeistSans } from "geist/font/sans";
import { GeistMono } from "geist/font/mono";

export default function RootLayout({ children }) {
  return (
    <html lang="en" className={`${GeistSans.variable} ${GeistMono.variable}`}>
      <body>{children}</body>
    </html>
  );
}
```
```css
/* globals.css */
:root { --font-sans: var(--font-geist-sans); --font-mono: var(--font-geist-mono); }
@theme { --font-sans: var(--font-geist-sans); --font-mono: var(--font-geist-mono); }
```

**Static HTML (Google Fonts):**
```html
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Geist:wght@300..700&family=Geist+Mono:wght@400;500&display=swap" rel="stylesheet">
```

**Presentations:** download Geist `.ttf` from vercel.com/font and install locally for
pptxgenjs / Keynote / PowerPoint.

---

*Substrate · TYPOGRAPHY.md · v0.2 · Syntropic Inc. Parent: DESIGN.md.*
