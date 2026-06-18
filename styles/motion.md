# Motion Reference

This file is the motion companion to `styles/design-system.md`. The design system contains
the motion tier framework. This file contains implementation patterns, decision logic,
and advanced techniques for Tier 4–5 work.

Read this before adding any animation beyond a basic fade. Read this especially before
any Tier 4–5 output in Agent 2, Godmode, or component generation.

---

## The First Question

Before any animation: **what breaks if this doesn't move?**

If the answer is "nothing" — the animation is decoration. Decoration is allowed at Tier 4–5.
But it must still earn its place by making the brand feel more alive, not just more busy.

The second question: **does the motion match the brand's energy tier?**

A legal firm at Tier 4 would be a mismatch. A creative agency at Tier 1 would be a waste.
The tier is not a complexity dial — it is a brand-fit dial.

---

## Tier Quick Reference

| Tier | Motion vocabulary | Representative brands |
|------|------------------|----------------------|
| 1 — Still | Opacity only. Everything else static. | Legal, institutional healthcare, government |
| 2 — Grounded | Subtle fadeUp entrances. Scale on press. That's it. | B2B SaaS, finance tools, HR software |
| 3 — Alive | Spring-ish hovers, scroll reveals, stagger. | Consumer SaaS, dev tools, modern fintech |
| 4 — Expressive | Kinetic type, magnetic interactions, parallax, clip-path reveals | Agencies, DTC, AI products, entertainment |
| 5 — Cinematic | 3D, page transitions, scroll storytelling, physics | Luxury, experimental portfolios, art direction |
| 6 — Editorial Cinematic | Scroll-scrubbed video, pinned narrative stacks, formation galleries | Flagship launches, agency hero moments, opt-in only |

---

## Scroll Reveal Patterns

### Directional Reveals (Tier 3–5)

Text and images entering from a specific direction create spatial storytelling — the page
feels like a world with depth, not a list of sections. Use direction deliberately:

- **Left → right**: natural reading order, good for text-forward sections
- **Right → left**: creates tension, best for countering the text direction (image enters opposite to copy)
- **Bottom → up**: classic neutral — use sparingly so it doesn't become wallpaper
- **Top → down**: reserved for hero drops or nav reveals
- **Scale from center**: product reveals, feature callouts, high-impact moments
- **Rotate**: product images landing like they were "dropped" — strong for fashion, footwear, DTC

**Pairing rule:** Within a feature strip, alternate directions between paired elements.
Text slides from left, image slides from right. This creates conversation between elements,
not parallel repetition.

```css
[data-reveal] {
  opacity: 0;
  transition: opacity 650ms cubic-bezier(0.23, 1, 0.32, 1),
              transform 650ms cubic-bezier(0.23, 1, 0.32, 1);
}
[data-reveal="left"]   { transform: translateX(-56px); }
[data-reveal="right"]  { transform: translateX(56px); }
[data-reveal="up"]     { transform: translateY(40px); }
[data-reveal="down"]   { transform: translateY(-24px); }
[data-reveal="scale"]  { transform: scale(0.9); }
[data-reveal="rotate"] { transform: translateY(28px) rotate(-4deg); transform-origin: left center; }
[data-reveal="rotate-r"]{ transform: translateY(28px) rotate(4deg); transform-origin: right center; }

[data-reveal].visible {
  opacity: 1;
  transform: none;
}

/* Stagger via CSS custom property set on the element inline */
[data-reveal][data-delay] {
  transition-delay: var(--reveal-delay, 0ms);
}
```

```js
// Set transition-delay from data-delay attribute
document.querySelectorAll('[data-reveal]').forEach(el => {
  const delay = el.dataset.delay || '0';
  el.style.setProperty('--reveal-delay', delay + 'ms');
});

const revealObserver = new IntersectionObserver((entries) => {
  entries.forEach(entry => {
    if (entry.isIntersecting) {
      entry.target.classList.add('visible');
      revealObserver.unobserve(entry.target);
    }
  });
}, { threshold: 0.1, rootMargin: '0px 0px -40px 0px' });

document.querySelectorAll('[data-reveal]').forEach(el => revealObserver.observe(el));
```

