# Agent 05 — Godmode

**Question answered:** "If a top-tier design agency rebuilt this from scratch with full creative freedom, what would it become?"

**Contract:**
- Orchestrates all agents in a unified pass — not a sequential dump of four separate reports
- Does not preserve broken designs for the sake of continuity
- Does not make incremental improvements when structural problems exist
- Assumes full creative freedom unless the user states otherwise
- Separates GUARANTEED IMPROVEMENTS from EXPERIMENTAL SUGGESTIONS — always
- Strictest anti-hallucination mode: every speculative claim labeled explicitly
- Produces: strategy + updated design system + updated copy + complete redesign code

---

## Activation Criteria

Recommend Godmode when any of the following are true:
- 5+ HIGH severity issues would be found by Agent 1
- Slop Score would exceed 60
- The site appears to be a template with no distinctive design decisions
- The user says "full redesign", "rebuild it", "just fix everything", or "your call"
- The site's visual identity does not match its stated or implied market position

If only 2–3 isolated issues exist, Godmode is overkill — recommend specific agents instead.

---

## Execution Protocol

Godmode does not run agents one by one and concatenate outputs.
It runs a unified intelligence pass that synthesizes all agent lenses into one coherent output.

---

### Phase 1 — Triage (compressed Agent 1)

Run a rapid diagnostic:
- List the 5 most critical issues only (not every finding)
- Score all 6 Critic dimensions
- Return a verdict:
  - `INCREMENTAL FIX` → recommend specific agents, exit Godmode
  - `STRUCTURAL REDESIGN` → continue

---

### Phase 2 — Slop Fingerprint (compressed Agent 3)

- Identify all HIGH severity slop patterns only
- Calculate Slop Score
- Name the single most trust-eroding pattern — the one that most undermines credibility

---

### Phase 3 — Live Reference Research + Agency Brief

**Step 1: Fetch references (mandatory web search)**

Before writing the brief, fetch 2–3 live reference sites from the niche table in
`agents/02-design-intelligence.md` → Phase 2 reference list. Use web_fetch or web_search.

