# IntelliFront

**Frontend intelligence system for evaluating, critiquing, and redesigning websites.**

IntelliFront is a Claude skill that operates like a senior design agency. It diagnoses
problems, detects AI-generated patterns, synthesizes research-backed design direction,
and generates production-quality redesign code.

## Live Demos

Sites built entirely using IntelliFront + Claude Code — no manual design work.

- [KOVA](https://kova-ruddy.vercel.app) — DTC sneaker brand
- [Seve](https://seve-zeta.vercel.app) — Luxury fragrance brand
- [Lumen](https://lumen-two-lake.vercel.app) — Modern AI product

---

## What It Does

- **Diagnoses** visual hierarchy, typography, spacing, accessibility, and trust issues
- **Detects** AI-generated, template-built, and low-credibility design patterns
- **Researches** best-in-class examples across 9 product niches
- **Redesigns** sections with working HTML/CSS code
- **Optimizes** for conversion on business-oriented sites
- **Transforms** entire sites in Godmode with a full redesign strategy

---

## What It Is Not

IntelliFront is not a website generator. It does not create websites from nothing.
It transforms existing or described sites into better ones.

---

## Repository Structure

```
intellifront/
├── SKILL.md                          ← Entry point — load this first
│
├── agents/
│   ├── 01-critic.md                  ← Frontend Critic
│   ├── 02-design-intelligence.md     ← Design Intelligence + code generation
│   ├── 03-slop-detector.md           ← AI/template pattern detection
│   ├── 04-conversion.md              ← Conversion optimization
│   └── 05-godmode.md                 ← Full transformation mode
│
├── styles/
│   ├── design-system.md              ← Design principles, tokens, absolute bans
│   ├── typography.md                 ← Font selection protocol + pairing library
│   └── motion.md                     ← Motion tier system + implementation patterns
│
├── components/
│   ├── README.md                     ← Component library overview
│   ├── nav.html                      ← Navigation variants
│   ├── hero.html                     ← Hero variants (split, editorial, kinetic)
│   ├── cards.html                    ← Feature strips, bento grid, testimonials
│   ├── cta.html                      ← CTA section variants
│   └── footer.html                   ← Footer variants (minimal, structured, editorial)
│
├── docs/
│   ├── design-references.md          ← Curated niche inspiration library
│   └── anti-slop-index.md            ← Full slop pattern taxonomy
│
├── utils/
│   ├── scoring.md                    ← Score calculation formulas
│   └── confidence.md                 ← Evidence discipline protocol
│
└── examples/
    └── example-output-saas.md        ← Complete example run (SaaS landing page)
```

---

## Installing as a Claude Skill

### Option 1 — Project Knowledge (Claude.ai)

1. Create a new Project in Claude.ai
2. Add all files from this repository to the Project's knowledge base
3. Start any conversation — IntelliFront activates automatically when you share a site

### Option 2 — System Prompt

Paste the contents of `SKILL.md` into your system prompt. The other files should be
included in your context window or referenced as available documents.

### Option 3 — Direct Invocation

In any Claude conversation, paste the contents of `SKILL.md` and say:
> "Use this skill to analyze [URL / screenshot / code]"

---

## How to Use It

### Basic usage

Share a site in any of these forms:
- A URL: `https://yoursite.com`
- A screenshot (paste or upload)
- HTML/CSS source code
- A description: "a SaaS landing page for a project management tool called X"

IntelliFront will analyze the input, present agent options, and wait for your selection.

### Selecting agents

After input analysis, you'll see an agent selection panel. Reply with:
- A number: `1`, `2`, `3`, `4`
- A combination: `1+3` or `1+3+4`
- `godmode` for the full transformation
- `your call` to run the recommended configuration

### Example prompts

```
Roast my landing page: [paste code or URL]
```

```
Does this look AI-generated? [paste code or screenshot]
```

```
Run godmode on this site. I want a complete redesign strategy.
```

```
Run agents 1 and 3 on this: [paste code]
```

```
What's wrong with my hero section? [paste hero HTML]
```

---

## The Agent System

| Agent | What it does | Generates code? |
|-------|-------------|----------------|
| 1 — Frontend Critic | Diagnoses problems | No |
| 2 — Design Intelligence | Research + redesign direction | Yes |
| 3 — Slop Detector | AI/template pattern detection | Yes (for fixes) |
| 4 — Conversion Optimizer | CTA, funnel, copy improvements | Yes (copy) |
| 5 — Godmode | Full transformation: all agents + complete redesign | Yes (full) |

---

## Generated Code

When agents generate code, it is:
- **Self-contained** — HTML with inline `<style>` blocks, no framework dependencies
- **Mobile-first** — all layouts work at 375px viewport
- **Accessible** — semantic HTML, aria labels, focus states
- **Original** — written for the specific site, not copied from components verbatim
- **Adaptable** — generated code can optionally use the IntelliFront component patterns from `/components/`, but this is not required

Code style and design system usage is flexible — agents write code appropriate to the
specific project, not forced into a template.

---

## Design Philosophy

**Restraint over maximalism.** The most common failure in AI-generated design is doing
too much. IntelliFront pushes in the opposite direction — every element earns its place.

**Motion is tiered, not blanket.** A legal firm and a creative agency have different
emotional contracts. Animations scale from "opacity only" (Tier 1) to "cinematic and
physics-based" (Tier 5) based on brand fit — not on what's impressive to generate.

**Evidence before advice.** Every finding is labeled FACT, INFERENCE, or ASSUMPTION.
Fabricated metrics, invented competitor comparisons, and hallucinated user behavior are
explicitly forbidden by the confidence protocol in `utils/confidence.md`.

**Slop is specific, not vague.** "This looks AI-generated" is not a useful critique.
"This uses the purple-to-blue gradient hero (V1), Inter as a display face (T1), and
the transformation-verb headline (C1)" is actionable.

---

## Niche Coverage

IntelliFront's design reference library covers:
- SaaS / developer tools / AI products
- Fintech / financial services
- E-commerce / DTC brands
- Real estate / luxury property
- Agencies / creative studios
- Healthcare / wellness
- Restaurants / hospitality
- Personal portfolios

Reference sites and pattern synthesis in `docs/design-references.md`.

---

## Contributing

This skill is designed to evolve. High-value contributions:

- **New slop patterns** — add to `docs/anti-slop-index.md` with ID, description, detection signal, and fix direction
- **New component variants** — add to the relevant `components/*.html` file as a commented variant
- **New niche references** — add to `docs/design-references.md` under the appropriate niche
- **New font pairings** — add to `styles/typography.md` under the relevant brand personality
- **Example outputs** — add real (anonymized) IntelliFront runs to `examples/`

---

## License

MIT. Use it, adapt it, build on it.

---

*IntelliFront is a Claude skill — it runs inside Claude, not as a standalone application.
It requires access to Claude (claude.ai or Anthropic API).*
