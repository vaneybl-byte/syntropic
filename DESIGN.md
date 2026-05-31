---
name: Substrate
description: >
  Design system for Syntropic — the world's first coherence soda. Deep violet
  substrate ground, cyan-violet emission glow, Penrose impossible-triangle mark.
  Cathedral-quiet, anti-stimulant, premium intellectual. Use for building Syntropic
  websites, landing pages, and presentations. Companion files: TYPOGRAPHY.md, MOTION.md.

# Tokens below are the source of truth. OKLCH is canonical (Tailwind v4 @theme,
# modern CSS). HEX is provided for tools that need it (pptxgenjs presentations,
# Figma, older pipelines). The two are matched to the locked product renders.

colors:
  # Substrate — the violet ground. Page backgrounds, can body, raised surfaces.
  substrate-rise:  { oklch: "oklch(27% 0.094 293)", hex: "#2A1A50" }   # top of gradient, hero panels
  substrate-base:  { oklch: "oklch(21% 0.071 292)", hex: "#1A0F35" }   # DEFAULT page ground
  substrate-veil:  { oklch: "oklch(19% 0.062 294)", hex: "#160C2C" }   # cards, panels
  substrate-deep:  { oklch: "oklch(17% 0.063 288)", hex: "#0F0828" }   # inset, footer, modal bg

  # Void — deeper than substrate, away from product. Hero backdrops, edges.
  void-mid:  { oklch: "oklch(16% 0.049 287)", hex: "#0C0820" }
  void-deep: { oklch: "oklch(13% 0.038 291)", hex: "#070414" }

  # Emission — the brand signal. Cyan-violet glow (tryptophan UV fluorescence).
  emission-core:  { oklch: "oklch(88% 0.072 233)", hex: "#A8E0FF" }   # brightest, hover/active, mark core
  emission-edge:  { oklch: "oklch(60% 0.194 285)", hex: "#7B68EE" }   # violet, default CTA fill, links
  emission-soft:  { oklch: "oklch(75% 0.072 230)", hex: "#7FB8D4" }   # muted cyan, subtitle, accents
  emission-trace: { oklch: "oklch(81% 0.057 300)", hex: "#C5B8E0" }   # pattern, faint embossing

  # Text
  champagne:  { oklch: "oklch(100% 0 0)",      hex: "#FFFFFF" }   # wordmark, brand-bearing white only
  cream:      { oklch: "oklch(94% 0.032 91)",  hex: "#F2EAD3" }   # headlines on substrate
  text-warm:  { oklch: "oklch(87% 0.02 85)",   hex: "#D9D2C4" }   # default body copy
  text-muted: { oklch: "oklch(67% 0.019 85)",  hex: "#9A9488" }   # captions, metadata, eyebrows
  text-faint: { oklch: "oklch(51% 0.015 82)",  hex: "#6A655C" }   # disabled, subdued labels

  # Awakening — warm system. Founder's Drop + book contexts ONLY. Never on primary surfaces.
  awakening-core: { oklch: "oklch(70% 0.195 41)", hex: "#FF6B2C" }
  awakening-deep: { oklch: "oklch(61% 0.214 32)", hex: "#E83A1A" }

  # Hairlines / borders (with alpha)
  hairline:        { value: "oklch(60% 0.12 285 / 0.30)" }   # default rule on substrate
  hairline-strong: { value: "oklch(74% 0.14 285 / 0.55)" }   # active rule, focus outline
  hairline-cream:  { value: "oklch(87% 0.02 85 / 0.18)" }    # neutral rule in content blocks

spacing:   # 8pt scale
  xs:   "8px"
  sm:   "16px"
  md:   "24px"
  lg:   "32px"
  xl:   "48px"
  "2xl": "80px"
  "3xl": "112px"
  "4xl": "160px"

radius:
  none: "0"
  xs:   "2px"
  sm:   "4px"
  md:   "8px"
  lg:   "12px"
  pill: "999px"

layout:
  content-max:  "1280px"   # standard section container
  prose-max:    "68ch"     # long-form reading width
  section-pad-y: "96px"    # desktop vertical section rhythm (2xl+)
  gutter:       "24px"     # grid gutter
  breakpoints:  { sm: "640px", md: "768px", lg: "1024px", xl: "1280px" }

icons:
  family: "Phosphor"
  package: "@phosphor-icons/react"
  default-weight: "light"   # regular for standard UI, bold/fill for emphasis only
---

# Substrate — Core (DESIGN.md)

Design system for **Syntropic**. This file is the visual foundation: color, surfaces,
spacing, layout, components, icons. Typography lives in `TYPOGRAPHY.md`; motion and
interaction craft in `MOTION.md`.

## North star

**Light from within.** Syntropic is the anti-stimulant coherence soda. The visual
register is the opposite of an energy drink: stillness instead of speed, depth instead
of noise, self-emission instead of reflected shine. Deep violet substrate, a single
cyan-violet glow, cathedral-quiet composition. Every surface should feel calm,
intentional, and premium — closer to Aesop, Cymbiotika, and an Apple keynote than to
anything on a gas-station shelf.