```html
<!-- Feature strip with paired directions — text left, image right -->
<section class="feature-strip">
  <div class="feature-strip__content" data-reveal="left" data-delay="0">
    <h2>Built for the long run</h2>
    <p>Every seam, every sole, every stitch — engineered to last.</p>
  </div>
  <div class="feature-strip__visual" data-reveal="right" data-delay="100">
    <img src="..." alt="Shoe detail shot">
  </div>
</section>

<!-- Product card with rotate drop -->
<div class="product-card" data-reveal="rotate" data-delay="0">
  <img src="..." alt="...">
</div>
```

---

### Tier 3 — Intersection Observer fadeUp

```js
const observer = new IntersectionObserver((entries) => {
  entries.forEach(entry => {
    if (entry.isIntersecting) {
      entry.target.classList.add('visible');
      observer.unobserve(entry.target); // only animate once
    }
  });
}, { threshold: 0.15 });

document.querySelectorAll('[data-reveal]').forEach(el => observer.observe(el));
```

```css
[data-reveal] {
  opacity: 0;
  transform: translateY(16px);
  transition: opacity 500ms cubic-bezier(0.23, 1, 0.32, 1),
              transform 500ms cubic-bezier(0.23, 1, 0.32, 1);
}
[data-reveal].visible {
  opacity: 1;
  transform: translateY(0);
}
/* Stagger via delay attribute */
[data-reveal][data-delay="1"] { transition-delay: 80ms; }
[data-reveal][data-delay="2"] { transition-delay: 160ms; }
[data-reveal][data-delay="3"] { transition-delay: 240ms; }
```

### Tier 4 — Clip-path reveal (dramatic)

```css
[data-reveal="clip"] {
  clip-path: inset(0 0 100% 0);
  transition: clip-path 800ms cubic-bezier(0.16, 1, 0.3, 1);
}
[data-reveal="clip"].visible {
  clip-path: inset(0 0 0% 0);
}
```

Works on text, images, and containers. Creates a "curtain lifting" entrance.
Stagger multiple elements with `transition-delay` for a cascade effect.

### Tier 5 — Scroll-linked parallax

```js
// Throttled via rAF — never raw scroll listener
let ticking = false;
window.addEventListener('scroll', () => {
  if (!ticking) {
    requestAnimationFrame(() => {
      const scrollY = window.scrollY;
      document.querySelectorAll('[data-parallax]').forEach(el => {
        const speed = parseFloat(el.dataset.parallax) || 0.3;
        el.style.transform = `translateY(${scrollY * speed}px)`;
      });
      ticking = false;
    });
    ticking = true;
  }
});
```

```html
<!-- data-parallax value = fraction of scroll distance to move -->
<div data-parallax="0.2">moves slower than scroll (foreground)</div>
<div data-parallax="-0.1">moves opposite to scroll (depth)</div>
```

---

## Hover Interaction Patterns

### Tier 3 — Directional fill button

```css
.btn-fill {
  position: relative;
  overflow: hidden;
  z-index: 0;
}
.btn-fill::before {
  content: '';
  position: absolute;
  inset: 0;
  background: var(--color-accent-hover);
  transform: translateY(100%);
  transition: transform 300ms cubic-bezier(0.23, 1, 0.32, 1);
  z-index: -1;
}
.btn-fill:hover::before {
  transform: translateY(0);
}
```

### Tier 4 — Spotlight border (cursor-aware)

```js
document.querySelectorAll('[data-spotlight]').forEach(card => {
  card.addEventListener('mousemove', e => {
    const rect = card.getBoundingClientRect();
    const x = e.clientX - rect.left;
    const y = e.clientY - rect.top;
    card.style.setProperty('--mouse-x', `${x}px`);
    card.style.setProperty('--mouse-y', `${y}px`);
  });
});
```

```css
[data-spotlight] {
  position: relative;
  overflow: hidden;
}
[data-spotlight]::before {
  content: '';
  position: absolute;
  width: 300px;
  height: 300px;
  border-radius: 50%;
  background: radial-gradient(circle, rgba(255,255,255,0.08) 0%, transparent 70%);
  left: var(--mouse-x, -999px);
  top: var(--mouse-y, -999px);
  transform: translate(-50%, -50%);
  pointer-events: none;
  opacity: 0;
  transition: opacity 200ms;
}
[data-spotlight]:hover::before {
  opacity: 1;
}
```

### Tier 4 — Magnetic button

