# IntelliFront Design System

The IntelliFront design system is an opinionated, original design language for generating
high-quality redesign code. It is not a framework — it is a set of principles, tokens,
and structural patterns that produce professional-grade output.

Generated code does not need to import this file. These are internalized principles and
reference tokens for Claude to apply when writing HTML/CSS.

---

## Core Philosophy

**Restraint is the differentiator.** Most AI-generated UI fails not because it lacks
complexity but because it lacks judgment — it adds too much, decorates without purpose,
and signals effort rather than taste.

Four constraints that eliminate 80% of AI-design tells:
1. Use whitespace as an active design element, not leftover space
2. Never decorate something that doesn't serve the user's understanding
3. Earn every animation — if you cannot explain why it exists, remove it
4. Typography is hierarchy — size + weight + color must all point the same direction

---

## Absolute Bans

These patterns are forbidden in all generated code. They are the most recognizable
signals of low-effort or AI-generated design:

### Copy bans
- **Emoji in UI copy** — no emoji anywhere in headlines, body text, feature descriptions,
  nav labels, buttons, or as bullet replacements. This is the #1 AI-generation tell.
  No exceptions for "just one rocket emoji" or "just the checkmarks". All of them. Gone.
  If the copy needs an emoji to work, rewrite the copy.

### Visual bans
- `background-clip: text` combined with any gradient (gradient text)
- `border-left: Npx solid` or `border-right: Npx solid` greater than 1px on cards, callouts, or list items
- Decorative glassmorphism: `backdrop-filter: blur()` on elements that don't actually overlap content
- Neon glows: `box-shadow: 0 0 Npx [saturated color]` on buttons, cards, or borders
- Bounce or elastic easing: `cubic-bezier` values that overshoot above 1 or below 0 for position
- Animating layout properties: `width`, `height`, `padding`, `margin`, `top`, `left` — use `transform` only
- Cards nested inside cards
- Same `box-shadow` value applied to every element on the page
- **Gradient mesh orbs on dark backgrounds** — multiple blurred radial-gradient circles floating
  behind content. This is the #1 dark-background slop pattern. It reads as AI-generated within
  2 seconds. If a dark section needs visual interest, use: a subtle SVG noise texture, a single
  very low-opacity tinted surface, or strong typography doing the work.
- **Glow buttons on dark backgrounds** — `box-shadow` with a saturated color spread creating a
  light-emission effect around buttons. Use tinted shadows with low opacity instead:
  `box-shadow: 0 8px 24px oklch(0% 0 0 / 0.3)` — depth, not glow.
- **Saturated gradients as section backgrounds** — purple-to-teal, blue-to-indigo, any multi-hue
  gradient as a primary section background. Single-hue gradients (light to slightly darker same hue)
  are acceptable when used with restraint.
- **font-weight 800 or 900 as a default** — these weights are reserved for brands whose entire
  visual identity requires typographic aggression. For everything else, 600–700 is the ceiling.

### Typography bans
- Inter as a display/heading face
- Syne anywhere
- Oversized italic serif as primary H1 (Fraunces, Playfair Display, Cormorant, Newsreader)
- Uppercase eyebrow chips directly above every section heading as the primary label pattern
- All-caps for body text or feature descriptions
- `letter-spacing` above `0.08em` on body text

### Layout bans
- Every section center-aligned (vary alignment across sections deliberately)
- 3-column icon+heading+2-line card grid as the primary feature presentation
- Hero images that are purely decorative with no product or narrative content
- More than 7 top-level navigation items
- Footer with more than 4 columns of equal-weight links

---

## Color System

### OKLCH — the correct color space

Use `oklch(L% C H)` notation for all color definitions.
- L = lightness (0–100%)
- C = chroma (0–0.4, where 0 = gray and 0.37 = maximum saturation)
- H = hue angle (0–360)

OKLCH is perceptually uniform: equal lightness steps look equal.
Adjust chroma as you approach white or black — high chroma at extreme lightness looks garish.

### Neutral tinting

Neutrals should always be tinted toward the brand hue. Even `oklch(97% 0.006 250)` is
perceptibly different from `oklch(97% 0 0)` and creates subconscious brand cohesion.

Minimum tint: chroma 0.005. Maximum tint for surfaces: chroma 0.015.

### Palette construction

For any site, the palette consists of:

