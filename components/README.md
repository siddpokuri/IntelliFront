# IntelliFront Component Library

This library provides reference implementations for the most common website sections.
Each component is a starting point — adapt freely to match the site's design system.

Components are written in semantic HTML + self-contained CSS. They are not a framework.
Generated code does not need to import or reference these files — they exist to establish
quality baselines and demonstrate IntelliFront's design principles in working code.

---

## Design Principles Encoded in Every Component

1. **Mobile-first** — all layouts start at 375px width
2. **Semantic HTML** — correct element types, not `<div>` soup
3. **Full interaction states** — hover, active (scale(0.97)), focus-visible on all interactive elements
4. **No external dependencies** — system font fallbacks, picsum for images
5. **Motion tier aware** — animations commented with their tier
6. **Accessible by default** — aria labels, roles, proper heading hierarchy
7. **No banned patterns** — see `styles/design-system.md` Absolute Bans section

---

## Component Files

| File | Contents |
|------|----------|
| `nav.html` | Sticky minimal nav + mobile hamburger |
| `hero.html` | 4 hero variants: split, centered editorial, product-focused, full-bleed |
| `cards.html` | Feature strips, stat blocks, testimonial layouts — not icon-card grids |
| `cta.html` | CTA section variants: minimal, full-width, dark editorial |
| `footer.html` | Footer variants: minimal, structured, editorial |
| `buttons.html` | 15 button variants with full usage guide and decision notes |
| `interactive.html` | 22 interactive components: toggle switches (pill/flat/glow), checkboxes (flip/wave), radio groups (tile/vertical glider), loaders (square/orbit/tower/radial/pulse), range slider, tab bars (pill/underline/segmented), status badges, step progress indicator |
| `ui-kit.html` | Extended micro-components: share tooltip, 3D tilt card, blob-glow card, dark pill search, outlined input, flip auth form, shake tooltip, skew tooltip |

---

## Component Usage in Agent Output

**Buttons are never optional.** Every generated site must use at least one named button
variant from `ui-kit.html`. A plain filled rectangle is the floor — not the default.
The decision tree in `agents/05-godmode.md` and `agents/02-design-intelligence.md`
defines which variant to pick per context. Adapt all colors to the project's OKLCH system.

For all other components, agents should use them as the starting point, not a fallback.
Pull from the kit first, adapt to the design system, then generate custom only if the
kit genuinely doesn't fit. "When in doubt, omit" is not the stance — "when in doubt,
try the nearest kit variant first" is.

---

## Common Customization Points

For any component, these are the primary customization variables:

```css
/* Override these to match the target site's design system */
--font-display: 'Your Display Font', system-ui, sans-serif;
--font-body:    'Your Body Font', system-ui, sans-serif;
--color-bg:      oklch(97% 0.006 250);
--color-text:    oklch(15% 0.01 250);
--color-accent:  oklch(55% 0.18 250);
--color-border:  oklch(88% 0.008 250);
--space-section: clamp(4rem, 8vw, 8rem);
```

---

## What Is Deliberately Absent

These component types are not included because they are the source of most design slop:

- ❌ 3-column icon + heading + 2-line card grid
- ❌ Auto-scrolling testimonial carousel
- ❌ "Why Choose Us" / "Our Values" section
- ❌ Stats block (10M users / 99.9% uptime) without narrative
- ❌ Generic logo wall with no context

If you need a feature section, use the **feature strips** in `cards.html`.
If you need testimonials, use the **long-form testimonial** or **named quote** variants.
If you need stats, wrap them in narrative — see the **stat narrative** variant in `cards.html`.