```js
document.querySelectorAll('[data-magnetic]').forEach(btn => {
  btn.addEventListener('mousemove', e => {
    const rect = btn.getBoundingClientRect();
    const x = e.clientX - rect.left - rect.width  / 2;
    const y = e.clientY - rect.top  - rect.height / 2;
    btn.style.transform = `translate(${x * 0.25}px, ${y * 0.25}px)`;
  });
  btn.addEventListener('mouseleave', () => {
    btn.style.transition = 'transform 500ms cubic-bezier(0.34, 1.4, 0.64, 1)';
    btn.style.transform = 'translate(0, 0)';
    setTimeout(() => btn.style.transition = '', 500);
  });
});
```

Keep the pull factor (0.25 above) between 0.15–0.35. Higher feels broken. Lower is invisible.

### Tier 5 — 3D tilt card

```js
document.querySelectorAll('[data-tilt]').forEach(card => {
  const strength = parseFloat(card.dataset.tilt) || 12;
  card.addEventListener('mousemove', e => {
    const rect = card.getBoundingClientRect();
    const x = (e.clientX - rect.left) / rect.width  - 0.5;
    const y = (e.clientY - rect.top)  / rect.height - 0.5;
    card.style.transform = `
      perspective(900px)
      rotateY(${x * strength}deg)
      rotateX(${-y * strength}deg)
      scale(1.02)
    `;
  });
  card.addEventListener('mouseleave', () => {
    card.style.transition = 'transform 600ms cubic-bezier(0.23, 1, 0.32, 1)';
    card.style.transform = 'perspective(900px) rotateY(0) rotateX(0) scale(1)';
    setTimeout(() => card.style.transition = '', 600);
  });
  card.style.transition = 'transform 150ms ease-out';
  card.style.transformStyle = 'preserve-3d';
  card.style.willChange = 'transform';
});
```

Use `strength` of 8–14 for cards. 20+ feels nauseating. Add a subtle glare layer inside
the card that moves opposite to the tilt for the full illusion.

---

## Kinetic Typography (Tier 4–5)

### Marquee / ticker

```html
<div class="marquee" aria-hidden="true">
  <div class="marquee__track">
    <span>Design Systems &nbsp;·&nbsp; </span>
    <span>Frontend Intelligence &nbsp;·&nbsp; </span>
    <span>No More Slop &nbsp;·&nbsp; </span>
    <!-- Duplicate for seamless loop -->
    <span>Design Systems &nbsp;·&nbsp; </span>
    <span>Frontend Intelligence &nbsp;·&nbsp; </span>
    <span>No More Slop &nbsp;·&nbsp; </span>
  </div>
</div>
```

```css
.marquee { overflow: hidden; }
.marquee__track {
  display: flex;
  width: max-content;
  animation: marquee 20s linear infinite;
}
.marquee:hover .marquee__track {
  animation-play-state: paused;
}
@keyframes marquee {
  from { transform: translateX(0); }
  to   { transform: translateX(-50%); }
}
```

### Text scramble effect

```js
class TextScramble {
  constructor(el) {
    this.el = el;
    this.chars = '!<>-_\\/[]{}—=+*^?#';
    this.update = this.update.bind(this);
  }
  setText(newText) {
    const old = this.el.innerText;
    const len = Math.max(old.length, newText.length);
    const promise = new Promise(res => this.resolve = res);
    this.queue = Array.from({ length: len }, (_, i) => ({
      from: old[i] || '',
      to: newText[i] || '',
      start: Math.floor(Math.random() * 20),
      end: Math.floor(Math.random() * 20) + 20,
    }));
    cancelAnimationFrame(this.frameRequest);
    this.frame = 0;
    this.update();
    return promise;
  }
  update() {
    let output = '', complete = 0;
    this.queue.forEach(({ from, to, start, end, char }, i) => {
      if (this.frame >= end) {
        complete++;
        output += to;
      } else if (this.frame >= start) {
        if (!char || Math.random() < 0.28) {
          this.queue[i].char = this.chars[Math.floor(Math.random() * this.chars.length)];
        }
        output += `<span class="scramble-char">${this.queue[i].char}</span>`;
      } else {
        output += from;
      }
    });
    this.el.innerHTML = output;
    if (complete !== this.queue.length) {
      this.frameRequest = requestAnimationFrame(this.update);
      this.frame++;
    } else {
      this.resolve();
    }
  }
}
```