```
Surface (3 levels):
  --surface-0: oklch(97-99% C H)   /* page background */
  --surface-1: oklch(93-96% C H)   /* card background */
  --surface-2: oklch(88-92% C H)   /* sunken / input background */

Text (3 levels):
  --text-primary:   oklch(10-18% C H)   /* headings, body */
  --text-secondary: oklch(38-48% C H)   /* labels, captions */
  --text-muted:     oklch(55-65% C H)   /* placeholders, disabled */

Border (2 levels):
  --border:         oklch(85-90% C H)   /* default borders */
  --border-strong:  oklch(72-80% C H)   /* emphasized borders */

Accent (1 color maximum):
  --accent:         oklch(L% C H)       /* brand action color */
  --accent-hover:   oklch(L-4% C H)    /* slightly darker on hover */
  --accent-text:    oklch(98% 0.005 H) /* text on accent — near white */
```

### Forbidden palette patterns

- Purple-to-blue gradients as primary backgrounds
- Neon accents (chroma > 0.35 on any visible element)
- Pure black `oklch(0% 0 0)` — always tint
- Pure white `oklch(100% 0 0)` — always tint
- Cyan-on-dark as the default developer-tool aesthetic
- More than one true accent color

---

## Typography System

### Font pairing principle

Every project needs exactly two font roles:
- **Display** — used for headings, hero text, large labels. Should carry brand personality.
- **Body** — used for paragraphs, captions, UI text. Should be highly readable at 16–18px.

They should feel intentionally paired — not interchangeable. The display face should feel
slightly *wrong* for body text and vice versa. That tension is the design.

### Type scale

Use a modular scale. Recommended ratio: 1.333 (perfect fourth) for most sites.
For bold editorial: 1.5. For dense UI: 1.25.

```
Base: 17px (1.0625rem)

Scale (1.333 ratio):
  --text-xs:   0.75rem    /* 12px — labels, badges */
  --text-sm:   0.875rem   /* 14px — captions, meta */
  --text-base: 1.0625rem  /* 17px — body */
  --text-md:   1.25rem    /* 20px — large body, intro */
  --text-lg:   1.5rem     /* 24px — small heading */
  --text-xl:   2rem       /* 32px — section heading */
  --text-2xl:  2.625rem   /* 42px — page heading */
  --text-3xl:  clamp(2rem, 4vw, 3rem)     /* hero — fluid, restrained */
  --text-4xl:  clamp(2.5rem, 5vw, 4rem)   /* display — fluid */
```

**On display size:** The default hero should sit at `--text-3xl` — roughly 2.5–3rem.
Larger than that (4rem+, 5rem+, 7vw+) requires a specific creative justification:
agency portfolio, kinetic type hero, luxury fashion. It is not the default.
Most sites that use 7–10vw hero type do so because it looks impressive in isolation —
not because it serves the reader. Hierarchy comes from weight + color contrast, not from
making the headline as large as physically possible.

### Weight strategy

**The weight range is narrower than you think.**

Maximum 3 weights in active use at any time:
- 400 (regular) — body, captions, navigation items
- 500 or 550 (medium) — subheadings, labels, secondary CTAs
- 600 or 700 (semibold/bold) — major headings, primary CTAs

**700 is the ceiling in almost every case.** Weight 800 (extrabold) and 900 (black/heavy)
should appear only when the brand's entire identity is built around typographic aggression —
a condensed sports brand, a bold agency, an editorial publication with a strong opinion.
For SaaS, fintech, healthcare, portfolio, e-commerce, real estate, and AI products:
700 is the maximum. Going to 800 signals effort. Good typography signals confidence.

**Why this matters:** AI-generated sites default to 800–900 weight because heavy type
looks impressive in a screenshot. In context, surrounded by body text and real content,
it reads as shouting. The sites that feel premium — Stripe, Linear, Aman, Compass —
use 500–700 throughout. Their hierarchy comes from size steps and color, not weight alone.

### Letter spacing

Display text (headings): `-0.01em` to `-0.025em`. Tighter than that (`-0.04em`, `-0.05em`)
reads as trying too hard unless the typeface specifically requires it (some condensed faces do).
Body text: never below `0em`. Negative tracking on body text reduces legibility.
All-caps labels: `0.04em` to `0.08em` — optical correction for the removed ascenders.

### Line height

Inverse relationship between font size and line height:
- Display / hero (text-3xl+): 1.1–1.2
- Section headings (text-xl–2xl): 1.2–1.35
- Body text: 1.6–1.7
- Captions / small: 1.4–1.5

