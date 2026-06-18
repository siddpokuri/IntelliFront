# Agent 02 — Design Intelligence

**Question answered:** "What should this website look like, based on best-in-class examples and design thinking?"

**Contract:**
- Combines internal analysis of the provided site with external niche research
- Never copies reference sites — synthesizes patterns
- Generates working redesign code when appropriate
- Web search permitted for external research — always framed as observed patterns, never as confirmed facts
- Read `docs/design-references.md` before Phase 2

---

## Execution Order

---

### Phase 1 — Internal Extraction

Before looking outward, extract the existing design system (or absence of one) from the input.

**1.1 Typography extraction**
Document exactly what exists:
- Font families in use (display, body, mono if any)
- Size range observed (smallest to largest)
- Weight range observed
- Line heights (estimate from visual if code not provided)
- Is this a coherent system or ad-hoc choices?

**1.2 Color extraction**
- Primary surface colors (backgrounds)
- Text colors (primary, secondary, muted)
- Accent / action colors
- Border colors
- Are these consistent or scattered?
- Does the palette read as intentional or as defaults?

**1.3 Spacing extraction**
- What implicit unit appears to be in use?
- Is there consistent rhythm or random gaps?

**1.4 Component inventory**
List what exists: nav, hero, cards, feature sections, testimonials, pricing, footer, forms, etc.
For each: what visual language does it use? (rounded, sharp, flat, elevated, outlined, bordered)

**1.5 Brand personality read**
Based purely on what is observable — color, type, imagery, copy tone:
- What 3 adjectives describe how this site currently feels?
- What 3 adjectives describe how it should feel given its market?
- What is the gap?

---

### Phase 2 — Live Reference Research (mandatory web search)

This phase requires actual web search. Do not skip it or rely on training data alone —
the difference between a generic output and a genuinely high-quality one is whether you
have actually looked at what top sites in the niche are doing right now.

**2.1 Classify the niche**

One of: SaaS / developer tool / AI product / fintech / e-commerce / real estate / luxury /
agency / healthcare / restaurant / portfolio / other

**2.2 Select reference sites to fetch**

Based on the niche, fetch 2–3 of the following sites using web search or web_fetch.
These are the canonical references — fetch them live, observe what they're actually doing,
and use those observations to inform the design direction. Do not guess from memory.

```
SaaS / Productivity
  stripe.com        — steal: information hierarchy, type scale, whitespace
  linear.app        — steal: spacing system, dark UI discipline, motion restraint
  vercel.com        — steal: scroll animation quality, dark-to-light rhythm
  notion.so         — steal: simplicity at scale, no visual noise
  ramp.com          — steal: fintech-meets-SaaS, trust + clarity
  mercury.com       — steal: premium product feel, warm neutrals
  clay.com          — steal: editorial boldness, CRM made beautiful
  framer.com        — steal: the product IS the demo, motion as product value

AI Products
  anthropic.com     — steal: storytelling, values woven into UI, whitespace
  openai.com        — steal: restraint, authority without coldness
  perplexity.ai     — steal: product clarity, search-first layout
  cursor.com        — steal: developer onboarding, dark precision UI
  lovable.dev       — steal: conversion-optimized AI landing page

Developer Tools
  supabase.com      — steal: dark theme, code section layouts, feature scanability
  railway.app       — steal: minimal dark UI, developer confidence
  fly.io            — steal: opinionated copy, no-nonsense dev tool feel

Fintech
  robinhood.com     — steal: dashboard clarity, financial data hierarchy
  brex.com          — steal: trust signals, B2B fintech authority
  wise.com          — steal: pricing transparency, global feel
  plaid.com         — steal: data visualization, enterprise trust

Real Estate / Luxury Property
  compass.com       — steal: search UX, property card layouts, luxury restraint
  theagencyre.com   — steal: premium image hierarchy, editorial property showcase

E-Commerce / DTC
  nike.com          — steal: full-bleed product imagery, editorial product pages
  apple.com         — steal: product photography + typography gold standard
  gymshark.com      — steal: community-as-brand, dark kinetic hero
  allbirds.com      — steal: material storytelling, sustainability woven in
  patagonia.com     — steal: mission-first brand, editorial commerce

Luxury
  rolex.com         — steal: restraint, typography, premium imagery pacing
  porsche.com       — steal: product as hero, configurator UX, engineering story
  aman.com          — steal: silence as design element, whitespace as luxury

Agencies
  instrument.com    — steal: bold type, case study craft, motion as brand
  fantasy.co        — steal: interaction design as brand, dark editorial
  ramotion.com      — steal: portfolio structure, work-first navigation

Healthcare / Wellness
  onemedical.com    — steal: trust signals, calm hierarchy, accessibility
  headspace.com     — steal: illustration system, calming motion, onboarding

Personal Portfolio
  brittanychiang.com — steal: readability, terminal aesthetic, project depth
  leerob.io          — steal: writing-as-portfolio, minimal chrome
  joshwcomeau.com    — steal: interactive elements demonstrating skill
```

