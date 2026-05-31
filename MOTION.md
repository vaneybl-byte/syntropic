---
name: Substrate Motion & Interaction
description: Motion language, transitions, signature animations, and UI/UX craft for Syntropic. Cathedral-quiet, anti-stimulant.
parent: DESIGN.md

libraries:
  primary: "Motion (motion/react) — MIT, declarative, AnimatePresence"
  scroll:  "Lenis — restrained smooth-scroll only"
  complex: "GSAP — single scroll-driven science explainer only"
  skip-for-mvp: ["Theatre.js", "Rive", "Lottie"]

tokens:
  ease:
    substrate:  "cubic-bezier(0.22, 1, 0.36, 1)"   # default — slow, heavy ease-out
    considered: "cubic-bezier(0.16, 1, 0.3, 1)"     # slightly sharper, UI micro-states
  duration:
    quick:    "200ms"   # hover, small state changes
    base:     "400ms"   # standard transitions
    slow:     "700ms"   # page / section entries
    ambient:  "1200ms"  # large atmospheric reveals, glow breathing
  spring:
    substrate: { stiffness: 120, damping: 30 }   # default — no overshoot
    heavy:     { stiffness: 80,  damping: 32 }   # large elements
---

# Substrate — Motion & Interaction (MOTION.md)

Motion reinforces the anti-stimulant thesis. It is **slow, heavy, considered, and
finite** — it guides attention, never demands it. The test for any animation:
**would it belong on an energy-drink site?** If yes, it's wrong here.

Library stack: **Motion** (`motion/react`) for everything; **Lenis** for gentle
smooth-scroll; **GSAP** only for one complex science explainer. Skip Lottie/Rive/Theatre
for MVP.

## Motion tokens

```css
:root {
  --ease-substrate:  cubic-bezier(0.22, 1, 0.36, 1);  /* default, heavy ease-out */
  --ease-considered: cubic-bezier(0.16, 1, 0.3, 1);

  --dur-quick:   200ms;
  --dur-base:    400ms;
  --dur-slow:    700ms;
  --dur-ambient: 1200ms;
}
```
```ts
// Motion spring presets
export const springSubstrate = { type: "spring", stiffness: 120, damping: 30 };
export const springHeavy     = { type: "spring", stiffness: 80,  damping: 32 };
```

## Core transition recipes

| Interaction | Recipe |
|---|---|
| Page entry | fade + `y: 8 → 0`, `--dur-slow`, `--ease-substrate`, once |
| Section scroll-reveal | opacity + `y: 12 → 0`, `--dur-base`/`slow`, once, viewport threshold ~0.2 |
| Staggered children | each child +60ms after previous |
| Hover lift (card/button) | `y: -2` to `-4px`, `--dur-quick`. No scale-bounce. |
| Modal open | fade + scale `0.98 → 1`, `--dur-base` |
| Nav link hover | color → `emission-core`, `--dur-quick` |
| Route transition | fade + subtle scale `0.99 → 1`, ~`--dur-base` |

## Signature animations (on-brand, distinctive)

These are the moves that make a Syntropic site feel like Syntropic — used sparingly,
each tied to the brand's "light from within" idea.

**1. Mark breathing glow.** The Penrose mark's glow opacity slowly breathes
`0.7 → 1 → 0.7` over `--dur-ambient × 3` (~3.6s), `--ease-substrate`, infinite. This is
the brand's one permitted perpetual animation — calm, like a slow pulse. Reduced-motion:
static at full glow.
```ts
<motion.div
  animate={{ opacity: [0.7, 1, 0.7] }}
  transition={{ duration: 3.6, ease: [0.22,1,0.36,1], repeat: Infinity }}
/>
```

**2. Emission hover bloom.** On hover, CTAs and the mark gain a soft expanding glow
(box-shadow `0 0 0` → `0 0 32px emission-edge/0.22`), `--dur-base`. A slow bloom, never
a flash.

**3. Wordmark assembly.** On first load, `SYNTROPIC` letters fade in with a 40ms stagger
while tracking expands from `0.05em → 0.18em`. Premium reveal, once. Reduced-motion:
appear instantly at final tracking.

**4. Scroll-reveal cascade.** Section content rises + fades as it enters viewport, with
60ms stagger between elements. The page "develops" like a photograph as you scroll —
quiet, sequential.