The deep violet is not a mood choice — it is the human-visible color of the brand's
mechanism (tryptophan UV fluorescence in microtubules). That's the only "why" you need
to remember: **the color is the mechanism.**

## Color system

Three layers, by role:

- **Substrate** — the violet ground. Page backgrounds, cards, raised panels. Use
  `substrate-base` as the default page ground, `substrate-veil` for cards,
  `substrate-rise` for hero/elevated panels, `substrate-deep` for inset/footer/modal.
- **Void** — deeper, less saturated. The space *around* the product in hero shots and
  full-bleed backdrops. `void-deep` at edges, `void-mid` as backdrop fade.
- **Emission** — the single brand signal. Cyan-violet glow. `emission-edge` (violet)
  for default CTAs and links; `emission-core` (cyan-white) for hover/active and the
  Penrose mark's glow; `emission-soft` for muted accents and subtitles; `emission-trace`
  for the impossible-objects pattern.

Text runs warm: `cream` for headlines, `text-warm` for body, `text-muted` for captions.
Pure `champagne` white is reserved for the wordmark and brand-bearing moments.

### Color rules

- **The emission carries brand.** If one accent must represent Syntropic, it's the
  cyan-violet emission — not white, not cream.
- **Substrate stays violet.** Hue lives at ~285–294. If a value reads "almost blue" or
  "almost black," pull it back into violet.