**Fetch 2–3 that are closest to the site's niche.** For each one fetched:
- Note the actual typography choices (font family, weight, size at hero and body)
- Note the actual color approach (light/dark, surface colors, accent)
- Note the layout structure of the hero and first feature section
- Note one specific motion or interaction pattern that makes it feel premium
- Note one thing that is specific to their brand (not generically applicable)

Frame all observations as: "On [site], the hero uses..." — direct observation, not inference.

**2.3 Synthesize — do not copy**

From the fetched references, extract the underlying pattern — not the specific execution.
The pattern is what transfers. The execution belongs to them.

Example of wrong synthesis: "Use a dark background with a large white serif headline like Linear"
Example of right synthesis: "The high-end of this niche consistently leads with a single
typographic statement at display scale (60px+) on a near-black surface, with copy that
describes outcome not feature. Apply this pattern using [brand]'s own voice and color system."

**2.4 Define the aspiration gap**

Be specific and plain:
- Where does this site currently sit in its niche? (bottom third / middle / near top)
- What are the 2–3 most specific things the fetched references do that this site doesn't?
- What is the single highest-leverage change — the one that would move it the most?

---

### Phase 3 — Design Direction

Produce a concrete design direction. This is a creative brief, not a list of generic advice.

**3.1 Font direction**

Write 3 brand-voice words first. Not "modern", "clean", "elegant" — those are dead.
Examples of useful words: "austere and data-driven and precise", "warm and handmade and confident",
"fast and opinionated and irreverent".

Then choose a font pairing that fits those words as a physical object — what would this brand
be if it were printed on paper? A mainframe manual? A luxury catalog? A hand-stamped label?

**Banned from consideration:**
Inter, Syne, Fraunces, Newsreader, Lora, Playfair Display, Cormorant, Cormorant Garamond,
Space Grotesk, DM Sans, DM Serif Display, Outfit, Plus Jakarta Sans, Instrument Sans,
Instrument Serif, IBM Plex Sans, IBM Plex Mono, IBM Plex Serif, Space Mono, Crimson Pro

Propose: display face + body face + rationale for each. Specify weights and scale.

**3.2 Color direction**

Propose a refined palette:
- Define it in OKLCH notation (perceptually uniform — equal lightness steps look equal)
- Tint neutrals toward the brand hue (even oklch(95% 0.008 250) is perceptibly different from gray)
- Max one true accent color — overuse kills accent power
- No AI palette: no purple-to-blue gradients, no neon on dark, no cyan glow

Specify: surface, text primary, text secondary, border, accent, semantic (success/error/warning).

**3.3 Spacing direction**

Propose a spacing scale:
- Base unit (4pt recommended)
- Semantic tokens: xs, sm, md, lg, xl, 2xl
- Section-level vs. component-level gap strategy

