# Anti-Slop Index

The complete taxonomy of patterns that signal AI-generated, template-built, or low-craft
frontend design. Referenced by Agent 3 (Slop Detector) and applied by all agents when
generating or evaluating output.

**How to use this index:**
- Each pattern has an ID (matches agent scoring system), description, detection signal,
  and the fix direction
- Severity levels: HIGH (fix immediately), MEDIUM (fix in next pass), LOW (polish)
- "AI tell level": how quickly an experienced designer would recognize this as AI-generated

---

## Category 1 — Visual Slop

### V1 — Purple/Blue Gradient Hero
**Severity:** HIGH · **AI tell level:** Instant

**What it is:** A full-width diagonal or radial gradient from a purple, violet, or indigo
to a blue or teal, used as the primary hero background. Often accompanied by floating
blob shapes in complementary colors.

**Why it reads as slop:** This exact gradient was the default "looks professional" choice
for AI-generated landing pages from 2023–2025. It has been applied to tens of thousands
of sites with zero brand relationship. It signals "I asked an AI to make something that
looks modern" more than any other single pattern.

**Detection:** Background-color or gradient on the hero section containing any combination
of hue values in the 250–300 range (purple/violet) paired with 200–250 (blue/teal).

**Fix direction:** Replace with a solid color derived from the actual brand. If a gradient
is genuinely desired, make it single-hue (light to slightly darker version of same hue) or
use an image. Earn the gradient by making it mean something.

---

### V2 — Decorative Glassmorphism
**Severity:** MEDIUM · **AI tell level:** High

**What it is:** Cards, modals, or containers with `backdrop-filter: blur()` and
semi-transparent backgrounds used primarily for visual effect, not to solve a layering problem.

**Why it reads as slop:** Glassmorphism was a genuine design trend that got immediately
co-opted into a "make it look designed" shortcut. When used without functional purpose
(i.e., there's no actual content behind the card that needs to bleed through), it's pure decoration.

**Detection:** `backdrop-filter: blur()` or `background: rgba(..., 0.x)` on cards that sit
on a solid color background with no content behind them.

**Fix direction:** Remove the blur effect. Use a solid card background instead. If translucency
is genuinely desired (sticky nav over hero content, modal over page), use it — just not on
feature cards sitting on a white background.

---

### V3 — Icon Card Grid
**Severity:** HIGH · **AI tell level:** Instant

**What it is:** A 3-column (sometimes 4-column) grid of identical cards, each containing:
an icon (often colorful, in a rounded-square container), a heading (2–4 words), and
2–3 lines of body text. Repeated 6–12 times.

**Why it reads as slop:** This is the single most common AI-generated feature section
structure. It emerged because AI can easily fill a template with parallel content.
It's visually flat (everything is equal weight), informationally poor (nothing is
prioritized), and immediately recognizable as generated.

**Detection:** Grid with 3+ identical-structure items each containing: icon/visual element
+ short heading + short paragraph. All cards same size. All have same visual treatment.

**Fix direction:** Feature strips (alternating text/visual, each one focused), bento grid
(asymmetric cells, varied importance), or a narrative section that treats one feature
at a time with depth. See `components/cards.html`.

---

### V4 — Neon Glow
**Severity:** HIGH · **AI tell level:** High

**What it is:** `box-shadow: 0 0 [N]px [saturated-color]` on buttons, cards, or borders.
Also: glowing text with `text-shadow` in saturated colors.

**Why it reads as slop:** Neon glow was the shorthand for "futuristic / tech / cool" in
the 2023–2024 wave of AI-generated UIs. It reads immediately as generated because no
real designer who has used it extensively would choose it — it dates rapidly, it reduces
legibility, and it has no relationship to how actual screens produce light.

**Fix direction:** Use `box-shadow: 0 0 0 1px [color]` for border emphasis. Use
`box-shadow: 0 4px 16px [color/0.15]` for subtle depth. If a dark-background product
has a legitimate "glow" aesthetic (gaming, nightlife, music), use warm gradients in
the background rather than emitted light on individual elements.

---

### V5 — Decorative Blob Shapes
**Severity:** MEDIUM · **AI tell level:** High

**What it is:** Large, soft-edged abstract shapes — often SVG paths or elements with
extreme border-radius values — in gradient colors, used as background decoration behind
hero content or feature sections.

**Why it reads as slop:** Blobs became the default "organic, modern" background element
in AI-generated UIs. They have no brand relationship, they often clash with the actual
content layout, and they are visually noisy without adding information.

**Fix direction:** If background interest is needed, use: a photography background,
a texture (subtle, purposeful), a geometric shape system that relates to the brand's
design language, or simply a high-quality solid color that breathes. If blobs are
genuinely part of the brand's visual identity (rare), use them consistently and sparingly.

---

### V9 — Nested Cards
**Severity:** HIGH · **AI tell level:** Medium