### Line length

Body text: max-width of `65–72ch`. Never let body text span full container width.
Headings: no max-width constraint — let them breathe.

---

## Spacing System

### 4pt base

Every spacing value is a multiple of 4px (0.25rem):

```
--space-1:  0.25rem   /* 4px  — tight inline gaps */
--space-2:  0.5rem    /* 8px  — icon-text gaps */
--space-3:  0.75rem   /* 12px — dense component padding */
--space-4:  1rem      /* 16px — standard component padding */
--space-5:  1.25rem   /* 20px */
--space-6:  1.5rem    /* 24px — comfortable padding */
--space-8:  2rem      /* 32px — section components */
--space-10: 2.5rem    /* 40px */
--space-12: 3rem      /* 48px — section internal padding */
--space-16: 4rem      /* 64px — section gaps narrow */
--space-20: 5rem      /* 80px */
--space-24: 6rem      /* 96px — section gaps wide */
--space-32: 8rem      /* 128px — hero vertical padding */
```

### Rhythm principle

**Component gaps < Section gaps < Page gaps.** Never use the same padding value
at all three levels. The hierarchy of breathing room creates hierarchy of content.

### Whitespace as hierarchy

Extra space above a heading reads as more important. Deliberately tight grouping
reads as related. Generous separation between sections reads as conceptual division.
This is not a bug — it is the primary non-typographic tool for hierarchy.

---

## Layout Patterns

### Container

```css
.container {
  width: 100%;
  max-width: 1200px;
  margin-inline: auto;
  padding-inline: clamp(1rem, 4vw, 2rem);
}

.container--text {
  max-width: 680px;
}

.container--wide {
  max-width: 1440px;
}
```

### Grid patterns that work

**Split (50/50 or 55/45):**
```css
.split { display: grid; grid-template-columns: 1fr 1fr; gap: var(--space-12); align-items: center; }
/* mobile: grid-template-columns: 1fr */
```

**Feature strip (text + visual alternating):**
Left-right alternating sections with full-bleed or contained visuals. Not cards.

**Asymmetric (2fr 1fr or 3fr 2fr):**
For hero sections or feature callouts where one side dominates.

**Auto-fit cards (when cards are actually appropriate):**
```css
.card-grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(280px, 1fr)); gap: var(--space-6); }
```

### Layout patterns to avoid

- 3 perfectly equal columns repeated 6+ times (icon-card grid)
- Centered everything — center is a layout decision, not a default
- Full-width text at desktop widths
- Horizontal scroll containers that don't communicate they are scrollable

---

## Motion System

IntelliFront operates on a **motion tier system**. Not all sites need restrained animation.
A luxury real estate site and a creative agency portfolio are different products with
different emotional contracts. Motion should match the brand's energy level — and when the
brand calls for it, motion can be genuinely expressive, cinematic, or wild.

The rule is not "keep it subtle." The rule is **intentionality** — every animation answers
"why does this move?" If the answer is "because it makes the brand feel alive and that is
the point," that is a valid answer.

---

### Motion Tiers

Assign a tier based on the site's brand energy and purpose before choosing animations:

| Tier | Brand profile | Motion character |
|------|--------------|-----------------|
| **1 — Still** | Healthcare, legal, institutional finance | Opacity fades only. No movement. Stillness signals trust. |
| **2 — Grounded** | SaaS dashboards, B2B tools, portfolio | Subtle entrances, minimal hover states. Motion is utility. |
| **3 — Alive** | Consumer SaaS, fintech, e-commerce | Confident transitions, scroll reveals, spring-physics hovers. |
| **4 — Expressive** | Agencies, DTC brands, entertainment, AI products | Kinetic type, magnetic elements, parallax, staggered chaos. |
| **5 — Cinematic** | Creative portfolios, luxury, experimental | Full-page transitions, 3D transforms, physics-based interactions, scroll storytelling. |

When in doubt, go one tier higher than feels safe. Conservative animation is forgettable.

---

### Easing Reference