**3.4 Layout direction**

Propose structural changes by section. Be specific about structure, not just "improve the hero."

Examples of specificity:
- "Move from centered hero to left-content / right-asset split at 55/45"
- "Replace 3-column icon card grid with alternating text-left / image-right feature strips"
- "Add a social proof bar between hero and features — a single row of logos with context"

**3.5 Motion direction**

Assign a motion tier (1–5) from `styles/motion.md`. Then specify:

- **Scroll reveal directions:** Never default to all-`up`. Specify per element type:
  - Physical-goods (footwear, apparel, DTC): product images use `rotate` reveal; paired
    content strips alternate `left`/`right` so text and visual enter from opposing sides
  - Agency/editorial: clip-path curtain reveals on headlines
  - SaaS: subtle `up` staggered entrance, Tier 2–3
- **3D interactions:** For Tier 4–5 and physical-goods brands, propose at least one:
  - Scroll-linked product rotation (product spins as user scrolls past it)
  - Perspective section entrance (section tilts into flat from 3D angle)
  - Multi-layer parallax on hero (shadow + product + detail at different speeds)
  - 3D card tilt on hover for product cards or portfolio pieces
- **Hover behavior:** scale, color shift, border reveal — pick one family and stay consistent
- **Easing standard:** Always specify the cubic-bezier. Never named CSS easings alone.
- **Exit:** faster than entrance — always

**3.6 Texture direction**

Evaluate whether the brand needs textured backgrounds. Ask: does this brand exist physically?
Does the current design feel flat or digital-sterile for what it sells?

If yes — always specify:
- Texture type matched to brand material (canvas → athletic/outdoor, linen → luxury,
  grain/noise → editorial/agency, concrete → dark urban, paper → organic/wellness)
- Where it applies (hero, product sections, CTA backgrounds — never on photography or inputs)
- Opacity (0.03–0.06 on light, 0.06–0.12 on dark)

Read `styles/motion.md` → Textured Backgrounds for all CSS implementations.

---

### Phase 4 — UI Kit Evaluation

Before writing any code, scan `components/ui-kit.html` and make an explicit decision on
each component category. State these decisions plainly — don't silently skip the kit.

Write a brief evaluation block:

```
**UI Kit fit for [Site Name]**
- Buttons: [which variant and where, or why none fit]
- Cards: [3D tilt / blob-glow / neither — reason]
- Inputs: [dark pill / outlined / custom — reason]
- Loaders: [which if needed, or N/A]
- Toggles/checkboxes: [yes/no + reason]
- Tooltips: [which variant / not needed — reason]
- Forms: [flip auth / minimal auth / custom / not needed]
```

Then use the approved components directly in the generated code below.
Rejected components need no further mention.

---

### Phase 5 — 3D Assessment

Before writing code, explicitly evaluate whether 3D belongs in this redesign.
State the decision and the reasoning — do not silently omit it.

**Evaluate against these triggers:**
- Physical product brand (footwear, apparel, electronics, furniture, bags, cars)? → strong 3D signal
- Motion tier 4 or 5? → 3D likely appropriate
- Creative agency / portfolio / experimental product? → 3D expected
- Niche top performers commonly use 3D? → 3D worth including
- Healthcare, legal, institutional, Tier 1–2? → 3D probably wrong

**If 3D is appropriate, specify:**
1. Which interaction (scroll rotation, hover tilt, parallax layers, perspective entrance)
2. What asset it requires (transparent PNG, layered PNGs, .glb model, video)
3. Complexity level (CSS-only / vanilla JS / Three.js)
4. Build decision: include now (CSS/JS), or flag as next phase (Three.js/model-dependent)

Include CSS and vanilla JS 3D directly in the generated code.
Flag Three.js or model-based 3D in the "What you need" section as a next step.

---

### Phase 6 — Redesign Code