**What it is:** A card container (background, border, border-radius, shadow) placed
inside another card container. Sometimes three levels deep.

**Why it reads as slop:** Nesting cards is a lazy solution to grouping related content.
It creates visual debt that compounds — the more levels, the more the design fights itself.
It's a tell of someone who learned "cards = organized" and didn't learn when to stop.

**Fix direction:** Flatten. Use dividers, typography scale, or spacing to group content
within a single card. If two levels are genuinely needed (e.g., a sidebar card containing
a list of items), ensure only one level uses the full card treatment.

---

### V10 — Side-Stripe Border
**Severity:** MEDIUM · **AI tell level:** High

**What it is:** `border-left: 3px solid [accent-color]` or `border-left: 4px solid`
on cards, callout boxes, testimonials, or list items.

**Why it reads as slop:** This was used prolifically by AI design tools as an
"emphasis" shorthand. It became so common that it now signals template-built or
AI-generated design rather than intentional emphasis.

**Fix direction:** For callouts: full border + tinted background. For testimonials:
large quotation mark, avatar, or pull-quote treatment. For list items: numbered
list, icon, or spacing-based grouping. Never the side stripe.

---

## Category 2 — Typography Slop

### T1 — Inter as Display Face
**Severity:** HIGH · **AI tell level:** Instant

**What it is:** Using Inter (or `font-family: -apple-system, BlinkMacSystemFont, 'Inter', sans-serif`)
for headings at all sizes, including the hero headline.

**Why it reads as slop:** Inter is an excellent UI/body font designed for legibility in
interfaces. It was never designed as a display face. Using it at 60–80px for a hero
headline produces a result that is legible but completely characterless. It is the
most-used font in AI-generated design by a large margin.

**Fix direction:** Keep Inter for body text if desired. Choose a display face with character
for headings. See `styles/typography.md` for niche-specific recommendations.

---

### T2 — Syne
**Severity:** HIGH · **AI tell level:** Instant

**What it is:** Any use of Syne, particularly at display sizes.

**Why it reads as slop:** Syne was intended as a distinctive, experimental display font.
It became the go-to "distinctive" font for AI-generated design because it appeared
frequently in training data as an example of "not Inter." Now it is one of the most
reliable AI-design tells. Its distinctive geometric feel is immediately recognizable
as a shortcut to "designed."

**Fix direction:** Browse Google Fonts with specific brand words in mind and choose
something that has a genuine relationship to the brand. See `styles/typography.md`.

---

### T3 — Oversized Italic Serif Hero
**Severity:** HIGH · **AI tell level:** Instant (as of 2025–2026)

**What it is:** A primary hero headline set in an oversized italic serif — Fraunces,
Playfair Display, Cormorant, or Newsreader — at 64px or larger, often in a light italic weight.

**Why it reads as slop:** This pattern became the dominant "luxury / editorial / premium"
AI-design hero treatment in 2024–2025. It was generated so frequently that it is now
a reliable fingerprint. The combination of oversized + italic + serif + hero position
is the tell — not any of those choices in isolation.

**Fix direction:** If an editorial serif is right for the brand, use it at a weight and
style that isn't the standard AI treatment. Consider: bold weight instead of light italic,
all-caps at a smaller size, mixed weight pairing, or placing it outside the hero position.

---

### T4 — Gradient Text
**Severity:** HIGH · **AI tell level:** High

**What it is:** `background: linear-gradient(...); -webkit-background-clip: text; color: transparent`
applied to headline or subheadline text.

**Why it reads as slop:** Gradient text reduces legibility (especially on non-white
backgrounds), breaks at text rendering edge cases, and became extremely common in
AI-generated UIs as a "makes it look dynamic" shortcut. It is decoration masquerading
as typography.

**Fix direction:** Use a single, solid color. If emphasis is needed: weight, size,
or a different color (not gradient).

---

### T5 — Uppercase Eyebrow Chip
**Severity:** HIGH · **AI tell level:** Instant

**What it is:** A small pill or chip element in uppercase, small tracking, with
a colored background or border, placed directly above every section heading on the page.

**Why it reads as slop:** This pattern — `<span class="chip">NEW FEATURE</span>` followed
by `<h2>Big Headline Here</h2>` — became so prevalent in AI-generated UIs that it is
immediately recognizable as a template structure. When every section has the same
eyebrow+heading+body structure, the page has no rhythm, only repetition.

