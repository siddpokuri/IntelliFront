# Design References

Curated by niche. Used by Agent 2 and Godmode for niche research and pattern synthesis.

**Usage rules:**
- Never claim to have visited a site unless you have fetched the URL
- Frame all observations as: "commonly seen in top [niche] sites" or "in the direction of X"
- Never copy — synthesize patterns
- These are starting points, not prescriptions

---

## The IntelliFront Core 10

If you could only reference 10 sites, these cover the widest range of design excellence:

| Site | Why it matters |
|------|---------------|
| stripe.com | Information hierarchy — dense content with perfect visual organization |
| linear.app | Spacing and restraint — every pixel is intentional |
| vercel.com | Motion quality — enters and transitions that feel crafted |
| notion.so | Simplicity at scale — complex product, clear UI |
| anthropic.com | Storytelling — values and product woven together honestly |
| apple.com | Product photography + typography — the gold standard |
| compass.com | Luxury + function — property showcase done right |
| nike.com | Editorial e-commerce — product as narrative |
| instrument.com | Agency portfolio — bold, opinionated, craft-forward |
| aman.com | Restraint as luxury — what whitespace and type can do alone |

---

## By Niche

---

### SaaS / Developer Tools

**Pattern library — what top performers do:**
- Left-aligned hero with product screenshot or UI preview on the right
- Dark feature sections interspersed with light — alternating tone keeps energy
- Code block sections: dark background, syntax highlighted, prominent
- Pricing pages: 3 tiers max, recommended plan clearly marked, monthly/annual toggle
- Social proof: logo walls with company names visible (not faded), named testimonials
- Navigation: clean, max 5 items, CTA in nav always

**What to synthesize from Stripe:**
- Hierarchy mastery — heading → subheading → body → CTA reads in clear layers
- Color used sparingly — white-dominant with one strong accent
- Feature sections that explain complexity without overwhelming

**What to synthesize from Linear:**
- The confidence of space — sections aren't crammed, nothing apologizes for existing
- Subtle dark hero with muted accent color, high contrast type
- Motion: understated entrances, nothing performative

**What to synthesize from Vercel:**
- Motion quality — scroll reveals that feel like they were choreographed
- Terminal / code aesthetic that doesn't feel clichéd
- Dashboard preview screenshots with ambient glow (used purposefully, not decoratively)

**Typography direction (SaaS):**
- Display: Geist, Cabinet Grotesk, Archivo, Satoshi — geometric and confident
- Body: Same family or a neutral complement — never serif for body
- Weight contrast: 400 body, 700 display. No in-between for headings.

**Avoid:**
- Purple-to-blue gradient hero backgrounds
- 6-column feature icon grids
- "Trusted by" logo walls with illegible faded logos

---

### Fintech / Financial Services

**Pattern library:**
- Trust is the primary design goal — every choice should build confidence
- Dashboard previews: real numbers (not 99.99%), realistic interfaces
- Security signals above the fold: not a badge wall, but woven into the narrative
- Pricing: transparent, no "contact sales" for standard tiers
- Typography: authoritative but not intimidating — medium weight, high readability

**What to synthesize from Wise:**
- Clarity about what you get and what it costs — no hidden information
- International by design — currencies, flags, global feel without stereotypes
- Clean white with strong typographic hierarchy

**What to synthesize from Mercury:**
- Premium without being cold — warm neutrals with strong type
- Product screenshots that feel like real tools, not demos
- Copy that respects the user's intelligence

**What to synthesize from Brex:**
- Data visualization in the hero — not decorative, but showing actual product
- Strong contrast between sections creates visual rhythm
- Social proof: named founders and CFOs, not "our customers"

**Typography direction (fintech):**
- Display: Barlow, Urbanist, or a structured geometric sans
- Body: same family or Source Sans — high legibility priority
- No playful fonts, no experimental display faces

**Avoid:**
- Stock photos of handshakes or money
- "Bank-grade security" phrases without specifics
- Generic dashboard illustrations that look like every other fintech

---

### E-Commerce / DTC

