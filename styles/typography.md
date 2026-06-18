# Typography Reference

Font selection is the single highest-leverage design decision. The wrong font makes every
other decision harder. The right font makes the whole system feel inevitable.

---

## Selection Protocol

### Step 1 — Name the voice

Write exactly 3 words that describe the brand's personality as an object in the world.
Not adjectives like "modern" or "clean" — those are empty. Ask: what would this brand be
if it were a physical thing?

**Useful word types:**
- Material: ceramic, machined, weathered, lacquered, forged, linen
- Era: mid-century, Edwardian, 1970s corporate, early internet, pre-war
- Sensory: crisp, warm, grainy, smooth, loud, whispered
- Emotional: confident, apologetic, decisive, curious, composed

Examples:
- "Austere, machined, decisive" → geometric sans with tight tracking, high contrast
- "Warm, handmade, confident" → humanist sans or slab, generous spacing
- "Fast, irreverent, loud" → condensed display, heavy weight, variable sizing
- "Quiet, premium, unhurried" → refined serif or optical-size aware sans

### Step 2 — Banned font check

Do not use these. They are training-data defaults that produce monoculture:

```
Inter, Syne, Fraunces, Newsreader, Lora, Playfair Display, Cormorant,
Cormorant Garamond, Space Grotesk, DM Sans, DM Serif Display, DM Serif Text,
Outfit, Plus Jakarta Sans, Instrument Sans, Instrument Serif, IBM Plex Sans,
IBM Plex Mono, IBM Plex Serif, Space Mono, Crimson Pro, Crimson Text
```

Syne is the most overused "distinctive" font in AI-generated design. It is an instant tell.
Inter is the most overused body font. Both are recognizable in 2 seconds.

### Step 3 — Browse with words in hand

Sources (all accessible to Claude via web search):
- Google Fonts (free, web-ready) — filter by category, look beyond the popular list
- Fontsource (npm-friendly Google Fonts mirror)

When browsing, hold the 3 brand-voice words and ask: would this font look at home on
[the physical object you described]? If yes, proceed. If not, keep looking.

### Step 4 — Cross-check

The right font for "elegant" is not necessarily a serif.
The right font for "technical" is not necessarily monospace.
The right font for "bold" is not necessarily heavy weight.

If your choice matches your first reflex → go back to Step 3.

---

## Pairing Library

These are proven pairings organized by brand personality. All fonts are Google Fonts
unless noted. Use as starting points — adapt weights and scales to the specific project.

---

### SaaS / Developer Tool / AI Product

**Precise and systematic:**
- Display: `Geist` (Vercel) — clean geometric, excellent at display sizes
- Body: `Geist Mono` for code-heavy UIs, or `Geist` at lighter weight for prose

**Technical but approachable:**
- Display: `Cabinet Grotesk` — slightly irregular, humanist, strong at large sizes
- Body: `Satoshi` — neutral and readable, pairs cleanly with Cabinet

**Opinionated and fast:**
- Display: `Archivo` (SemiBold or Bold — 600/700) — compressed, direct
- Body: `Archivo` at Regular — single-family with wide weight range

**Note on condensed heavy weights:** `Barlow Condensed ExtraBold`, `Archivo Black`,
`Unbounded` — these are valid choices for brands whose identity is built on typographic
aggression (sports, bold agency, streetwear). They are not appropriate as default
recommendations for SaaS, fintech, portfolio, or most DTC brands. When in doubt,
use the semibold or bold cut of the same family rather than the black weight.

**Dark developer tool:**
- Display: `JetBrains Mono` at large sizes — readable monospace with personality
- Body: `Karla` or `Mulish` — clean humanist sans for prose

---

### Fintech / Financial Services

**Trust-first:**
- Display: `Barlow` Semi-Condensed SemiBold — structured, confident
- Body: `Barlow` Regular — cohesive, readable

**Premium fintech (Wise, Mercury direction):**
- Display: `Urbanist` Bold — modern, clean, premium without coldness
- Body: `Urbanist` Regular — highly legible, slightly geometric

**Institutional:**
- Display: `Libre Baskerville` Bold — authority and tradition
- Body: `Source Sans 3` — clean complement to the serif

---

### E-Commerce / DTC Brand

**Editorial commerce (Allbirds, Patagonia direction):**
- Display: `Cormorant SC` — note: Cormorant is on the banned list for *Cormorant Garamond* and *Cormorant* as oversized italic hero — Small Caps variant used for display labels is different
  - Alternative: `Libre Caslon Display` for editorial headers
