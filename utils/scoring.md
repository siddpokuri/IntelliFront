# Scoring System

Scoring formulas and guidelines for all IntelliFront agents.
Scores communicate severity quickly — they are tools for the user, not grades.

---

## Agent 1 — Frontend Critic Scores

Six dimensions, each 0–100.

### Calculation method

Each dimension starts at 100. Deduct per issue found:

| Severity | Deduction |
|----------|-----------|
| HIGH     | 15–25 pts (use judgment based on impact) |
| MEDIUM   | 6–12 pts |
| LOW      | 2–4 pts |

Floor: 0. Never negative.

### Dimension descriptions

**Visual Hierarchy (0–100)**
Does the eye know where to go without effort?
- 90–100: Clear, intentional hierarchy — heading → sub → body → CTA reads in under 3 seconds
- 70–89: Mostly clear with 1–2 competing elements
- 50–69: Flat — several elements fight for attention
- 30–49: No clear focal point — everything is equal weight
- 0–29: Actively confusing — the eye has nowhere to land

**Typography (0–100)**
Does the type system create hierarchy and reflect the brand?
- 90–100: Cohesive system, distinctive display face, correct scale and spacing
- 70–89: Works well, minor inconsistencies
- 50–69: Generic font choices, inconsistent scale, or poor legibility
- 30–49: Banned patterns present (Inter as display, gradient text, etc.)
- 0–29: Multiple HIGH typography slop patterns + poor legibility

**Spacing & Layout (0–100)**
Is there a consistent spatial system? Does the layout breathe correctly?
- 90–100: Clear spacing system, section rhythm varies appropriately, no orphaned elements
- 70–89: Generally consistent with some rhythm issues
- 50–69: Random spacing values, or uniform spacing with no hierarchy
- 30–49: Cramped sections, or wasteful sections, or misaligned grid
- 0–29: No apparent system — arbitrary spacing throughout

**Accessibility (0–100)**
Can all users access and understand this content?
- 90–100: WCAG AA throughout, focus states, semantic markup, alt text
- 70–89: AA on most elements, minor gaps
- 50–69: Several contrast failures or missing focus states
- 30–49: Multiple HIGH accessibility failures
- 0–29: Systematic accessibility failures — color as sole differentiator, no focus states, etc.

**Trust Perception (0–100)**
Does this site feel like it belongs to a real, credible organization?
- 90–100: Polished, specific, real humans visible, strong proof
- 70–89: Generally credible with some generic elements
- 50–69: Several trust signals missing or weak
- 30–49: Multiple trust-eroding patterns present
- 0–29: Actively appears fake or low-quality

**Consistency (0–100)**
Do components follow a coherent visual language across the page?
- 90–100: Clear design system evident — buttons, cards, type all consistent
- 70–89: Mostly consistent with some component drift
- 50–69: Multiple inconsistencies — buttons vary, type is ad-hoc
- 30–49: No apparent consistency — components each have own treatment
- 0–29: Actively contradictory styles in use simultaneously

---

## Agent 3 — Slop Detector Scores

### Slop Score (0–100, lower is better)

Starts at 0. Add per finding:
- HIGH severity pattern: +10
- MEDIUM severity pattern: +5
- LOW severity pattern: +2
- Cap at 100

**Thresholds:**
| Score | Meaning |
|-------|---------|
| 0–15  | Minimal slop — site reads as professionally designed |
| 16–35 | Low slop — a few generic choices, overall credible |
| 36–55 | Moderate slop — clearly template-influenced, multiple tells |
| 56–75 | High slop — multiple HIGH-severity patterns, trust is eroded |
| 76–100 | Very high slop — AI-generated or heavily template-built with no distinctive choices |

### Credibility Score (0–100, higher is better)

Starts at 100. Subtract per finding:
- HIGH severity pattern: −10
- MEDIUM severity pattern: −5
- LOW severity pattern: −2
- Floor at 0

**Thresholds:**
| Score | Meaning |
|-------|---------|
| 85–100 | Highly credible — builds immediate trust |
| 70–84  | Credible with fixable gaps |
| 50–69  | Questionable — a discerning visitor would have doubts |
| 30–49  | Low credibility — multiple trust-eroding elements present |
| 0–29   | Not credible — would actively disqualify this vendor for many buyers |

### Professionalism Score (0–100, higher is better)

This is a holistic judgment, not calculated by formula. Answer:

**Does this look like it was made by a professional designer who made intentional choices,
or does it look like it was generated or built from a template?**

Guiding questions:
- Is there a distinctive font choice that feels chosen for this brand? (+10–15)
- Does the spacing system feel intentional? (+10)
- Are there any design choices that make you ask "that's interesting"? (+10–20)
- Is the color palette brand-specific or default? (+0 if default, +10–15 if distinctive)
- Do interactions feel designed? (+0–15)
- Would an experienced designer immediately peg this as AI-generated? (−20–30 if yes)

---

## Agent 4 — Conversion Scores

### Conversion Score (0–100)

Holistic assessment of how effectively the page drives its primary conversion action.

**Calculation factors:**
| Factor | Max contribution |
|--------|-----------------|
| Hero clarity (headline + CTA) | 25 pts |
| Primary CTA quality | 20 pts |
| Trust/proof quality | 20 pts |
| Funnel friction level | 20 pts |
| Pricing clarity (if applicable) | 15 pts |

**Score meaning:**
| Range | Meaning |
|-------|---------|
| 85–100 | Optimized — best practices followed throughout |
| 70–84  | Good — a few high-ROI improvements available |
| 50–69  | Mediocre — meaningful conversion friction present |
| 30–49  | Poor — multiple conversion blockers |
| 0–29   | Broken — the conversion path is unclear or non-functional |

### Trust Score (0–100)

Specific to conversion-relevant trust signals:
- Named testimonials with company/role: +15 each (cap at 30)
- Logo wall with context: +10
- Security/compliance signals: +10
- Real pricing visible: +10
- Contact/team visible: +10
- Founder/team story: +10
- Press coverage: +5
- No proof at all: start at 20 max

### Offer Clarity (0–100)

Can a visitor understand what they get and what it costs in 10 seconds?
- 90–100: Crystal clear — pricing visible, value specific, CTA obvious
- 70–89: Mostly clear with one or two ambiguities
- 50–69: Confusing or vague value proposition, or hidden pricing
- 0–49: Cannot determine what the product does or what it costs

---

## Godmode Score Display

Godmode shows both Current and Post-Redesign Target scores.

**Current:** calculated as above from input.

**Post-Redesign Target:** what the scores should reach after implementing all
Guaranteed Improvements. Do not promise the target — frame as:
"Based on the planned changes, these dimensions should reach approximately..."

Be conservative: if current Visual Hierarchy is 38 and the fix is significant,
target 72–78, not 95. Scores of 95+ require genuinely exceptional execution
and should not be promised.

---

## Score Presentation Rules

1. Always show scores in a table, not inline text
2. Always include a brief rationale column explaining the score
3. Never use scores as the headline — lead with the most important finding
4. For Godmode: always show current vs. target side by side
5. Low scores are not insults — frame them as opportunity
6. High scores should still note what would push them higher