**Pattern library:**
- Product imagery is the UI — everything else should disappear
- Mobile-first without exception — most purchases happen on phone
- Above-the-fold: product, one clear benefit, one CTA
- Social proof: photos of real customers using the product
- Checkout: as few steps as possible, trust signals throughout
- Story pages: brand narrative as editorial, not marketing copy

**Scroll animation (mandatory for DTC):**
- Product images should never just fade in — use `rotate` reveal for footwear and apparel
  (feels like the product landed on the page), `scale` for accessories, `left`/`right` for
  paired editorial strips
- Alternating feature sections: content enters from left, product enters from right — every
  section, alternating — creates a visual rhythm that feels intentional
- Hero product: consider scroll-linked rotation (product rotates as user scrolls) for
  footwear, bags, and hard goods — makes digital feel physical

**3D for physical goods (strongly recommend):**
- Scroll-linked product spin on hero or featured product section
- Multi-layer parallax on product photography (separate the shoe from its shadow)
- Perspective entrance on full-width editorial sections (tilts from 3D into flat as it enters)

**Textures (always suggest for physical goods brands):**
- Canvas texture on backgrounds for athletic/outdoor brands
- Linen or paper grain for premium/sustainable brands
- Concrete or asphalt texture for urban/street footwear
- Subtle noise overlay (0.04 opacity) on any flat dark section
- Never apply texture directly over photography

**What to synthesize from Nike:**
- Full-bleed product imagery with type overlay — the product is the hero
- Kinetic energy even in still images — composition suggests motion
- Copy is active and specific: "Built for the track. Worn everywhere else."

**What to synthesize from Gymshark:**
- Community as brand — people in product, not product alone
- Dark-to-light visual narrative that guides the scroll
- Strong mobile hero — product fills the frame

**What to synthesize from Allbirds:**
- Environmental storytelling — material + sustainability woven into product copy
- Restraint: white space, limited palette, letting the product breathe
- Navigation that doesn't compete with the product

**Typography direction (DTC):**
- Display: varies widely by brand — match the product personality
- Body: highly readable at 16px+ on mobile — avoid thin weights
- Luxury DTC: refined serif display + neutral sans body

**Avoid:**
- "Shop now" as a CTA (generic)
- Reviews without photos
- Product pages with 8 different CTAs competing

---

### Real Estate / Luxury Property

**Pattern library:**
- Photography is everything — image quality determines trust
- Minimal chrome — the property is the product, the UI is the frame
- Search and filter: prominent, functional, not buried
- Luxury signal: restraint and whitespace, not gold color
- Typography: refined, slightly editorial
- Agent/team page: real photos, real names, real credentials

**What to synthesize from Compass:**
- Search as the primary interaction — everything leads to finding a property
- Card layouts that let photography dominate
- Clean nav with location intelligence built in

**What to synthesize from Sotheby's / Aman:**
- The page breathes — generous padding, nothing rushed
- Typography does the emotional work — large, refined, unhurried
- Color palette: near-white surfaces, muted neutrals, no accent gimmicks
- Hero that establishes place and aspiration, not features

**Typography direction (real estate / luxury):**
- Display: Gilda Display, EB Garamond, Canela direction, Libre Baskerville
- Body: Raleway, Josefin Sans, or a humanist sans with good weight range
- Large tracking on headlines for luxury feel (-0.02em to -0.04em)

**Avoid:**
- Auto-playing property tour videos in the hero
- Bright accent colors that feel out of place (blue CTAs on a luxury property site)
- More than 2–3 properties above the fold

---

### Agency / Creative Studio

**Pattern library:**
- The site itself is the portfolio — if it doesn't demonstrate craft, nothing will
- Case study structure: problem → process → result → impact
- Motion is expected and should be high quality (Tier 4–5 appropriate)
- Team: real names, real photos, real roles — not a wall of LinkedIn headshots
- Contact: one clear path, no phone trees

**What to synthesize from Instrument:**
- Bold, opinionated type at large scale
- Case studies that show thinking, not just final output
- Navigation that feels designed, not default

**What to synthesize from Fantasy Interactive:**
- Interaction design as brand expression — every hover state is a statement
- Dark-dominant with strategic color accents
- Portfolio pieces presented with editorial care

**What to synthesize from Metalab / Ramotion:**
- "The work first" philosophy — case studies dominate
- Clear specialization communicated immediately
- Photography and device mockups that look hand-produced, not templated