- Body: `Jost` — geometric, confident, readable

**Sportswear / High-energy (Nike direction):**
- Display: `Barlow Condensed` Bold (700) — kinetic, compressed. ExtraBold only if the
  brand's energy genuinely calls for it — Nike itself uses weight sparingly.
- Body: `Barlow` Regular — same family, wide weight range

**Luxury DTC:**
- Display: `EB Garamond` at large sizes — classic, elegant, not trendy
- Body: `Nunito Sans` — clean humanist, doesn't compete with the serif

---

### Real Estate / Luxury Property

**Luxury restraint (Compass, Sotheby's direction):**
- Display: `Canela` (Future Fonts, paid) or `Gilda Display` (free) — editorial, refined
- Body: `Raleway` Medium — structured, architectural

**Approachable luxury:**
- Display: `Yeseva One` — confident serif with character
- Body: `Josefin Sans` — geometric, airy, pairs with serif well

---

### Agency / Creative Studio

**Portfolio with opinions:**
- Display: `Archivo Narrow` Bold (700) — tight and confident without screaming
- Body: `Archivo` Regular — single family, strong weight contrast

**Experimental editorial:**
- Display: `Unbounded` SemiBold — wide, futuristic. Use Black weight only when the
  site's entire identity is built on typographic scale and weight.
- Body: `Noto Sans` — completely neutral, lets the display face dominate

**Note on agency type:** The impulse to use Black/900 weights for agencies is understandable
but usually wrong. Instrument.com, Fantasy.co, and Metalab use confident but not extreme
weights. The boldness comes from scale and composition, not from weight alone.

**Refined creative:**
- Display: `Bodoni Moda` at display sizes only — classic with tension
- Body: `Mulish` — clean, not competing

---

### Healthcare / Wellness

**Clinical trust:**
- Display: `Nunito` ExtraBold — rounded, approachable, not childish at large sizes
- Body: `Nunito` Regular — single family, consistent system

**Calm wellness (Headspace, Calm direction):**
- Display: `Quicksand` SemiBold — soft, warm, optimistic
- Body: `Lato` — neutral, readable, widely accessible

---

### Restaurant / Hospitality

**Fine dining:**
- Display: `Playfair` is banned as an oversized italic hero, but `Playfair Display SC` for
  display labels (not hero H1) can work — alternative: `Gilda Display`
- Body: `Raleway` — structured, a bit architectural

**Casual dining / café:**
- Display: `Vollkorn` Bold — warm, slightly old-fashioned in a good way
- Body: `Source Serif 4` — extremely readable, warmth without softness

---

### Personal Portfolio

**Developer portfolio:**
- Display: `Fira Code` at large sizes — signals craft, unusual at display scale
- Body: `Fira Sans` — same family, prose-ready

**Designer portfolio:**
- Display: `Hanken Grotesk` Bold — precise, confident, not templated
- Body: `Hanken Grotesk` Regular — single family, tight system

**Minimal editorial portfolio:**
- Display: `Libre Baskerville` — classic authority, elegant at display
- Body: `Libre Franklin` — same foundry, cleanly paired

---

## Type Scale by Site Type

| Site type | Display size range | Body size | Scale ratio |
|-----------|-------------------|-----------|-------------|
| SaaS / app | 40–80px | 16–17px | 1.25–1.333 |
| Marketing / landing | 56–96px | 17–18px | 1.333–1.5 |
| E-commerce | 32–64px | 16–17px | 1.25 |
| Portfolio | 64–120px | 16–18px | 1.5 |
| Dashboard / tool | 20–32px | 13–15px | 1.2 |
| Editorial / blog | 32–56px | 17–20px | 1.333 |

---

## Weight Contrast Rule

The minimum weight difference between adjacent heading levels: 2 weights.
If your heading is 700, the next level must be 500 or below.
If everything is 400, there is no typographic hierarchy — only size hierarchy.
Size hierarchy alone is weak. Weight + size hierarchy is strong.

---

## Spacing Around Typography

- Above a section heading: at least 3× the line height of that heading
- Below a heading before body text: 0.5–0.75× the line height
- Between body paragraphs: 1× the line height (use `margin-bottom: 1em`)
- Before a CTA below body: at least 1.5× the line height

This creates the visual grouping that tells readers what belongs together.