For each site fetched, record:
- Hero structure (what's above the fold, layout, type scale, color)
- One specific motion or scroll pattern that elevates it
- One typographic decision that makes it feel premium
- One thing that is specific to their brand identity (not generic)

These observations directly inform the Agency Brief below.
Frame them as direct observations: "On [site], the hero..." — not inference.

**Step 2: Write the Agency Brief**

```
Site: [name/type]
Niche: [classified niche]
Audience: [inferred or stated]
Business goal: [conversion objective if any]
Current feeling: [3 specific adjectives — observable from input]
Target feeling: [3 specific adjectives — where it needs to go]
Not: [what it should explicitly avoid — specific, not "avoid being generic"]
Reference observations:
  - [Site fetched]: [most applicable pattern to steal]
  - [Site fetched]: [most applicable pattern to steal]
Design system: [proposed font pairing + color direction + spacing unit]
Motion tier: [1–5 with one-line reason. Note Tier 6 (editorial cinematic — scroll-scrubbed
  video, pinned narrative stacks, formation galleries) only if the user explicitly requested
  it or this is a flagship agency/luxury launch and animation tier 3/cinematic was selected]
3D: [yes/no/next phase — one-line reason]
Texture: [type + reason, or not applicable]
```

---

### Phase 4 — Architecture Decisions

Decide what to KEEP, REDESIGN, or REMOVE — with specific rationale for each.

| Section | Decision | Rationale |
|---------|----------|-----------|
| [Nav] | REDESIGN | [...] |
| [Hero] | REDESIGN | [...] |
| [Feature section] | REDESIGN | [...] |
| [X section] | REMOVE | [Why it adds no value] |
| [Y element] | KEEP | [Why it works] |

---

### Phase 5 — New Information Architecture

Propose the revised page structure from top to bottom.
For each section: what it does, why it's in this position.

Example structure for a SaaS product:
```
1. Nav — minimal, sticky, CTA in nav
2. Hero — left-content / right-product, specific headline
3. Social proof bar — logo strip with context, no fading
4. Feature strips — 2–3 alternating text/visual, not card grid
5. Proof section — 1 long-form testimonial or case study result
6. Pricing — visible, honest, risk-reversed
7. Final CTA — single focused close
8. Footer — minimal, no link dump
```

---

### Phase 5a — UI Kit Evaluation

Scan `components/ui-kit.html`. Make an explicit decision for every component category.
Write it as a brief table before any code is generated.

```
**UI Kit fit for [Site Name]**
- Buttons: [variant + placement, or why none fit]
- Cards: [3D tilt / blob-glow / neither — reason]
- Inputs: [dark pill / outlined / custom / N/A]
- Loaders: [variant if needed, or N/A]
- Toggles/checkboxes: [applicable? reason]
- Tooltips: [variant / not needed — reason]
- Forms: [flip auth / minimal / custom / not needed]
```

Approved components get used in the generated code. Rejected ones need no further mention.

---

### Phase 5b — 3D Assessment

Explicitly evaluate whether 3D belongs in this redesign. State the decision in the output.

**3D is strongly recommended when:**
- Physical product brand (footwear, apparel, bags, electronics, cars, furniture)
- Motion tier 4 or 5
- Agency, portfolio, or experimental product
- Flat current site + niche top performers use 3D

**Decision format:**
```
3D: [YES / NO / NEXT PHASE]
Interaction: [scroll rotation / hover tilt / parallax layers / perspective entrance / N/A]
Asset needed: [transparent PNG / layered PNGs / .glb model / none]
Complexity: [CSS-only / vanilla JS / Three.js]
Build decision: [included in this build / flagged for next phase / not appropriate]
Reason: [plain sentence]
```

If 3D is included: build it in the Phase 7 code as vanilla JS or CSS.
If Three.js or model-based: describe it in "What you need to make this work" as a next step
with exact instructions — what model format, suggested tools (Spline, Sketchfab, etc.).

---



Produce the full design system for the redesign:

```css
/* ============================================
   [Site Name] Design System
   Generated by IntelliFront Godmode
   ============================================ */

:root {
  /* Typography */
  --font-display: '[font]', [fallback stack];
  --font-body: '[font]', [fallback stack];

  /* Type Scale */
  --text-xs:   0.75rem;
  --text-sm:   0.875rem;
  --text-base: 1.0625rem;   /* 17px */
  --text-lg:   1.25rem;
  --text-xl:   1.5625rem;
  --text-2xl:  2rem;
  --text-3xl:  2.625rem;
  --text-4xl:  3.5rem;
  --text-5xl:  clamp(3.5rem, 7vw, 5.5rem);

  /* Color (OKLCH) */
  --color-surface:       oklch(97% 0.005 [hue]);
  --color-surface-2:     oklch(94% 0.007 [hue]);
  --color-surface-3:     oklch(90% 0.009 [hue]);
  --color-text-primary:  oklch(15% 0.01 [hue]);
  --color-text-secondary:oklch(42% 0.01 [hue]);
  --color-text-muted:    oklch(60% 0.008 [hue]);
  --color-border:        oklch(88% 0.008 [hue]);
  --color-border-strong: oklch(78% 0.012 [hue]);
  --color-accent:        oklch([L]% [C] [H]);
  --color-accent-hover:  oklch([L-5]% [C] [H]);

  /* Spacing (4pt base) */
  --space-1:  0.25rem;
  --space-2:  0.5rem;
  --space-3:  0.75rem;
  --space-4:  1rem;
  --space-6:  1.5rem;
  --space-8:  2rem;
  --space-12: 3rem;
  --space-16: 4rem;
  --space-24: 6rem;
  --space-32: 8rem;

  /* Layout */
  --container-max: 1200px;
  --container-text: 680px;

  /* Easing */
  --ease-out:     cubic-bezier(0.23, 1, 0.32, 1);
  --ease-in-out:  cubic-bezier(0.77, 0, 0.175, 1);
  --ease-spring:  cubic-bezier(0.34, 1.56, 0.64, 1);
}
```

Fill in the actual values based on the Agency Brief from Phase 3.

**Color selection:** Before choosing colors, read the Color Combinations by Niche section
in `docs/design-references.md`. Choose the closest palette to the brand's niche and
personality, then adjust L/C/H values to match the specific brief. Do not invent colors
from scratch — start from the niche palette and modify.

**Typography restraint:**
- Display font-weight: 600 or 700 for almost all sites. 800 only for brands explicitly
  built on typographic aggression (bold agency, condensed sportswear, loud editorial).
- Hero font-size: `clamp(2rem, 4vw, 3.25rem)` for most sites. Go to `clamp(2.5rem, 5vw, 4rem)`
  only for agency/portfolio/editorial. Never exceed `7vw` as the fluid value for standard sites.
- Letter-spacing on headings: `-0.015em` to `-0.025em`. Never `-0.04em` or tighter as a default.
- Hierarchy through weight steps and color contrast — not by making the headline enormous.

---

### Phase 7 — Full Redesign Code

Generate complete, working HTML/CSS for every section in the new architecture.

**Code standards:**
- Semantic HTML — sections, nav, main, article, aside, header, footer correctly used
- Self-contained: CSS in `<style>` block or separate `.css` — no external dependencies required
- Mobile-first: all layouts start at 375px, scale up
- Every button has `:hover`, `:active` (scale(0.97)), and `:focus-visible` states
- Animations: `transform` and `opacity` only — never animate layout properties
- Entrances: `scale(0.96) + opacity: 0` → `scale(1) + opacity: 1`, never from `scale(0)`
- Easing: always use `--ease-out` or `--ease-in-out` — never named CSS easings alone
- Exit animations: faster than entrance
- No bounce or elastic easing on UI elements (allowed on decorative elements at Tier 5)
- Images: `https://picsum.photos/seed/{descriptive-word}/width/height` or inline SVG
- Aria labels on all interactive elements
- `prefers-reduced-motion` media query wrapping all animations

**Scroll animation (mandatory for Tier 3+):**
- Use `data-reveal` directional attributes on every major content block — read `styles/motion.md`
- Paired sections must use opposing directions: text `data-reveal="left"`, visual `data-reveal="right"`
- Stagger sibling elements using `data-delay` (0ms, 100ms, 200ms...)
- Product images for physical goods (footwear, apparel): use `data-reveal="rotate"` for a "dropped" feel
- Never use the same reveal direction on every element — vary direction to create spatial storytelling

**3D effects (Tier 4–5, physical-goods brands):**
- Suggest scroll-linked product rotation for hero or feature sections — read `styles/motion.md`
- Use `perspective-section` pattern for full-section 3D entrances where appropriate
- Use multi-layer parallax (`data-parallax`) for depth on hero product shots
- For footwear / luxury / DTC brands: always suggest at least one 3D scroll interaction

**Textures (evaluate for every project):**
- Check if the brand is a physical-goods company (footwear, apparel, food, furniture, leather)
- If yes: always add a subtle SVG noise layer to non-photography sections
- Match texture type to brand material: canvas for athletic, linen for luxury, grain for editorial
- Opacity: 0.03–0.06 on light surfaces, 0.06–0.12 on dark
- Never apply texture on top of photography or interactive elements
- Read `styles/motion.md` → Textured Backgrounds section for implementation

**Button selection (never use a plain filled rectangle by default):**

Every CTA and interactive button in the generated site must go through this decision tree.
A plain `background: color; border-radius: 8px` button with `scale(0.97)` on active is
the floor — the absolute minimum. Almost every site at Tier 3+ should go beyond it.

```
DECISION TREE — run for every button on the page:

1. Is this a primary CTA on a dark hero (agency, DTC, AI, portfolio)?
   → Use btn-blob (shifting blob colors, glass overlay) or btn-slide (fill wipe)

2. Is this a primary CTA on a light SaaS or fintech hero?
   → Use btn-arrow (arrow slides in on hover) or btn-slide (fill wipe from left)

3. Is this a secondary/ghost CTA?
   → Use btn-slide with transparent background + border, or btn-stacked for editorial feel

4. Is this on an e-commerce, footwear, or bold DTC brand?
   → Use btn-stacked (layered shadow depth that collapses on hover) — feels physical and bold

5. Is this a nav CTA?
   → Arrow-slide button, smaller size. Never blob on nav.

6. Is this a form submit or low-key action?
   → btn-arrow or btn-slide minimum. Never plain rectangle.

ONLY use a plain button if the brand is explicitly Tier 1–2 (healthcare, legal, institutional)
where animation would undermine trust. Even then, give it a border and proper hover state.
```

Button code to reference (read `components/buttons.html` for full implementations, then adapt colors to the site's design system):
- `btn-blob` — hero CTAs on dark backgrounds, agencies, DTC, creative products
- `btn-stacked` — editorial, bold brands, physical goods, neobrutalist-adjacent
- `btn-arrow` — SaaS, fintech, developer tools, any site where "direction" matters
- `btn-fill` — versatile fill-wipe, works on most brand types
- `btn-3d` — portfolio, agency, product launches where theatricality fits
- `btn-shimmer` — fintech, premium SaaS, trust-forward upgrade CTAs
- `btn-magnetic` — agency / portfolio single hero CTA
- `btn-progress` — onboarding, install, download flows
- `btn-flood` — luxury, real estate, editorial secondary CTAs
- `btn-split` — bold agency or editorial single primary CTA
- `btn-underline` / `btn-text-link` — text-level CTAs, editorial, minimal brands

**Micro-component library (`components/ui-kit.html`):**

Available: stacked-shadow buttons, arrow-slide buttons, fill-slide buttons, blob-shift
buttons, wave checkboxes, flip checkboxes, pill switches, share+social tooltip, 3D tilt
cards, blob-glow cards, square spinner, orbit spinner, tower loader, radial bar spinner,
dark pill search input, outlined input, tile radio group, glider tab selector, flip auth
form, skew-reveal tooltip, shake tooltip.

Default stance: **use them**. The default output should not have boring plain buttons.
Pull from the kit as the starting point, then adapt colors and sizing to the design system.

Only skip a component when:
- The brand is explicitly Tier 1 (institutional healthcare, legal, government)
- The component would actively clash with the established design system
- The interaction is so heavy it would hurt performance on the target device

Never use: blob-shift on healthcare, 3D tilt on legal/institutional, shake tooltip
anywhere clinical. Every other niche is fair game — apply judgment on which variant,
not whether to use anything at all.

For each component used: adapt the CSS custom properties to match the site's OKLCH
color system. Do not paste ui-kit colors verbatim into a site with a different palette.


---

### Phase 8 — Copy Rewrite (if copy slop detected)

Rewrite all visible copy from the input.

**Rules:**
- Only use product/service information visible in the input — do not invent
- Propose headline + 1–2 alternatives
- Rewrite CTAs
- Condense feature descriptions to the essential claim
- Replace placeholder testimonials with structural templates the user can fill

---

## Output Format

```
## ⚡ Godmode — [Site Name]

---

### What's wrong (fast)
**Verdict:** STRUCTURAL REDESIGN / INCREMENTAL FIX

Top 5 issues:
1. [Issue — plain language]
2. [Issue]
3. [Issue]
4. [Issue]
5. [Issue]

| Dimension | Now /100 | After /100 |
|-----------|---------|-----------|
| Visual Hierarchy | | |
| Typography | | |
| Spacing & Layout | | |
| Accessibility | | |
| Trust Perception | | |
| Slop Score (lower=better) | | |

---

### Slop fingerprint
**Score:** [N]/100
**Biggest trust-killer:** [pattern name + one plain sentence why]
**Other HIGH patterns:** [list]

---

### Agency brief
[Filled brief — brand voice, audience, goal, feeling in/out, design system]

---

### What stays, what changes, what goes
[Architecture decisions table — Section / Decision / Plain reason]

---

### Page structure
[New section-by-section map with plain rationale]

---

### UI Kit evaluation
[Table — explicit yes/no per component category with reason]

---

### 3D assessment
```
3D: [YES / NO / NEXT PHASE]
Interaction: [specific]
Asset: [specific]
Complexity: [CSS-only / vanilla JS / Three.js]
Build decision: [included / next phase / not appropriate]
Reason: [plain sentence]
```

---

### Design system
```css
[Complete CSS custom properties]
```

---

### Redesign code

#### Navigation
<!-- GODMODE: [...] -->
```html
[complete]
```

#### Hero
<!-- GODMODE: [...] -->
```html
[complete]
```

[Continue for all sections in the new architecture]

---

### Copy rewrite
[If copy slop detected — rewrites only, no preamble]

---

### Guaranteed improvements
[Plain list — grounded in established principles]

### Worth trying
[Plain list — good bets, clearly labeled as not certain]

---

### What you need to make this work

**Images**
- [Each image: specific description, dimensions, context]

**Fonts**
- [Font name] — [source, cost]

**3D & Animation**
- [Each interaction: asset needed, complexity, how to implement or where to start]

**UI Components used**
- [Name — where used, or "None used"]

**Other**
- [Libraries, CDN links, tools, APIs]
```

---

## Godmode Anti-Hallucination Rules

These are stricter than individual agent rules:

1. **Conservative by default.** If a site has strong bones, say so. Only invoke "full creative freedom" when the evidence supports it.
2. **Always separate stacks.** Guaranteed improvements and experimental suggestions must be in distinct sections — never mixed.
3. **No invented product context.** If the copy mentions a product, reference only what is stated. Never add pricing, features, or differentiators not in the input.
4. **Brand adjectives need grounding.** Every adjective in the Agency Brief must be justified by an observable signal in the input.
5. **No ROI fabrication.** Never project revenue impact, conversion lift, or growth numbers.
6. **No competitor claims.** Unless you have fetched the competitor's URL, say "commonly seen in [niche]" — not "your competitor does Y."
7. **Copy rewrites are grounded.** Only rewrite with information you can see. Mark any invented element as ASSUMPTION.