Use for hero headlines on agencies, games, or any product that wants to feel alive on load.

### Staggered word/character split

```js
function splitAndAnimate(el) {
  const words = el.textContent.split(' ');
  el.innerHTML = words.map((word, i) =>
    `<span class="word" style="--i:${i}; display:inline-block; overflow:hidden">
       <span class="word__inner">${word}</span>
     </span>`
  ).join(' ');
}
```

```css
.word__inner {
  display: inline-block;
  transform: translateY(110%);
  animation: wordReveal 700ms cubic-bezier(0.16, 1, 0.3, 1) forwards;
  animation-delay: calc(var(--i) * 60ms);
}
@keyframes wordReveal {
  to { transform: translateY(0); }
}
```

---

## Page Transitions (Tier 5)

Without a framework, use the View Transitions API (Chrome 111+, progressive enhancement):

```js
document.querySelectorAll('a[data-transition]').forEach(link => {
  link.addEventListener('click', async e => {
    e.preventDefault();
    const href = link.href;
    if (!document.startViewTransition) {
      location.href = href; return;
    }
    await document.startViewTransition(async () => {
      const res = await fetch(href);
      const html = await res.text();
      const doc = new DOMParser().parseFromString(html, 'text/html');
      document.querySelector('main').replaceWith(doc.querySelector('main'));
      history.pushState({}, '', href);
    });
  });
});
```

```css
::view-transition-old(root) {
  animation: 300ms cubic-bezier(0.4, 0, 1, 1) both slideOut;
}
::view-transition-new(root) {
  animation: 400ms cubic-bezier(0, 0, 0.2, 1) both slideIn;
}
@keyframes slideOut {
  to { transform: translateY(-30px); opacity: 0; }
}
@keyframes slideIn {
  from { transform: translateY(30px); opacity: 0; }
}
```

---

## 3D Scroll Storytelling (Tier 5)

For fashion, footwear, luxury, and DTC brands — scroll-driven 3D makes product feel
physical. The product should feel like it exists in space, not on a screen.

### Scroll-linked product rotation

```js
// Product spins as user scrolls through the section
const productSection = document.querySelector('.product-3d');
const productImg = productSection.querySelector('.product-3d__img');

const sectionObserver = new IntersectionObserver(([entry]) => {
  if (entry.isIntersecting) {
    window.addEventListener('scroll', onProductScroll, { passive: true });
  } else {
    window.removeEventListener('scroll', onProductScroll);
    productImg.style.transform = '';
  }
});
sectionObserver.observe(productSection);

let rafId;
function onProductScroll() {
  if (rafId) return;
  rafId = requestAnimationFrame(() => {
    const rect = productSection.getBoundingClientRect();
    const progress = 1 - (rect.top + rect.height) / (window.innerHeight + rect.height);
    const clampedProgress = Math.max(0, Math.min(1, progress));
    const rotateY = (clampedProgress - 0.5) * 40; // -20deg to +20deg
    const rotateX = (clampedProgress - 0.5) * -10;
    productImg.style.transform = `
      perspective(1000px)
      rotateY(${rotateY}deg)
      rotateX(${rotateX}deg)
      scale(${1 + clampedProgress * 0.05})
    `;
    rafId = null;
  });
}
```

```css
.product-3d__img {
  will-change: transform;
  transition: transform 100ms linear; /* slight smoothing */
}
```

### Perspective scroll section (entire section tilts into view)

```css
.perspective-section {
  perspective: 1200px;
  overflow: hidden;
}
.perspective-inner {
  transform: rotateX(12deg) scale(0.95);
  transform-origin: center bottom;
  opacity: 0;
  transition: transform 900ms cubic-bezier(0.16, 1, 0.3, 1),
              opacity 700ms cubic-bezier(0.23, 1, 0.32, 1);
}
.perspective-inner.visible {
  transform: rotateX(0deg) scale(1);
  opacity: 1;
}
```

### Floating product on scroll (parallax depth layers)

```html
<div class="float-scene" data-parallax-scene>
  <div class="float-scene__shadow" data-parallax="-0.05"></div>
  <div class="float-scene__product" data-parallax="0.1"></div>
  <div class="float-scene__detail" data-parallax="0.25"></div>  <!-- e.g. laces -->
</div>
```

