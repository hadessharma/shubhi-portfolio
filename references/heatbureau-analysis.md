# Heat Bureau → Your Portfolio: Visual Design Analysis

Reference: https://www.heatbureau.com/
Date: July 26, 2026

---

## Key Design DNA of Heat Bureau

| Element | Heat Bureau | Your Portfolio |
|---------|-------------|----------------|
| **Theme** | Full dark mode (`#111/#121212`) | Light mode (`#f5f5f1`) |
| **Color accent** | Neon orange for active nav states | Blue `#3654ff` (used sparingly) |
| **Typography** | Sans-serif (Neue Montreal) + Monospace (DM Mono) in brackets | Serif (Fraunces) + Sans (Inter) + Mono (IBM Plex) |
| **Imagery** | Cinematic, full-bleed, high-grain monochrome textures | Stock photos in contained frames |
| **Project layout** | Mixed hierarchy: 1 full-width hero + 2-col grid | Uniform 2-column alternating cards |
| **Hover states** | Image → grainy monochrome + circular arrow cursor | Image scale + floating tag |
| **Labels** | Monospace in brackets: `[ CREATIVE DIRECTOR ]` | Mono with line prefix: `— Senior Product Designer` |
| **Footer** | Rich 4-column with `[heat]` `[social]` `[reach]` `[location]` groups | Minimal 2-element footer |

---

## 9 Suggestions for Your Portfolio

### 1. 🌑 Add a Dark Section for Visual Rhythm

Heat Bureau's entire site is dark, but you don't need to go full dark. **Add one dark "chapter" to break the monotony** of your all-cream page.

**Where:** The CTA/Contact section (`style.css` lines 898-958)

```css
.cta-section {
  background: var(--ink);
  color: var(--paper);
}
.cta-section .eyebrow { color: rgba(245,245,241,.5); }
.cta-section .eyebrow::before { background: rgba(245,245,241,.3); }
.cta-section h2 em { color: #8b9dff; }
.cta-section .btn { border-color: var(--paper); color: var(--paper); }
.cta-section .btn.filled { background: var(--paper); color: var(--ink); }
.cta-section .btn.filled:hover { background: var(--signal); border-color: var(--signal); }
.contact-grid { border-top-color: rgba(245,245,241,.15); }
.contact-grid a { color: var(--paper); }
```

> This creates a visual "chapter break" exactly like Heat Bureau does between its dark sections and the slightly different-toned footer.

---

### 2. 🖼️ Grainy Monochrome Hover Effect on Project Cards

This is Heat Bureau's signature interaction — hovering over a project card transforms the image from color to a high-grain monochrome with a circular arrow icon appearing in the center.

**Where:** `style.css` lines 729-857 — project card hover styles

```css
.project-media::after {
  content: '↗';
  position: absolute;
  inset: 0;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 24px;
  color: var(--paper);
  width: 56px; height: 56px;
  margin: auto;
  border: 1.5px solid var(--paper);
  border-radius: 50%;
  opacity: 0;
  transform: scale(0.7);
  transition: opacity .4s var(--ease), transform .4s var(--ease);
  z-index: 2;
}
.project-card:hover .project-media img {
  filter: grayscale(1) contrast(1.2);
}
.project-card:hover .project-media::after {
  opacity: 1;
  transform: scale(1);
}
```

---

### 3. 🎬 Featured Project Hero (Mixed Grid Layout)

Heat Bureau uses a **mixed hierarchy** for projects: one full-width "hero" project at the top, then a 2-column grid below. This instantly signals which project is most important.

**Where:** `index.html` lines 167-299 — `#work` section

> Make your first project card (Curate) span full width as a cinematic banner. Add a CSS class like `.project-card.featured` with `grid-template-columns: 1fr` and a much larger image aspect ratio (21:9).

---

### 4. 📋 Structured Footer with Column Groups

Heat Bureau's footer is beautifully organized with monospace bracket labels (`[heat]`, `[social]`, `[reach]`, `[location]`), each heading a column of links.

**Where:** `index.html` lines 353-356 — current minimal footer

Your current footer is just two lines of text. Upgrade to a multi-column footer:

```html
<footer>
  <div class="wrap">
    <div class="footer-grid">
      <div class="footer-col">
        <div class="footer-label">[pages]</div>
        <a href="#about">About</a>
        <a href="#work">Work</a>
        <a href="#process">Process</a>
      </div>
      <div class="footer-col">
        <div class="footer-label">[social]</div>
        <a href="#">LinkedIn</a>
        <a href="#">Dribbble</a>
        <a href="#">Twitter / X</a>
      </div>
      <div class="footer-col">
        <div class="footer-label">[reach]</div>
        <a href="mailto:hello@shubhangishah.design">Email</a>
        <a href="#">Resume</a>
      </div>
      <div class="footer-col">
        <div class="footer-label">[location]</div>
        <span>Ahmedabad, India</span>
        <span>GMT+5:30</span>
      </div>
    </div>
    <div class="footer-bottom">
      <div>© 2026 Shubhangi Singh</div>
      <div>Designed with intention</div>
    </div>
  </div>
</footer>
```

> The `[bracket]` monospace labels are a signature Heat Bureau pattern that would complement your existing Figma-inspired design language perfectly.

---

### 5. 🪗 Accordion-Style Process Section

Heat Bureau's Services page uses a clean numbered accordion (`01. Concept & Strategy`, `02. Design`, `03. Development`) with `+` expand icons. This is more interactive than your static 4-column grid.

**Where:** `index.html` lines 301-334 — `#process` section

> Convert your Process section from a static 4-column grid to an expandable accordion. Each step starts collapsed showing just the title, and clicking reveals the description. This encourages interaction and reduces visual clutter.

---

### 6. 🏷️ Bracket-Style Monospace Labels

Heat Bureau consistently uses `[ CREATIVE DIRECTOR ]` style bracketed labels in monospace. This is a small typographic choice that adds serious character.

**Where:** Throughout your portfolio — eyebrow labels, skill chips, role tags

Adapt your existing eyebrow format from `01 — About` to `[ 01 — About ]` or use brackets for role labels in case studies.

---

### 7. 📸 Large Cinematic Portrait in About Section

Heat Bureau's Studio page features a massive, high-grain monochrome founder portrait — the image takes up nearly half the viewport and has a raw, editorial quality.

**Where:** `index.html` lines 90-94 — `.about-portrait`

> Your About portrait placeholder is a gradient with decorative elements but no actual photo. Adding a high-quality, editorially styled portrait photograph would massively elevate this section. Even a black-and-white treatment with added grain (like Heat Bureau's founders) would feel premium.

---

### 8. ✨ Immersive Hero Treatment

Heat Bureau's hero is radically minimal — just a centered script logotype on a dark canvas, nothing else. It's confident and bold.

**Where:** `index.html` lines 38-74 — hero section

Your hero is information-rich (which is fine for a portfolio), but consider adding a **scroll-triggered transition** that fades the hero into the content section below, rather than a hard cut.

---

### 9. 🧭 Active Nav State with Accent Color

Heat Bureau highlights the current page's nav link in **bright orange** while others stay white. This is a strong, clear wayfinding pattern.

**Where:** `index.html` lines 24-35 + `style.css` lines 210-267

```css
nav a.active { color: var(--signal); }
nav a.active::after { width: 100%; background: var(--signal); }
```

Add JS to track which section is in view and toggle `.active` on the corresponding nav link.

---

## Priority Matrix

| Priority | Suggestion | Visual Impact | Effort |
|----------|-----------|--------------|--------|
| 🔴 **Do first** | Dark CTA section (#1) | High — instant visual rhythm | Low |
| 🔴 **Do first** | Structured footer (#4) | High — polished & professional | Low |
| 🔴 **Do first** | Active nav states (#9) | Medium — polish & usability | Low |
| 🟡 **High impact** | Grainy hover effect (#2) | Very High — signature interaction | Medium |
| 🟡 **High impact** | Featured project hero (#3) | High — visual hierarchy | Medium |
| 🟡 **High impact** | Real portrait photo (#7) | Very High — credibility | Depends on photo |
| 🟢 **Nice to have** | Accordion process (#5) | Medium — interactive engagement | Medium |
| 🟢 **Nice to have** | Bracket labels (#6) | Low — typographic character | Low |
| 🟢 **Nice to have** | Hero transition (#8) | Low — cinematic polish | Medium |

---

## Summary

The biggest takeaways from visually browsing Heat Bureau:

1. **The grainy monochrome hover effect** is their most iconic interaction — very achievable with CSS `filter: grayscale(1) contrast(1.2)` + a pseudo-element arrow
2. **The structured footer** with bracket-labeled columns would complement your Figma-inspired aesthetic perfectly
3. **One dark section** (CTA) would create the visual rhythm your all-cream page currently lacks
4. **Active nav highlighting** is a small but meaningful UX improvement