**Fix direction:** Use section labels sparingly — once or twice per page, only where
they add genuine navigational value. Redesign as: a subtle text label with no pill,
a numbered section marker, or simply remove it (the heading usually doesn't need a preamble).

---

## Category 3 — Copy Slop

### C1 — Transformation Verbs
**Severity:** HIGH · **AI tell level:** Instant

The five most overused AI-generated hero verbs:

| Verb | What to say instead |
|------|---------------------|
| Elevate | Name what specifically improves |
| Transform | Describe the actual before/after |
| Unlock | Name what was previously inaccessible |
| Unleash | What specific capability are you releasing? |
| Revolutionize | A strong claim — prove it with specifics |

**Pattern:** "[Verb] your [noun] with [product]" as the hero headline.

**Fix direction:** Lead with the specific outcome. "Cut onboarding time in half" beats
"Transform your onboarding experience." Specificity is credibility.

---

### C2 — Frictionless/Seamless
**Severity:** HIGH · **AI tell level:** High

**What it is:** Using "seamless," "effortless," "frictionless," or "intuitive" as
primary descriptors in copy.

**Why it reads as slop:** These words describe the experience of using the product, not
the product itself. They are claims without evidence. Every product says it's seamless.
Saying it means nothing. Real copywriting shows the friction being removed, not tells.

**Fix direction:** Show don't tell. "Three clicks from upload to published" instead of
"effortless publishing." "No more copy-pasting between tools" instead of "seamless integration."

---

### C8 — Placeholder Testimonials
**Severity:** HIGH · **AI tell level:** Instant

**What it is:** Testimonials with generic names (John D., Sarah C., Alex M., Mike T.)
or clearly stock-photo avatars with placeholder copy.

**Why it reads as slop:** It's the most trust-destroying element on any page. A sophisticated
visitor immediately recognizes placeholder testimonials and discounts everything else on the page.

**Fix direction:** If you don't have real testimonials yet, don't use testimonials.
Use a different proof mechanism: a demo, a case study, or a waitlist number.

---

### C9 — Emoji in UI Copy
**Severity:** HIGH · **AI tell level:** Instant

**What it is:** Any emoji used in headlines, subheadlines, body copy, feature descriptions,
navigation labels, button text, section headings, eyebrow labels, testimonials, pricing
tables, or as bullet point replacements (🚀 Fast · ✅ Secure · 💡 Smart).

**Why it reads as slop:** Emoji in UI copy is the single fastest signal that a site was
vibe-coded or AI-generated. No brand at the high end of any market uses emoji in their
product UI or marketing copy — not Stripe, not Linear, not Apple, not Rolex, not Anthropic.
Emoji belong in chat and social. The bullet-list emoji pattern (🚀 = speed, ✅ = trust,
💡 = insight) is the most recognizable AI-generation fingerprint that exists. It signals
content was generated, not written.

**Detection:** Any Unicode emoji in visible UI text. Does not apply to user-generated
content displays or chat UIs where emoji are the expected medium.

**Fix direction:** Remove every emoji. Replace with plain text — the words should carry
the meaning. If visual markers are genuinely needed, use a consistent SVG icon system.
If the copy only works with an emoji propping it up, rewrite the copy.

---

## Category 4 — Layout Slop

### L2 — Identical Section Rhythm
**Severity:** HIGH · **AI tell level:** High

**What it is:** Every section on the page follows the same template:
[Eyebrow label] → [H2 heading] → [Body paragraph] → [3-column card grid or 2-column split]
with identical padding and identical visual treatment.

**Why it reads as slop:** Rhythm requires variation. When every section is the same,
there is no hierarchy — only repetition. The eye has no reason to engage. It signals
that the page was filled rather than designed.

**Fix direction:** Vary section structure deliberately. A full-bleed testimonial between
two feature sections. A dense data section between two spacious text sections. A dark
background section between two light ones. Contrast creates rhythm.

---

## Category 5 — Interaction Slop

### I3 — Hover Glow
**Severity:** HIGH · **AI tell level:** High

**What it is:** Elements (buttons, cards, icons) that emit a colored glow on hover —
implemented via `box-shadow: 0 0 [N]px [saturated-color]`.

**Why it reads as slop:** Glow is not a natural property of hover states. Buttons don't
emit light. This was used prolifically as a "this button is interactive" shorthand in
AI-generated UIs. Real interactive states use: background color shift, border change,
scale transform, text color change — not emitted light.

**Fix direction:** `background-color` shift on hover, plus `transform: scale(0.97)` on active.

---

## Patterns That Are NOT Slop

These are often flagged incorrectly — they are legitimate design choices when used intentionally:

- **Dark mode / dark backgrounds** — only slop when it's the AI default with neon accents
- **Glassmorphism on sticky nav** — functionally correct use, not decoration
- **Large bold hero type** — only slop if combined with gradient text + eyebrow chip + italic serif
- **Gradient backgrounds** — only slop when it's the generic purple-to-blue without brand relationship
- **Animation on scroll** — only slop when everything animates with no hierarchy of importance
- **Logo walls** — only slop when logos are faded, context-free, and unverifiable
- **Testimonials with star ratings** — only slop when there are no real names or specifics
- **Cards** — only slop when every piece of content is in an identical card regardless of need