Each layer moves at a different speed — creates genuine 3D depth without WebGL.
Shadow moves opposite to product to simulate light source remaining fixed.

---

## Tier 6 — Editorial Cinematic (use sparingly, agency/launch sites only)

These patterns sit above Tier 5. They require real engineering effort and meaningfully
heavier JS — reserve them for hero moments on flagship launches, agency portfolios, or
luxury brand sites where the build budget supports it. Never default to these; they are
opt-in upgrades a user requests explicitly, or that Godmode proposes only when motion
tier 3 (cinematic) is selected and the niche is agency / luxury / experimental product.

### Frame-scrubbed video hero (scroll drives playback position)

Instead of a looping background video, the video's *timeline* is bound directly to
scroll position — scrolling down plays the video forward, scrolling up reverses it.
This reads as far more intentional than autoplay loop video.

```js
// Bind a video's currentTime to scroll progress through its containing section
function bindScrollVideo(video, section) {
  let ready = false;
  video.addEventListener('loadedmetadata', () => { ready = true; }, { once: true });

  let ticking = false;
  function sync() {
    if (!ready || ticking) return;
    ticking = true;
    requestAnimationFrame(() => {
      const rect = section.getBoundingClientRect();
      const total = rect.height + window.innerHeight;
      const passed = window.innerHeight - rect.top;
      const progress = Math.min(1, Math.max(0, passed / total));
      const target = progress * video.duration;
      // Avoid thrashing currentTime on sub-frame deltas
      if (Math.abs(video.currentTime - target) > 0.03) {
        video.currentTime = target;
      }
      ticking = false;
    });
  }

  window.addEventListener('scroll', sync, { passive: true });
  sync();
}
```

For smoother results on Safari/iOS (where `currentTime` scrubbing stutters), pre-decode
frames to an offscreen canvas using `createImageBitmap` at section-load time, then index
into the frame array by scroll progress instead of seeking the video element directly.
This trades a one-time decode cost for buttery scroll-scrubbing afterward. Cap frame
count around 60–90 for a 3–5 second clip; more than that rarely improves perceived
smoothness and bloats memory.

**When to use:** hero section on launch pages, product reveal moments. **Never** on
content-heavy pages — the decode cost isn't worth it below the fold.

### Frosted-edge glass (refined glassmorphism)

A more deliberate take on glass surfaces than flat `backdrop-filter: blur()` — adds a
faint gradient rim so the edge of the glass catches light, which is what separates
"considered glass" from "default glassmorphism slop."

```css
.glass-edge {
  background: rgba(255, 255, 255, 0.025);
  backdrop-filter: blur(6px) saturate(1.1);
  -webkit-backdrop-filter: blur(6px) saturate(1.1);
  position: relative;
  isolation: isolate;
}
.glass-edge::after {
  content: '';
  position: absolute;
  inset: 0;
  border-radius: inherit;
  padding: 1px;
  background: linear-gradient(
    165deg,
    rgba(255, 255, 255, 0.35) 0%,
    rgba(255, 255, 255, 0.08) 25%,
    rgba(255, 255, 255, 0) 45%,
    rgba(255, 255, 255, 0) 65%,
    rgba(255, 255, 255, 0.08) 85%,
    rgba(255, 255, 255, 0.35) 100%
  );
  -webkit-mask:
    linear-gradient(#000 0 0) content-box,
    linear-gradient(#000 0 0);
  -webkit-mask-composite: xor;
  mask-composite: exclude;
  pointer-events: none;
}
/* Heavier variant for primary CTAs / modals */
.glass-edge--strong {
  backdrop-filter: blur(28px) saturate(1.15);
  -webkit-backdrop-filter: blur(28px) saturate(1.15);
  box-shadow: 0 8px 24px rgba(0, 0, 0, 0.18), inset 0 1px 1px rgba(255, 255, 255, 0.12);
}
```

The mask-composite trick paints the gradient rim *only* on the 1px border, not the
whole surface — this is what makes it read as a refined edge-light rather than a flat
tinted overlay. Use `.glass-edge` for nav bars, chips, and secondary cards. Reserve
`.glass-edge--strong` for one or two hero-level surfaces — overusing the strong variant
flattens the hierarchy it's meant to create.

