# Confidence & Evidence Protocol

Every IntelliFront output must pass evidence discipline before being finalized.
This file defines the labeling system and the verification checklist.

---

## The Three Labels

### FACT
Directly observable in the provided input.

"Directly observable" means: you can point to the exact element, line of code,
or visible section of the screenshot that supports this claim.

Examples:
- "The hero headline is set in Inter at approximately 48px" (visible in screenshot/code)
- "The CTA button uses `border-left: 4px solid` on the card" (visible in code)
- "There is no pricing information on this page" (directly observable absence)
- "The primary CTA text reads 'Learn more'" (directly readable)

### INFERENCE
A reasonable conclusion derived from observable signals, design principles, or
established UX knowledge. Must be labeled when used.

Inferences are allowed and valuable — they are how we connect observations to
recommendations. They just must be transparent.

Examples:
- "The current line length (~90ch) likely reduces readability for sustained reading"
- "Leading with a feature list in the hero may reduce conversion compared to leading
  with a user outcome" — this is an inference, not a proven fact
- "The typography system appears to use an 8pt grid based on the padding values visible"

### ASSUMPTION
Something not supported by the input that we are speculating about.
Must be labeled and ideally verified or removed.

When to use: only when an assumption is necessary to give useful advice and cannot
be verified from the input.

Examples:
- "(ASSUMPTION: if this targets enterprise buyers, the pricing page omission is especially problematic)"
- "(ASSUMPTION: this appears to be a mobile-first product, though no mobile view was provided)"

When you find yourself making an assumption — ask: can I reframe this as conditional?
"If X is true, then Y" is more honest than stating Y as fact.

---

## Pre-Output Verification Checklist

Run this before finalizing any agent output. Every item must pass.

### Evidence check
- [ ] Every major claim is labeled FACT, INFERENCE, or ASSUMPTION
- [ ] No claim says "users think X" or "users prefer Y" without basis in established UX research
- [ ] No competitor comparisons unless the competitor's site was actually fetched
- [ ] No fabricated metrics (conversion %, user counts, revenue impact)
- [ ] No claims about sections/pages not present in the input

### Copy integrity check
- [ ] Any copy rewrites use only information from the input — no invented features or pricing
- [ ] Any invented copy is labeled as structural template: "[Insert real outcome here]"
- [ ] Testimonial rewrites that use invented names are labeled as templates

### Specificity check
- [ ] Every recommendation is specific enough to act on without guessing
- [ ] "Improve the hero" is never a final recommendation — it must say what to change, how
- [ ] Scores have rationale — not just numbers

### Confidence rating (for every major recommendation)

Before including a recommendation, rate it:

| Rating | Meaning | Label required? |
|--------|---------|----------------|
| HIGH confidence | Grounded in established principles, directly supported by input | No label needed |
| MEDIUM confidence | Well-reasoned inference, common pattern with some variability | "likely" / "commonly associated with" |
| LOW confidence | Speculative, depends on unknown context | "ASSUMPTION" / remove if possible |

Low confidence claims should be removed or reframed as conditional before output.

---

## Language Guidelines by Confidence Level

### For HIGH confidence claims (no label needed):
- "The 3-column icon card grid reduces hierarchy clarity"
- "The heading font (Inter) lacks the character needed for a display role"
- "Missing `:focus-visible` states fail WCAG 2.4.7"

### For MEDIUM confidence claims:
- "likely improves..."
- "commonly associated with higher engagement in..."
- "may reduce cognitive load by..."
- "in top [niche] sites, this pattern is typically..."
- "the research suggests..."

### For LOW confidence / ASSUMPTION:
- "(ASSUMPTION: if the target audience is non-technical...)"
- "(If this is a B2B site — which is unconfirmed — then...)"
- "Without seeing the mobile view, this is speculative: the layout may..."

### Forbidden language (never use for causal claims):
- "This will increase conversions by X%"
- "Users will prefer..."
- "This is scientifically proven to..."
- "This is objectively better because..."
- "Research shows that exactly..."

---

## Special Rules by Agent

### Agent 2 (Design Intelligence) — External Research
When referencing external sites or industry patterns:
- ✅ "Commonly seen in top SaaS sites, the hero typically..."
- ✅ "In the direction of what [site] does with typography..."
- ❌ "Stripe uses exactly this pattern" (unless you have fetched stripe.com)
- ❌ "This is what all fintech sites do" (overgeneralization)

### Agent 3 (Slop Detector) — Intent Claims
Never assume designer intent:
- ✅ "This resembles the common AI-generated icon card grid pattern (V3)"
- ✅ "This reads as template-built due to the identical section structure (L2)"
- ❌ "This was generated by AI"
- ❌ "The designer didn't care about X"

### Agent 4 (Conversion) — Impact Claims
All conversion impact claims are MEDIUM confidence unless backed by cited research:
- ✅ "First-person CTAs ('Start my trial') commonly outperform second-person in A/B tests — though results vary by audience (INFERENCE)"
- ❌ "First-person CTAs increase conversions by 25%"
- ❌ "This will double your signups"

### Agent 5 (Godmode) — Scope Claims
Godmode must not overstate what a redesign will achieve:
- ✅ "The planned changes address the primary trust and hierarchy issues. If implemented well, this should significantly improve first impressions."
- ❌ "After this redesign, your conversion rate will improve by 40%"
- ❌ "This is exactly what your site needs"

---

## When to Remove a Claim Entirely

Remove a claim rather than label it ASSUMPTION when:
1. It requires information not in the input and the label would undermine the usefulness of the finding
2. The claim is LOW confidence and the output is already thorough without it
3. The claim is speculative about user psychology without grounding in established principles
4. It would require a disclaimer longer than the claim itself to be honest

A shorter, more precise output is always better than a longer one padded with low-confidence speculation.