```css
/* Tier 2+ — clean deceleration, the workhorse */
--ease-out:        cubic-bezier(0.23, 1, 0.32, 1);

/* Tier 3+ — for elements moving across screen */
--ease-in-out:     cubic-bezier(0.77, 0, 0.175, 1);

/* Tier 3+ — hover color/border transitions */
--ease-hover:      cubic-bezier(0.4, 0, 0.2, 1);

/* Tier 3+ — drawers, sidebars, panels */
--ease-drawer:     cubic-bezier(0.32, 0.72, 0, 1);

/* Tier 4+ — has slight overshoot, feels spring-like in CSS */
--ease-spring:     cubic-bezier(0.34, 1.4, 0.64, 1);

/* Tier 5 — dramatic entrance, aggressive deceleration */
--ease-expo:       cubic-bezier(0.16, 1, 0.3, 1);

/* Tier 5 — elastic snap, use on decorative elements only */
--ease-elastic:    cubic-bezier(0.68, -0.6, 0.32, 1.6);
```

Note: `--ease-elastic` overshoots by design. Use on decorative elements (logos, icons, blobs)
where overshoot adds delight. Never on functional UI (modals, dropdowns, form feedback).

`ease-in` is still banned for entrances and UI feedback. It starts slow when the user is
watching most intently. Only acceptable mid-sequence when something is leaving the screen.

---

### Duration Standards

```
Button press feedback:           100–150ms
Tooltip / small popover:         125–200ms
Dropdown / select:               150–250ms
Modal / drawer:                  250–400ms
Scroll reveal (Tier 2–3):        300–500ms
Scroll reveal (Tier 4–5):        600–1000ms
Kinetic type / marquee:          linear, 8–20s loop
Parallax:                        tied to scroll position, no duration
3D rotate / tilt:                physics-based or 300–600ms ease-out
Page transition:                 400–700ms
```

**Exit always faster than entrance.** If entrance is 500ms, exit is 250ms.
This asymmetry mimics how physical objects behave — they take longer to arrive than to leave.

---

### Entrance Patterns by Tier

**Tier 1–2:**
```css
@keyframes fadeIn {
  from { opacity: 0; }
  to   { opacity: 1; }
}
/* Duration: 300ms ease-out */
```

**Tier 3:**
```css
@keyframes fadeUp {
  from { opacity: 0; transform: translateY(12px); }
  to   { opacity: 1; transform: translateY(0); }
}
/* Duration: 400ms --ease-out, staggered */
```

**Tier 4 — dramatic entrance:**
```css
@keyframes slideReveal {
  from { opacity: 0; transform: translateY(40px) scale(0.94); }
  to   { opacity: 1; transform: translateY(0) scale(1); }
}
/* Duration: 700ms --ease-expo */
```

**Tier 5 — cinematic:**
```css
/* Clip-path reveal — text or image slides in from below a mask */
@keyframes clipReveal {
  from { clip-path: inset(0 0 100% 0); }
  to   { clip-path: inset(0 0 0% 0); }
}
/* Duration: 800–1200ms --ease-expo, stagger heavily */

/* 3D flip entrance */
@keyframes flipIn {
  from { opacity: 0; transform: perspective(800px) rotateX(-30deg) translateY(20px); }
  to   { opacity: 1; transform: perspective(800px) rotateX(0) translateY(0); }
}
```

Never animate from `scale(0)`. Always from at minimum `scale(0.9)`.

---

### Expressive Patterns (Tier 4–5)

These are encouraged when the site's brand energy calls for them. They are not slop —
they are intentional craft. The difference between slop and expression is purpose.

**Kinetic marquee / ticker:**
```css
@keyframes marquee {
  from { transform: translateX(0); }
  to   { transform: translateX(-50%); }
}
.marquee-track {
  display: flex;
  width: max-content;
  animation: marquee 18s linear infinite;
}
/* Pause on hover: .marquee-track:hover { animation-play-state: paused; } */
```

**Magnetic button effect (CSS approximation, use JS for true magnetic):**
```css
.magnetic {
  transition: transform 300ms cubic-bezier(0.34, 1.4, 0.64, 1);
}
/* JS: track mousemove, apply translateX/Y proportional to cursor distance */
```

**Text scramble / glitch (Tier 5, agencies/games/experimental):**
```css
@keyframes glitch {
  0%, 100% { clip-path: inset(0 0 100% 0); transform: translateX(0); }
  20%       { clip-path: inset(33% 0 33% 0); transform: translateX(-4px); }
  40%       { clip-path: inset(66% 0 0 0);   transform: translateX(4px); }
  60%       { clip-path: inset(0 0 66% 0);   transform: translateX(-2px); }
  80%       { clip-path: inset(0 0 33% 0);   transform: translateX(0); }
}
```