**Critical implementation note:** if pairing with entrance animations, the animation's
`fill-mode` must be `backwards`, never `both` or `forwards`. A lingering `transform`
left on the element after a `forwards`-filled animation silently breaks `backdrop-filter`
on that element in most browsers — the glass blur stops compositing correctly. `backwards`
applies the starting state before the animation runs but releases all properties cleanly
once it completes.

### Pinned narrative sections (each section locks, then releases into the next)

For long-form story-driven pages — manifestos, "about us" narratives, process walkthroughs.
Each full-viewport section pins in place while the *next* section rises and rotates into
view from below, like pages turning upward.

```js
// Vanilla implementation — no animation library required.
// Each section after the first starts rotated forward (face-down) and
// straightens as it crosses into the viewport; the section before it
// stays pinned via position: sticky rather than a JS pin/scrub library.
function initStackedReveal(root) {
  const panels = Array.from(root.querySelectorAll('[data-stack-panel]'));

  panels.forEach((panel, i) => {
    panel.style.position = 'sticky';
    panel.style.top = '0';
    panel.style.zIndex = String(i + 1);

    if (i > 0) {
      panel.style.transformOrigin = 'bottom center';
      panel.style.transform = 'rotateX(8deg) scale(0.97)';
      panel.style.opacity = '0';
      panel.style.transition =
        'transform 700ms cubic-bezier(0.16,1,0.3,1), opacity 600ms ease-out';
    }
  });

  const io = new IntersectionObserver((entries) => {
    entries.forEach((entry) => {
      if (entry.isIntersecting && entry.intersectionRatio > 0.4) {
        entry.target.style.transform = 'rotateX(0deg) scale(1)';
        entry.target.style.opacity = '1';
      }
    });
  }, { threshold: [0.4] });

  panels.forEach((p, i) => { if (i > 0) io.observe(p); });
}
```

```css
[data-stack-panel] {
  min-height: 100svh;
  perspective: 1600px;
}
```

Genuinely effective for manifesto-style pages but expensive to build well and easy to
get janky on mid-range mobile — test scroll performance on an actual mid-tier Android
device before shipping, not just desktop Chrome.

### Radial gallery (items arc into a curved formation, then drift on scroll)

A circular/arced image arrangement that *forms* from a scattered or linear starting
state, then drifts slowly as the user continues scrolling — used for team photos, press
logos, or product variant galleries on launch pages.

```js
// Items start as a loose scatter, settle into a circle, then bow outward
// into a shallow arc as scroll continues. All positions computed per-frame
// from scroll progress — no animation library, no virtual scroll hijacking.
function initRadialGallery(container, items) {
  let formProgress = 0; // 0 = scattered, 1 = circle formed
  let driftProgress = 0; // 0 = circle, 1 = bowed arc

  function layout() {
    const w = container.clientWidth;
    const h = container.clientHeight;
    const radius = Math.min(w, h) * 0.32;
    const arcRadius = Math.max(w, h) * 1.1;
    const n = items.length;

    items.forEach((el, i) => {
      const angle = (i / n) * Math.PI * 2;
      const circleX = Math.cos(angle) * radius;
      const circleY = Math.sin(angle) * radius;

      const spread = 120; // degrees of arc spread when bowed
      const start = -90 - spread / 2;
      const step = spread / (n - 1);
      const arcAngle = ((start + i * step) * Math.PI) / 180;
      const arcX = Math.cos(arcAngle) * arcRadius;
      const arcY = Math.sin(arcAngle) * arcRadius + arcRadius * 0.4;

      const scatterX = el.dataset.scatterX || (el.dataset.scatterX = (Math.random() - 0.5) * w);
      const scatterY = el.dataset.scatterY || (el.dataset.scatterY = (Math.random() - 0.5) * h);

      const x1 = lerp(parseFloat(scatterX), circleX, formProgress);
      const y1 = lerp(parseFloat(scatterY), circleY, formProgress);
      const x2 = lerp(x1, arcX, driftProgress);
      const y2 = lerp(y1, arcY, driftProgress);

      el.style.transform = `translate(${x2}px, ${y2}px)`;
    });
  }

  function lerp(a, b, t) { return a + (b - a) * t; }

  let raf;
  function onScroll() {
    if (raf) return;
    raf = requestAnimationFrame(() => {
      const rect = container.getBoundingClientRect();
      const vh = window.innerHeight;
      formProgress = Math.min(1, Math.max(0, 1 - (rect.top / vh)));
      driftProgress = Math.min(1, Math.max(0, (vh - rect.top - vh * 0.6) / (vh * 1.5)));
      layout();
      raf = null;
    });
  }

  window.addEventListener('scroll', onScroll, { passive: true });
  window.addEventListener('resize', layout);
  setTimeout(() => { layout(); onScroll(); }, 50);
}
```