- **No pure black.** The deepest surface is `void-deep` (#070414), warm violet-black.
  Pure `#000000` reads dead; substrate is alive.
- **No max-saturation neon.** Emission caps at the tokens above — luminous, never
  poster-paint. Real UV fluorescence has soft falloff.
- **Awakening is reserved.** Warm orange (`awakening-*`) appears only on Founder's Drop
  and book-aligned surfaces. Never on the primary product, never as default decoration.
- **OKLCH is canonical; HEX is the export.** Build sites in OKLCH (Tailwind v4 `@theme`).
  Use HEX for presentations (pptxgenjs), Figma, and any tool without OKLCH support.

## Surfaces, elevation, material

Depth comes from **value contrast and hairlines**, almost never from drop shadows.

- Layer surfaces by value: `void-deep` → `substrate-deep` → `substrate-base` →
  `substrate-veil` → `substrate-rise`. Stepping up one level = "this is raised."
- **Hairline first.** Use a 1px `hairline` border before reaching for any shadow.
- **Self-emission carries depth.** The Penrose mark and emission CTAs glow from within —
  they're their own light source. Light comes *from* them, not *onto* them.
- **Matte, not glass.** Surfaces are mineral and solid. No glassmorphism / frosted blur.
  The only translucency allowed is photographic (real liquid, real haze) — never UI.
- **Shadows, when used:** modals only — `0 24px 60px oklch(7% 0.04 285 / 0.45)` plus a
  `hairline-strong` ring. Cards rest on borders + value contrast, not shadows.
- **Emission glow (sparingly):** `0 0 32px oklch(60% 0.194 285 / 0.22)` around the mark
  or an active CTA on hover. See `MOTION.md` for how it animates.

## Layout & grid

- **Section container:** max-width `1280px`, centered, with responsive side padding
  (24px mobile → 48px+ desktop).
- **Vertical rhythm:** sections get `96px` top/bottom padding on desktop (`2xl` token),
  scaling down to `48px` on mobile. Generous breathing room is part of the brand.
- **Prose width:** long-form text caps at `68ch` for readability on dark surfaces.
- **Grid:** 12-column with `24px` gutter for complex layouts; most marketing sections
  are better as simple 1–3 column flex/grid with large gaps.
- **Hero composition:** split (≈55/45 type/product) on desktop, per the locked hero
  shots. Centered layouts are permitted only in vertical/mobile contexts.
- **Negative space is a feature.** When unsure, add space. The brand breathes.

## Components

Read tokens, never hand-type values.

**Button — primary:** `emission-edge` fill, `substrate-deep` text, `radius-xs` (2px),
padding `16px 38px`, min-height 54px, tagline-style type (see TYPOGRAPHY.md). Hover →
`emission-core` fill + subtle emission glow.

**Button — secondary:** transparent fill, `champagne` text, `hairline-strong` 1px
border, same sizing. Hover → border brightens.

**Button — ghost:** transparent, `emission-soft` text, no border. Inline / low-emphasis.

**Card:** `substrate-veil` bg, `hairline` border, `radius-md` (8px), `32px` padding.
Flat — no drop shadow. Min `24px` gap between cards; never nest cards.

**Card — elevated:** `substrate-rise` bg, `hairline-strong` border. Hero/featured blocks.

**Input:** `substrate-deep` bg, `cream` text, `hairline` border, `radius-sm` (4px),
`16px 18px` padding. Focus → `hairline-strong` border + emission focus ring (MOTION.md).
Label: mono eyebrow style above the field, `text-muted`.

**Badge — emission:** `emission-edge` at 18% alpha bg, `emission-core` text,
`hairline-strong` border, `radius-pill`, `6px 14px`, mono eyebrow type. For "NEW",
"FOUNDER'S DROP", "LIVE".

**Badge — awakening:** `awakening-core` at 16% alpha bg + text, pill. Founder's Drop /
book contexts only.

**Nav link:** `cream` text, body type. Hover → `emission-core`, 200ms. Sticky nav: on
scroll, background becomes `substrate-base` at ~85% with a bottom `hairline` (no blur —
use solid alpha, not backdrop-filter, to honor the No-Glass rule, or a very light blur
if the team accepts it; default is solid).

**Section scaffold:** optional mono eyebrow → headline (h2) → subhead (body-large,
`text-warm`, max 65ch) → content. See TYPOGRAPHY.md for the type tokens.

**Brand lockup:** Penrose mark + wordmark, `24px` gap. Mark sits above or beside the
wordmark — never integrated as a letter (there is no "A" in SYNTROPIC). Small Penrose
icon may sit at the end of a tagline as a signature mark.

## Icons

**Phosphor Icons** (`@phosphor-icons/react`) is the single icon family. MIT-licensed,
1,512 glyphs × 6 weights, strong science coverage. Never mix in a second family.

- **Default weight: Light.** Regular for standard UI. Bold/Fill only for small sizes
  (<20px) or genuine emphasis. Default is quiet.
- **Color via token** (`currentColor` or an explicit emission/text token). Never
  hard-code.
- **Decorative icons get `aria-hidden`;** meaningful icons get a label.
- **Brand-domain vocabulary:** `atom, brain, flask, test-tube, microscope, dna,
  waveform, pulse, function, orbit` (science); `cube, cube-transparent, hexagon,
  infinity, circles-three, triangle` (geometry); `drop, drop-half, leaf, plant`
  (product); `lightning-slash` (anti-stimulant — struck-through bolt, brand-perfect),
  `moon, sun-dim, eye, sparkle` (ambient — `sparkle` small/accent only, never decoration).
- **Avoid:** Lucide as primary (AI-default), wellness "leaf-with-smile" sets, mixing
  families, Bold as default weight.

Install: `npm i @phosphor-icons/react` → `import { Atom } from "@phosphor-icons/react"`
→ `<Atom size={24} weight="light" />`. Vanilla: `unpkg.com/@phosphor-icons/web`.
Figma: "Phosphor Icons" plugin.

## Do / Do not

**Do**
- Use deep violet substrate as the ground; cyan-violet emission as the single accent.
- Layer depth with value + hairlines; keep surfaces matte.
- Breathe — generous spacing, generous prose width, negative space.
- Read tokens for every value; build in OKLCH, export HEX for presentations.
- Keep the wordmark flat; keep the mark separate from the wordmark.

**Do not**
- ❌ Pure black `#000000` (use `void-deep`).
- ❌ Glassmorphism / frosted backdrop blur.
- ❌ Sci-fi clutter: sparkles, grids, speed lines, particles, holograms, neon.
- ❌ Multi-color gradients / rainbow / "aurora" / AI-default purple-blue mush.
  (Substrate violet is principled and allowed; ungrounded purple gradients are not.)
- ❌ Drop shadows on cards (borders + value contrast instead).
- ❌ Awakening warm on primary surfaces.
- ❌ Mixing icon families; Lucide as primary.
- ❌ Hand-typed color/spacing values that bypass the tokens.

## Tailwind v4 setup

```css
/* globals.css */
@import "tailwindcss";

@theme {
  --color-substrate-rise: oklch(27% 0.094 293);
  --color-substrate-base: oklch(21% 0.071 292);
  --color-substrate-veil: oklch(19% 0.062 294);
  --color-substrate-deep: oklch(17% 0.063 288);
  --color-void-mid:  oklch(16% 0.049 287);
  --color-void-deep: oklch(13% 0.038 291);
  --color-emission-core:  oklch(88% 0.072 233);
  --color-emission-edge:  oklch(60% 0.194 285);
  --color-emission-soft:  oklch(75% 0.072 230);
  --color-emission-trace: oklch(81% 0.057 300);
  --color-cream:      oklch(94% 0.032 91);
  --color-text-warm:  oklch(87% 0.02 85);
  --color-text-muted: oklch(67% 0.019 85);
  --color-awakening-core: oklch(70% 0.195 41);

  --radius-xs: 2px; --radius-sm: 4px; --radius-md: 8px; --radius-lg: 12px;
  --spacing-2xl: 80px; --spacing-3xl: 112px; --spacing-4xl: 160px;
}
```

Then use `bg-substrate-base`, `text-cream`, `text-emission-soft`, `border-emission-edge`,
etc. directly.

---

*Substrate · DESIGN.md · v0.2 · Syntropic Inc. Companion files: TYPOGRAPHY.md, MOTION.md.*