**Scroll-linked parallax (Tier 4–5):**
```css
/* Use @scroll-timeline or JS IntersectionObserver + CSS custom properties */
/* Never use scroll listeners on the main thread for parallax */
.parallax-layer {
  will-change: transform;
  /* transform updated via JS: element.style.transform = `translateY(${offset}px)` */
}
```

**3D card tilt (Tier 4–5, portfolio, luxury, agency):**
```js
// On mousemove over card:
const rect = card.getBoundingClientRect();
const x = (e.clientX - rect.left) / rect.width  - 0.5;
const y = (e.clientY - rect.top)  / rect.height - 0.5;
card.style.transform = `
  perspective(800px)
  rotateY(${x * 12}deg)
  rotateX(${-y * 12}deg)
  scale(1.02)
`;
```

**Blob / fluid shape animation (Tier 4, avoid if it's just decoration):**
```css
@keyframes blobMorph {
  0%, 100% { border-radius: 60% 40% 30% 70% / 60% 30% 70% 40%; }
  25%       { border-radius: 30% 60% 70% 40% / 50% 60% 30% 60%; }
  50%       { border-radius: 50% 60% 30% 70% / 40% 50% 60% 30%; }
  75%       { border-radius: 40% 30% 60% 50% / 60% 40% 50% 70%; }
}
/* Only use when the blob is part of the visual identity, not generic decoration */
```

**Stagger at scale (Tier 4–5):**
```css
/* Use CSS custom property for index-based delay */
.item { animation-delay: calc(var(--i) * 80ms); }
/* Set --i via inline style in HTML: <div class="item" style="--i:0"> */
/* No cap on stagger count — but keep each delay ≤120ms for large lists */
```

---

### What Stays Banned Regardless of Tier

Even Tier 5 cinematic sites must not use these:
- Animating `width`, `height`, `margin`, `padding`, `top`, `left` — use `transform` + `clip-path`
- `ease-in` on any entrance or feedback animation
- Auto-playing video or looping audio without user initiation
- Hover glow effects (`box-shadow: 0 0 Npx saturated-color`) — this is distinct from expressive lighting
- Animations on every scroll event without `requestAnimationFrame` throttling
- Removing `:focus-visible` without a replacement

---

### Button Press Feedback (Mandatory at All Tiers)

```css
button, a.btn, [role="button"] {
  transition: transform 120ms cubic-bezier(0.23, 1, 0.32, 1),
              background-color 150ms cubic-bezier(0.4, 0, 0.2, 1);
}
button:active, a.btn:active {
  transform: scale(0.97);
}
```

At Tier 5, can become more theatrical:
```css
button:active {
  transform: scale(0.93) rotate(-1deg);
  transition-duration: 80ms;
}
```

---

### Accessibility (Non-Negotiable)

```css
@media (prefers-reduced-motion: reduce) {
  *, ::before, ::after {
    animation-duration: 0.01ms !important;
    animation-iteration-count: 1 !important;
    transition-duration: 0.01ms !important;
    scroll-behavior: auto !important;
  }
}
```

Reduced motion means no movement-based animations — but opacity and color transitions
that aid comprehension can remain. Keep fade-ins. Remove slides, rotates, and scales.

---

## Interactive States (Mandatory)

Every generated component must include:

| State | Requirement |
|-------|-------------|
| `:hover` | Visual change — background, border, or transform |
| `:active` | `transform: scale(0.97)` minimum |
| `:focus-visible` | Visible focus ring — `outline: 2px solid var(--accent); outline-offset: 2px` |
| Loading | Skeleton or spinner where async operations exist |
| Empty | Instructive empty state — not just "nothing here" |
| Error | Inline error message with specific guidance |

Never suppress `:focus-visible` without replacing it with an equivalent visible indicator.

---

## Mobile Rules

- Mobile-first: start with single-column, 375px base
- Hero sections: use `min-height: 100svh` not `height: 100vh` (avoids iOS Safari jump)
- Touch targets: minimum 44×44px (use `padding` to expand visual elements)
- Body text: minimum 16px on mobile (17px preferred)
- Never use `overflow: hidden` on `body` — it disables scrolling on iOS
- Multi-column grids: always collapse to single column below 640px
- Navigation: hamburger menu is fine — just make it actually work (focus trap, scroll lock)