**When to use:** press/partner logo walls, team pages, "as featured in" sections that
want to feel alive rather than a static row. Items should be small (60–100px) — this
pattern reads as cluttered at large sizes. Cap at 12–20 items; beyond that the formation
takes too long to read and the motion becomes noise rather than delight.

### Row-scaling portrait grid (each row scales in and out as it crosses center-screen)

For speaker walls, team grids, or testimonial photo arrays. Unlike a simple fade-in
grid, each portrait scales from 0 → 1 → 0 as it travels through the viewport — so
portraits above and below the current scroll position are always slightly receded,
keeping visual focus on whatever's centered.

```js
function initScalingGrid(grid) {
  const cells = Array.from(grid.querySelectorAll('[data-scale-cell]'));

  cells.forEach((cell) => {
    let raf;
    function update() {
      raf = null;
      const rect = cell.getBoundingClientRect();
      const vh = window.innerHeight;
      const center = rect.top + rect.height / 2;
      // 0 at viewport edges, 1 at viewport center
      const distFromCenter = Math.abs(center - vh / 2);
      const proximity = Math.max(0, 1 - distFromCenter / (vh / 2));
      const scale = 0.55 + proximity * 0.45; // ranges 0.55 → 1.0
      cell.style.transform = `scale(${scale})`;
      cell.style.opacity = String(0.4 + proximity * 0.6);
    }
    function onScroll() {
      if (!raf) raf = requestAnimationFrame(update);
    }
    window.addEventListener('scroll', onScroll, { passive: true });
    update();
  });
}
```

```css
[data-scale-cell] {
  will-change: transform, opacity;
  transition: transform 80ms linear; /* light smoothing only, not the main driver */
}
```

Grayscale + slight contrast boost on the images themselves (`filter: grayscale(1)
contrast(1.1)`) reads as more editorial than full color, and gives the brand's accent
color somewhere to stand out against when used elsewhere on the page.

---



Texture is the difference between a site that looks designed and one that feels designed.
It adds physicality — the sense that the brand exists in the real world.

**When to suggest textures:**

| Brand type | Texture direction |
|------------|------------------|
| Footwear / apparel | Fabric grain, canvas weave, rubber micro-texture |
| Luxury / leather goods | Leather grain, brushed metal, linen |
| Organic / wellness | Paper grain, raw cotton, uncoated stock |
| Agency / creative | Film grain, risograph noise, concrete |
| Dark-mode SaaS | Subtle noise overlay to prevent flat digital look |
| Real estate / luxury | Stone, marble vein (as background, not decoration) |

**Textures that are always wrong:** Chevron, polka dots, diagonal stripe — these are
patterns, not textures. Avoid unless it's a deliberate retro/brand choice.

---

### SVG Noise (universal, no image dependency)

```css
/* Inline SVG noise filter — renders noise on any background color */
.noise-layer {
  position: relative;
}
.noise-layer::after {
  content: '';
  position: absolute;
  inset: 0;
  background-image: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='300' height='300'%3E%3Cfilter id='noise'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.85' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='300' height='300' filter='url(%23noise)' opacity='0.04'/%3E%3C/svg%3E");
  pointer-events: none;
  border-radius: inherit;
  z-index: 0;
}
/* Scale: 0.03–0.05 opacity for light surfaces. 0.06–0.1 for dark. */
```

### Grain animation (cinematic Tier 5)