**Typography direction (agency):**
- Display: Archivo Black, Unbounded, Barlow Condensed ExtraBold — or a striking serif
- Body: neutral complement — Mulish, Noto Sans, Karla
- Large size + tight tracking on hero = immediate confidence signal

**Avoid:**
- Stock award graphics ("Agency of the Year" badges)
- Client list without case studies
- Process diagrams that explain "our unique methodology"

---

### Healthcare / Wellness

**Pattern library:**
- Accessibility is not optional — WCAG AA minimum, aim for AAA
- Trust signals are medical-grade: credentials, certifications, named practitioners
- Calm color palettes — nothing high-saturation
- Copy: empathetic and human, not clinical jargon unless B2B
- Navigation: clear, simple — users may be stressed or unwell

**What to synthesize from One Medical:**
- Warmth without sacrificing professionalism
- Photography of real care moments — not stock hospital corridors
- Onboarding flow clarity — every step is explained

**What to synthesize from Headspace:**
- Illustration as a brand differentiator — not photos
- Color and motion that are calming, not urgent
- Navigation with very few options — reduce cognitive load

**Typography direction (healthcare):**
- Display: Nunito, Quicksand for wellness — humanist, rounded, approachable
- Display: More structured sans for clinical/B2B — Barlow, Karla
- Body: extremely high legibility — 17–18px minimum, 1.7 line height
- No thin weights anywhere

**Avoid:**
- Bright red as an accent (implies emergency)
- Dense text blocks that feel clinical
- Animation that creates urgency or anxiety

---

### Personal Portfolio

**Pattern library:**
- The work is the primary content — everything else is framing
- Simple navigation — 4 items maximum: Work, About, Writing (maybe), Contact
- Contact: prominent and frictionless — the whole point is to be hired
- Personality comes through in small details, not big declarations

**What to synthesize from Brittany Chiang:**
- Clean, organized — every project presented with context
- Monospace/terminal aesthetic that fits the developer persona
- Scrolling single-page structure with clear sections

**What to synthesize from Lee Robinson:**
- Writing as part of the portfolio — demonstrates thinking
- Minimal chrome, content-forward
- Personal brand that feels genuine, not performed

**What to synthesize from Josh Comeau:**
- Interactive elements that demonstrate skill in context
- Color and typography that are distinctive without being distracting
- Writing that makes you want to hire the person

**Typography direction (portfolio):**
- Display: Hanken Grotesk, Archivo, or something with personality that fits you
- Body: highly readable, generous line height — portfolio is often long-form
- Mono: for code snippets, terminal aesthetics where appropriate