**5. Coherence field drift.** Background impossible-objects pattern drifts very slowly
(60–90s loop) or shifts subtly with scroll (single-layer, gentle). The "field" feels
alive but never busy. Reduced-motion: static.

**6. Liquid / UV bloom.** For product moments, the violet liquid or UV glow "fills in"
on reveal — a radial brightness bloom from center, `--dur-slow`. Use only at key product
beats, not routinely.

**7. Stat count-up.** Numbers (e.g., "20%") count up when scrolled into view, `--dur-slow`,
ease-out, once. Pairs well with mono type for data.

> Optional, use with caution: **cursor-aware glow** — a faint radial emission follows
> the cursor on dark hero sections, like a flashlight in a dark room. Powerful but easy
> to overdo; if it reads as gimmicky or "gaming," cut it. Never on content-dense pages.

## UI/UX craft — the invisible details

The polish layer. These small things separate "premium" from "template."

- **Focus rings.** Keyboard focus → 2px `hairline-strong` outline, 3px offset, never
  removed. Visible focus is non-negotiable for accessibility.
- **Selection color.** `::selection { background: emission-edge/0.3; color: cream; }` —
  even text selection is on-brand.
- **Hover states everywhere.** Every interactive element has a deliberate hover (lift,
  glow, or color shift). Nothing interactive is static on hover.
- **Loading states.** Skeletons in `substrate-veil` with a slow shimmer sweep
  (`--dur-ambient`, `--ease-substrate`) — not a spinner. Calm, not anxious.
- **Empty states.** A quiet Penrose mark + one line of `text-muted` copy. Never a
  cartoon illustration.
- **Smooth scroll.** Lenis at gentle settings (lerp ~0.1). Never aggressive
  scroll-hijacking; the page should still feel native.
- **Sticky nav.** Transparent at top; on scroll, background fades to `substrate-base`
  ~85% with a bottom `hairline`, `--dur-base`. (Solid alpha, not backdrop-blur, to honor
  the No-Glass rule.)
- **Scroll progress.** Optional thin (2px) `emission-edge` bar at top showing read
  progress on long editorial pages.
- **Image reveal.** Images fade + scale `1.02 → 1` as they enter viewport — a settle,
  not a zoom.
- **Cursor.** Default system cursor. No custom cursor gimmicks (reads as gaming/agency-
  reel, off-brand).
- **Tap targets.** Minimum 44×44px on touch. Generous spacing between actions.
- **No layout shift.** Reserve space for images/fonts; target CLS < 0.1.

## Forbidden patterns

Stimulant-signals — categorically banned:

- ❌ Bouncy / overshoot spring entries
- ❌ Perpetual pulse loops on inactive elements (the mark's slow breathing is the *only*
  permitted perpetual motion)
- ❌ Magnetic hover (element chases cursor)
- ❌ Multi-layer parallax (single subtle layer is the max)
- ❌ Neon flashes, strobe, flicker, glow trails
- ❌ Particle systems / floating sparkle fields
- ❌ Scale-bounce on hover (`scale: 1.1` + overshoot)
- ❌ Auto-advancing carousels
- ❌ Looping background video with visible motion (static or very-slow-pan only)
- ❌ Custom cursors / cursor gimmicks

## Accessibility (mandatory)

```css
@media (prefers-reduced-motion: reduce) {
  *, *::before, *::after {
    animation-duration: 0.01ms !important;
    animation-iteration-count: 1 !important;
    transition-duration: 0.01ms !important;
    scroll-behavior: auto !important;
  }
}
```
With Motion, use `useReducedMotion()` to swap transforms for instant opacity. When
reduced-motion is on: disable Lenis, freeze the mark glow at full, make the coherence
field static, drop all transforms to opacity-only. Always test in OS settings.

## References (study these)

Restrained premium motion: Apple product pages, Aesop, A. Lange & Söhne, Audemars Piguet,
Polestar, Lucid, Cymbiotika.
Scientific-illustration motion (for diagrams): ciechanow.ski, ncase.me, distill.pub,
Quanta interactives, Refik Anadol motion studies.

---

*Substrate · MOTION.md · v0.2 · Syntropic Inc. Parent: DESIGN.md.*