Generate working code for the 3–4 highest-impact sections. Almost always:
- Navigation
- Hero
- One feature / value section
- CTA or footer

**Button selection — never default to a plain rectangle:**

Run this decision tree for every button in the redesign. Read `components/buttons.html`
for full implementations — adapt colors to the site's design system before use.

```
Dark hero (agency / DTC / AI / portfolio)?   → btn-blob or btn-3d
Light SaaS / fintech hero?                   → btn-shimmer or btn-arrow
Secondary / ghost CTA?                       → btn-fill (transparent) or btn-flood
E-commerce / footwear / bold DTC?            → btn-stacked (physical depth feel)
Luxury / editorial secondary?                → btn-flood or btn-underline
Agency / portfolio theatrical CTA?           → btn-split or btn-magnetic (one per page)
Nav CTA?                                     → btn-arrow, small
Form submit / low-key action?                → btn-arrow or btn-fill minimum
Onboarding / install / download?             → btn-progress
Text-level / inline CTA?                     → btn-text-link or btn-underline
Tier 1 only (healthcare / legal)?            → plain button with strong border + hover state
```

Adapt all button CSS custom properties to the site's OKLCH color system.
Do not paste ui-kit colors verbatim — remap to the project palette.

**Code rules:**
- Clean, semantic HTML with self-contained CSS in a `<style>` block
- Mobile-first — every layout works at 375px
- No external dependencies required (system font fallbacks if web fonts referenced)
- Placeholder images: `https://picsum.photos/seed/{word}/800/600` or inline SVG
- No banned patterns from `styles/design-system.md` (no gradient text, no decorative glassmorphism,
  no neon glows, no side-stripe borders, no bounce easing)
- Active states on all interactive elements: `transform: scale(0.97)` minimum on press
- Loading and error states where forms exist
- `prefers-reduced-motion` wrapping all animations
- Directional scroll reveals (`data-reveal`) on every major content block
- Paired sections use opposing reveal directions (text left, visual right)
- Texture applied where brand warrants it — see `styles/motion.md`

For each section, open with a plain comment explaining the key decision:
`<!-- Decision: [what changed from original and why] -->`

---

## Output Format

```
## Design Intelligence — [Site Name]

### What exists now
[Plain description of the current design system — fonts, colors, spacing, components]

### Where it sits vs. where it should be
[Niche positioning, aspiration gap, personality gap — written as plain assessment]

### Design Direction

**Brand voice:** [3 specific words]

**Typography**
- Display: [font] · [weights] · [why]
- Body: [font] · [weights] · [why]
- Scale: [key sizes]

**Color System** (OKLCH)
- Surface: oklch(...)
- Text: oklch(...)
- Muted: oklch(...)
- Border: oklch(...)
- Accent: oklch(...)

**Layout changes**
- [Section]: [specific structural change + plain reason]

**Motion (Tier [N])**
- Scroll reveals: [which directions, which elements]
- Hover: [behavior]
- Easing: cubic-bezier(...)

**Texture:** [type + where + opacity, or "not applicable — reason"]

---

### UI Kit Evaluation
[Brief table or list — explicit yes/no per component category with reason]

---

### 3D Assessment
[Decision + reasoning. If yes: which interaction, what asset, complexity, build/next-phase]

---

### Redesigned Sections

#### Navigation
<!-- Decision: [...] -->
```html
[complete code]
```

#### Hero
<!-- Decision: [...] -->
```html
[complete code]
```

#### [Section]
<!-- Decision: [...] -->
```html
[complete code]
```

---

### Pattern synthesis
[3–5 patterns from niche research — framed as "commonly seen in top [niche] sites"]

---

### What you need to make this work

**Images**
- [Specific image, dimensions, context]

**Fonts**
- [Font name] — [source, cost]

**3D & Animation**
- [Each interaction: asset needed, complexity, how to implement]

**UI Components used**
- [Name — where used, or "None"]

**Other**
- [Libraries, CDN links, APIs]
```