**Avoid:**
- "I'm a full-stack developer passionate about creating seamless user experiences"
- Animated skill bars (they're meaningless)
- Every project in an identical card grid

---

## Additional Inspiration Sources

**Three sites that consistently generate useful patterns:**
- trylyto.com — clean SaaS, well-proportioned
- db-longbow.webflow.io — editorial dark UI, strong typography
- noomoagency.com — agency with craft and restraint

**What to look for in any reference site:**
1. What does the hero communicate in 3 seconds without reading?
2. Where does the eye go first, second, third?
3. How does the nav behave as you scroll?
4. What happens on hover on the primary CTA?
5. How does it hold up on a 375px mobile screen?
6. What is the spacing rhythm — is it consistent?
7. Is there a clear typographic system or ad-hoc choices?
8. Does the footer feel like an afterthought or part of the design?

---

## Color Combinations by Niche

All values in OKLCH. Hex equivalents noted where helpful.
Each palette: surface · text · accent · border.
Use as starting points — always tint neutrals toward the brand hue.

---

### SaaS / Developer Tools

**1 — Stripe-direction (dark navy + indigo)**
Reads as: financial infrastructure, serious craft, trusted at scale.
- Surface:  `oklch(97% 0.006 260)` — blue-tinted near-white
- Text:     `oklch(14% 0.025 260)` — deep navy (#0A2540 direction)
- Accent:   `oklch(58% 0.22 278)`  — brand indigo (#635BFF direction)
- Border:   `oklch(88% 0.01 260)`

**2 — Linear-direction (cool dark + purple)**
Reads as: engineering discipline, product focus, premium B2B tool.
- Surface:  `oklch(13% 0.01 270)`  — near-black, cool
- Text:     `oklch(96% 0.005 270)` — off-white
- Accent:   `oklch(62% 0.2 300)`   — muted purple
- Border:   `oklch(24% 0.012 270)`

**3 — Vercel-direction (monochrome + rare blue)**
Reads as: infrastructure, engineered to look designed, speed.
- Surface:  `oklch(10% 0.005 260)` — tinted near-black
- Text:     `oklch(97% 0.003 260)` — #FAFAFA
- Accent:   `oklch(65% 0.18 250)`  — rare blue touch
- Border:   `oklch(22% 0.008 260)`

**4 — Notion-direction (warm white + black)**
Reads as: calm productivity, simple, human, no ego.
- Surface:  `oklch(98% 0.005 80)`  — warm white, slight yellow tint
- Text:     `oklch(16% 0.008 60)`  — warm near-black
- Accent:   `oklch(52% 0.16 260)`  — calm blue, used sparingly
- Border:   `oklch(88% 0.008 80)`

**5 — Mercury-direction (dark purple + warm neutrals)**
Reads as: premium B2B banking, not a traditional bank.
- Surface:  `oklch(15% 0.018 300)` — deep purple-black
- Text:     `oklch(94% 0.008 60)`  — warm off-white
- Accent:   `oklch(68% 0.14 300)`  — muted purple
- Border:   `oklch(26% 0.015 300)`

**6 — Clay-direction (warm surface + editorial type)**
Reads as: opinionated, CRM for people with taste, design-literate B2B.
- Surface:  `oklch(96% 0.012 60)`  — warm cream
- Text:     `oklch(18% 0.015 50)`  — warm dark brown-black
- Accent:   `oklch(58% 0.22 35)`   — warm orange-red
- Border:   `oklch(86% 0.015 60)`

---

### AI Products

**1 — Anthropic-direction (deep teal + warm off-white)**
Reads as: values-driven, thoughtful, trustworthy, not cold.
- Surface:  `oklch(97% 0.008 185)` — slightly teal-tinted white
- Text:     `oklch(18% 0.02 200)`  — deep cool-warm dark
- Accent:   `oklch(52% 0.18 185)`  — restrained teal
- Border:   `oklch(87% 0.01 185)`

**2 — OpenAI-direction (stark near-white + black)**
Reads as: authority, neutral intelligence, no personality as the personality.
- Surface:  `oklch(99% 0.002 0)`   — almost pure white
- Text:     `oklch(11% 0.005 0)`   — near-black
- Accent:   `oklch(55% 0.15 160)`  — green, used very rarely
- Border:   `oklch(90% 0.004 0)`

**3 — Perplexity-direction (dark + teal)**
Reads as: search clarity, focused, fast, information-first.
- Surface:  `oklch(16% 0.01 215)`  — dark blue-gray
- Text:     `oklch(95% 0.006 215)`
- Accent:   `oklch(65% 0.2 195)`   — teal
- Border:   `oklch(26% 0.012 215)`

**4 — Cursor-direction (dark + electric blue)**
Reads as: developer precision, dark IDE energy, fast.
- Surface:  `oklch(12% 0.008 255)` — very dark blue-black
- Text:     `oklch(96% 0.005 255)`
- Accent:   `oklch(66% 0.24 255)`  — electric blue
- Border:   `oklch(22% 0.012 255)`

---

### Fintech / Financial Services

**1 — Trust navy + gold (heritage fintech)**
Reads as: institutional trust, established wealth, private banking.
- Surface:  `oklch(97% 0.006 250)`
- Text:     `oklch(18% 0.03 250)`  — deep navy (#1B2A4A direction)
- Accent:   `oklch(72% 0.12 80)`   — warm gold (#C69B3C direction)
- Border:   `oklch(86% 0.01 250)`

**2 — Wise-direction (forest green + off-white)**
Reads as: transparent, international, confident, not a bank.
- Surface:  `oklch(97% 0.01 145)`  — very light green-tinted
- Text:     `oklch(20% 0.04 145)`  — forest green (#163300 direction)
- Accent:   `oklch(82% 0.22 135)`  — bright green (#9FE870 direction)
- Border:   `oklch(86% 0.015 145)`

**3 — Brex-direction (warm white + orange)**
Reads as: startup confidence, bold, not pretending to be a bank.
- Surface:  `oklch(98% 0.004 60)`
- Text:     `oklch(14% 0.01 50)`
- Accent:   `oklch(68% 0.24 45)`   — warm orange
- Border:   `oklch(88% 0.008 60)`

**4 — Klarna-direction (violet-black + pink)**
Reads as: consumer fintech, playful confidence, fashion-forward payments.
- Surface:  `oklch(97% 0.003 340)` — off-white (#F9F8F5 direction)
- Text:     `oklch(10% 0.018 300)` — violet-black (#0B051D direction)
- Accent:   `oklch(78% 0.18 355)`  — Klarna pink (#FFA8CD direction)
- Border:   `oklch(88% 0.006 340)`

**5 — Ramp-direction (clean white + green)**
Reads as: clarity, no-bullshit expense management, modern CFO tool.
- Surface:  `oklch(99% 0.003 145)`
- Text:     `oklch(14% 0.015 155)`
- Accent:   `oklch(56% 0.2 150)`   — confident green
- Border:   `oklch(90% 0.006 145)`

---

### E-Commerce / DTC

**1 — Nike-direction (pure black + white)**
Reads as: athletic authority, restraint as power, product IS the color.
- Surface:  `oklch(99% 0 0)`       — pure white
- Text:     `oklch(9% 0.003 0)`    — #111111
- Accent:   `oklch(62% 0.24 40)`   — orange, used rarely
- Border:   `oklch(88% 0 0)`

**2 — Dark editorial DTC (Gymshark-direction)**
Reads as: community, kinetic, dark hero energy, performance brand.
- Surface:  `oklch(12% 0.008 250)`
- Text:     `oklch(96% 0.005 250)`
- Accent:   `oklch(76% 0.2 195)`   — cyan-teal
- Border:   `oklch(24% 0.01 250)`

**3 — Allbirds-direction (natural + sustainable)**
Reads as: material-first, earthy, premium sustainable brand.
- Surface:  `oklch(96% 0.012 80)`  — warm cream
- Text:     `oklch(22% 0.015 70)`  — warm dark brown
- Accent:   `oklch(58% 0.16 145)`  — muted sage green
- Border:   `oklch(86% 0.016 80)`

**4 — Apple-direction (white + silver)**
Reads as: product photography IS the palette, type does the hierarchy work.
- Surface:  `oklch(99% 0.002 250)`
- Text:     `oklch(11% 0.005 250)`
- Accent:   `oklch(60% 0.14 250)`  — system blue, used minimally
- Border:   `oklch(88% 0.005 250)`

**5 — Bold outdoor / mission-driven DTC (Patagonia-direction)**
Reads as: outdoor brand, mission-first, warm not cold.
- Surface:  `oklch(97% 0.008 55)`  — warm off-white
- Text:     `oklch(16% 0.02 50)`
- Accent:   `oklch(52% 0.22 30)`   — deep terracotta-red
- Border:   `oklch(86% 0.012 55)`

---

### Luxury / Premium

**1 — Onyx + ivory (Chanel / Rolex direction)**
Reads as: heritage houses, private clubs, nothing to prove.
- Surface:  `oklch(97% 0.006 80)`  — ivory (#F4EADE direction)
- Text:     `oklch(10% 0.005 60)`  — onyx near-black
- Accent:   `oklch(72% 0.1 80)`    — warm taupe — no loud accent
- Border:   `oklch(84% 0.012 80)`

**2 — Onyx + gold (jewelry / watchmaking)**
Reads as: dark velvet box, stones catching light, Rolex.
- Surface:  `oklch(11% 0.01 80)`   — near-black warm
- Text:     `oklch(96% 0.008 80)`  — warm off-white
- Accent:   `oklch(72% 0.12 80)`   — gold (#C69B3C direction)
- Border:   `oklch(22% 0.015 80)`

**3 — Aman / Rosewood direction (emerald + champagne)**
Reads as: luxury hospitality, golden hour, 20-year wayfinding.
- Surface:  `oklch(96% 0.012 80)`  — champagne (#EBDAB0 direction)
- Text:     `oklch(22% 0.04 160)`  — Harrods emerald dark (#0D4C3C direction)
- Accent:   `oklch(48% 0.18 155)`  — rich emerald
- Border:   `oklch(84% 0.018 80)`

**4 — Coastal Mediterranean (quiet luxury)**
Reads as: Aman beach club, stone and sand, effortless.
- Surface:  `oklch(95% 0.014 80)`  — warm sand
- Text:     `oklch(28% 0.02 80)`   — warm taupe-dark
- Accent:   `oklch(58% 0.1 200)`   — washed-out Mediterranean blue
- Border:   `oklch(84% 0.018 80)`

**5 — Porsche-direction (dark + carmine red)**
Reads as: engineering as luxury, precision, performance heritage.
- Surface:  `oklch(14% 0.008 250)`
- Text:     `oklch(94% 0.006 250)`
- Accent:   `oklch(55% 0.24 25)`   — carmine red
- Border:   `oklch(28% 0.01 250)`

---

### Agency / Creative Studio

**1 — Near-black + chartreuse (bold agency)**
Reads as: opinionated, makes a statement, work-first confidence.
- Surface:  `oklch(12% 0.008 120)` — very dark, slight green cast
- Text:     `oklch(95% 0.01 120)`
- Accent:   `oklch(88% 0.28 128)`  — chartreuse (#C8FF00 direction)
- Border:   `oklch(24% 0.012 120)`

**2 — Cream + hot pink (bold editorial agency)**
Reads as: fearless, maximalist, design-as-personality.
- Surface:  `oklch(96% 0.012 80)`  — warm cream (#F5F0E8 direction)
- Text:     `oklch(14% 0.01 50)`   — charcoal (#1A1A1A direction)
- Accent:   `oklch(66% 0.32 355)`  — hot pink
- Border:   `oklch(84% 0.018 80)`

**3 — Instrument-direction (pure black + white, type-first)**
Reads as: work speaks for itself, type IS the brand expression.
- Surface:  `oklch(10% 0.004 260)`
- Text:     `oklch(97% 0.003 260)`
- Accent:   `oklch(97% 0.003 260)` — white as accent, no color needed
- Border:   `oklch(22% 0.006 260)`

**4 — Dark blue-black + electric (motion-forward studio)**
Reads as: technical craft, interactive, Framer / Ramotion direction.
- Surface:  `oklch(13% 0.015 270)`
- Text:     `oklch(95% 0.006 270)`
- Accent:   `oklch(70% 0.28 270)`  — electric violet-blue
- Border:   `oklch(25% 0.018 270)`

**5 — Off-white + terracotta (warm creative studio)**
Reads as: human-centered, brand identity work, craft-first.
- Surface:  `oklch(97% 0.01 60)`
- Text:     `oklch(18% 0.018 55)`
- Accent:   `oklch(60% 0.2 40)`    — warm terracotta
- Border:   `oklch(86% 0.014 60)`

---

### Healthcare / Wellness

**1 — Clinical trust (slate + teal)**
Reads as: patient portal, clean, stable, modern clinic.
- Surface:  `oklch(98% 0.004 215)` — near-white, slightly cool
- Text:     `oklch(22% 0.018 220)` — deep slate
- Accent:   `oklch(60% 0.18 195)`  — teal, calm not aggressive
- Border:   `oklch(88% 0.008 215)`

**2 — Hims-direction (charcoal + white)**
Reads as: modern consumer health, editorial simplicity, not clinical.
- Surface:  `oklch(99% 0.002 0)`
- Text:     `oklch(22% 0.006 0)`   — #333333
- Accent:   `oklch(40% 0.006 0)`   — dark gray used sparingly
- Border:   `oklch(88% 0.004 0)`

**3 — Headspace-direction (warm coral + cream)**
Reads as: calming, approachable, meditation, not a hospital.
- Surface:  `oklch(97% 0.01 60)`   — warm cream
- Text:     `oklch(20% 0.018 50)`
- Accent:   `oklch(68% 0.2 30)`    — soft coral-orange
- Border:   `oklch(88% 0.012 60)`

**4 — Healing green (wellness / natural health)**
Reads as: gut health, supplements, clean living, calm growth.
- Surface:  `oklch(97% 0.01 145)`
- Text:     `oklch(22% 0.04 150)`  — deep forest green
- Accent:   `oklch(62% 0.18 145)`  — mid green
- Border:   `oklch(87% 0.014 145)`

**5 — Serenity blue (mental health / therapy / meditation)**
Reads as: calm, trustworthy, sky and water, non-threatening.
- Surface:  `oklch(97% 0.008 240)` — sky-tinted white
- Text:     `oklch(22% 0.025 245)` — deep ocean blue
- Accent:   `oklch(62% 0.18 235)`  — clear blue
- Border:   `oklch(87% 0.01 240)`

---

### Real Estate / Luxury Property

**1 — Compass-direction (clean white + black)**
Reads as: modern luxury brokerage, search-first, property IS the brand.
- Surface:  `oklch(99% 0.003 0)`
- Text:     `oklch(10% 0.004 0)`
- Accent:   `oklch(52% 0.008 0)`   — mid-gray, type-only hierarchy
- Border:   `oklch(88% 0.004 0)`

**2 — Warm cream + dark navy (Sotheby's direction)**
Reads as: heritage luxury, auction house gravitas, old-money positioning.
- Surface:  `oklch(96% 0.012 80)`  — warm cream
- Text:     `oklch(18% 0.03 250)`  — deep navy
- Accent:   `oklch(52% 0.18 250)`  — blue for CTAs only
- Border:   `oklch(84% 0.016 80)`

**3 — Stone + warm white (boutique luxury property)**
Reads as: architectural photography, restraint, Mediterranean villa energy.
- Surface:  `oklch(97% 0.01 80)`
- Text:     `oklch(30% 0.015 70)`  — warm stone-dark
- Accent:   `oklch(52% 0.06 80)`   — barely-there warm taupe
- Border:   `oklch(85% 0.015 80)`

---

### Personal Portfolio

**1 — Developer (dark navy + mint terminal)**
Reads as: Brittany Chiang direction, craft-forward, developer identity.
- Surface:  `oklch(14% 0.01 155)`  — #0A192F direction
- Text:     `oklch(88% 0.012 155)` — light slate
- Accent:   `oklch(75% 0.2 155)`   — mint green (#64FFDA direction)
- Border:   `oklch(26% 0.015 155)`

**2 — Minimal white (Lee Robinson direction)**
Reads as: writing-forward, content over chrome, product thinker.
- Surface:  `oklch(99% 0.002 0)`
- Text:     `oklch(13% 0.006 0)`
- Accent:   `oklch(55% 0.18 255)`  — calm blue for links only
- Border:   `oklch(90% 0.004 0)`

**3 — Warm editorial (Josh Comeau direction)**
Reads as: interactive, personality, design-literacy signal.
- Surface:  `oklch(97% 0.01 60)`
- Text:     `oklch(16% 0.012 55)`
- Accent:   `oklch(62% 0.24 310)`  — warm pink-purple
- Border:   `oklch(87% 0.014 60)`

**4 — Bold monochrome (agency-adjacent portfolio)**
Reads as: opinionated designer, type is the portfolio.
- Surface:  `oklch(12% 0.005 260)`
- Text:     `oklch(96% 0.004 260)`
- Accent:   `oklch(82% 0.24 80)`   — warm yellow, single accent only
- Border:   `oklch(24% 0.008 260)`

---

### Usage Notes

- Every surface color above is tinted toward the brand hue — even at 0.004–0.012 chroma. Pure `oklch(97% 0 0)` is always slightly colder and flatter than these tinted equivalents.
- Accent colors are used sparingly — one per site, on CTAs and key interactions only. Never more than one true accent.
- "Direction" palettes are synthesized starting points, not direct brand copies. Adjust L, C, H to match the specific project's voice before shipping.
- For dark-surface palettes: keep text at 94–97% lightness, not pure white. The subtle warmth separates premium from harsh.
- When in doubt, reduce chroma before increasing it. A palette that reads as "clean" is almost always lower-chroma than it initially seems.