```css
/* Animated grain — film-like, used on full dark hero sections */
.grain-hero::after {
  content: '';
  position: fixed; /* fixed so it doesn't scroll with content */
  inset: -50%;
  width: 200%; height: 200%;
  background-image: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='400' height='400'%3E%3Cfilter id='g'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.75' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='400' height='400' filter='url(%23g)' opacity='0.055'/%3E%3C/svg%3E");
  pointer-events: none;
  opacity: 0.5;
  animation: grainShift 0.4s steps(2) infinite;
  z-index: 0;
}
@keyframes grainShift {
  0%   { transform: translate(0, 0); }
  25%  { transform: translate(-2%, -1%); }
  50%  { transform: translate(1%, 2%); }
  75%  { transform: translate(-1%, 1%); }
  100% { transform: translate(2%, -2%); }
}
```

### CSS fabric/canvas texture (no image file needed)

```css
/* Woven canvas — good for footwear, bags, apparel */
.canvas-texture {
  background-color: oklch(94% 0.012 60);
  background-image:
    repeating-linear-gradient(
      0deg,
      transparent,
      transparent 2px,
      oklch(90% 0.015 60 / 0.4) 2px,
      oklch(90% 0.015 60 / 0.4) 3px
    ),
    repeating-linear-gradient(
      90deg,
      transparent,
      transparent 2px,
      oklch(90% 0.015 60 / 0.3) 2px,
      oklch(90% 0.015 60 / 0.3) 3px
    );
}

/* Subtle linen — luxury, editorial */
.linen-texture {
  background-color: oklch(96% 0.008 80);
  background-image:
    repeating-linear-gradient(
      45deg,
      oklch(93% 0.01 80 / 0.5) 0px,
      transparent 1px,
      transparent 4px
    ),
    repeating-linear-gradient(
      -45deg,
      oklch(93% 0.01 80 / 0.4) 0px,
      transparent 1px,
      transparent 4px
    );
}

/* Concrete — agency, dark editorial */
.concrete-texture {
  background-color: oklch(18% 0.005 250);
  background-image: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='200' height='200'%3E%3Cfilter id='c'%3E%3CfeTurbulence type='turbulence' baseFrequency='0.65' numOctaves='3' stitchTiles='stitch'/%3E%3CfeColorMatrix type='saturate' values='0'/%3E%3C/filter%3E%3Crect width='200' height='200' filter='url(%23c)' opacity='0.08'/%3E%3C/svg%3E");
}
```

### Texture + color: the right combination

Texture on a white background = paper.
Texture on a warm tan = canvas or leather.
Texture on a dark surface = concrete, felt, or rubber.
Texture on a gradient = wrong — the noise fights the gradient.

**Opacity calibration:**
- Light backgrounds: 0.03–0.06 opacity on the noise layer
- Dark backgrounds: 0.06–0.12 opacity
- Never exceed 0.15 — at that point texture becomes pattern

### When to suggest textures in Godmode / Agent 2

Always suggest when:
- The brand is physical-goods (footwear, apparel, furniture, food, leather goods)
- The site uses a plain white or near-white background with no other surface interest
- The design direction includes words like "raw", "craft", "handmade", "luxury", "premium"
- The site is for a brand that exists in the physical world and the current design feels digital-sterile

Suggest sparingly when:
- The brand is pure SaaS with no physical product (subtle noise on dark hero only)
- The design is intentionally minimal / clinical (healthcare, legal)

Never suggest:
- Texture on top of photography (the noise fights the image)
- Heavy texture on body text sections (reduces readability)
- Texture on interactive elements (buttons, inputs)

---

## Performance Rules

- Only animate `transform` and `opacity` — compositor thread only
- `will-change: transform` only on elements actively animating — it costs GPU memory
- Remove `will-change` after animation completes if dynamically applied
- Never animate on raw `scroll` event — always throttle via `requestAnimationFrame`
- Long-running CSS animations (marquees, blobs) must be `pointer-events: none` and isolated
- Test on mobile — what runs at 60fps on desktop may drop to 20fps on a mid-range phone
- Infinite animations should be isolated from the main content tree where possible

---

## The Taste Test

Before shipping animation at Tier 4–5, run this:

1. Watch the page load 5 times in a row. Does it still feel good on the 5th view?
   If it's annoying by view 3, cut it.

2. Show it to someone who doesn't know what the site does. Do they comment on the animation
   before the content? If yes, the animation is too loud.

3. Turn off CSS animations (`animation: none !important` in DevTools). Does the site
   still make sense and communicate the same message? If not, content is hiding behind motion.

4. Check mobile. Halve your animation durations mentally. Does it still feel intentional?

If all 4 pass — ship it.
