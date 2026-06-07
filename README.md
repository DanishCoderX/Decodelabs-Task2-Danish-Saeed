# Project 2 — Responsive Web Layout
### DecodeLabs Frontend Development · Batch 2026

A mobile-first responsive page that adapts gracefully from a 320px phone to a 1440px desktop. Every layout decision is driven by progressive enhancement — base CSS written for the smallest screen, enhanced upward with `min-width` media queries.

---

## 🔗 Quick Links

| | |
|-|-|
| **Live Page** | `P2.html` |
| **Stylesheet** | `P2.css` |
| **Author** | Danish Saeed |
| **Program** | DecodeLabs Batch 2026 |

---

## 🎯 Project Goal

62.73% of web traffic is mobile. This project proves a layout can serve every device without a separate mobile site or a CSS framework — using fluid units, smart breakpoints, and the right layout tool for each job.

---

## 📐 Breakpoint System

| Breakpoint | Range | Changes |
|------------|-------|---------|
| **Mobile** (base) | 0px → 479px | Single column, stacked layout, hamburger nav, full-width tap targets |
| **Tablet SM** | 480px+ | Hero becomes 2-column row, breakpoints grid → 2 cols, feature cards → 2 cols, footer row layout |
| **Tablet LG** | 768px+ | Desktop nav appears, hamburger hidden, about → 2-column grid, cards → 3 cols, breakpoints → 4 cols |
| **Desktop** | 1024px+ | Device visual expands, larger card heights, full prose font size |

---

## 📄 Page Sections

| Section | Element | Responsive Behaviour |
|---------|---------|----------------------|
| Header | `<header>` | Hamburger on mobile → desktop nav at 768px |
| Hero | `<section>` | Stacked column → 2-column row at 480px |
| About | `<section>` | Stacked → 5fr/7fr grid at 768px |
| Skills | `<section>` | `auto-fit` grid — self-adjusting, no breakpoints needed |
| Breakpoints | `<section>` | 1 col → 2 col → 4 col progression |
| Feature Cards | `<section>` | 1 col → 2 col → 3 col progression |
| Contact | `<section>` | Centred, fluid font size throughout |
| Footer | `<footer>` | Stacked → row at 480px |

---

## 🛠️ Techniques Used

### Mobile-First Strategy
- Base CSS targets the **smallest screen** — no assumptions about viewport
- All media queries use `min-width` (never `max-width`) to layer enhancements upward
- Structure: write for 320px → enhance at 480px → enhance at 768px → enhance at 1024px

### Fluid Units
| Unit | Used For |
|------|----------|
| `%` | Container width, fluid image widths |
| `rem` | Spacing scale, consistent sizing |
| `vw` | Typography scaling mid-range |
| `clamp()` | Headings, body text, card titles — smooth continuous scale |
| `min()` | Container: `min(1200px, 100% - 2.5rem)` |

### Typography — `clamp()` Examples
```css
font-size: clamp(2.25rem, 8vw, 5rem);   /* Hero heading */
font-size: clamp(1rem, 2.5vw, 1.125rem); /* Body text */
font-size: clamp(1.5rem, 4vw, 2.5rem);  /* About headline */
```
No stepped breakpoints for font sizes — the scale is continuous.

### CSS Grid — Self-Responsive Pattern
```css
grid-template-columns: repeat(auto-fit, minmax(min(250px, 100%), 1fr));
```
The skills grid adjusts its column count automatically with **zero media queries**.

### Hamburger Navigation
- Toggle implemented in vanilla JavaScript (`display: flex / none`)
- `document.body.style.overflow = 'hidden'` locks scroll when menu is open
- Closes on: close button click, nav link click, clicking the backdrop, or window resize to desktop
- Full-screen overlay with centred links at `clamp(1.5rem, 6vw, 2rem)` font size

### Touch Targets
- CSS variable `--touch-target: 44px` applied as `min-height` on every interactive element
- Covers: nav links, hamburger button, close button, mobile nav links, footer links, all buttons
- Zoom never disabled — `user-scalable` not set, allows up to 500% zoom (WCAG 1.4.4)

### Layout Systems
- **CSS Grid** — page-level section layouts, multi-column cards
- **Flexbox** — header, hero actions, footer, button groups, fact list items
- Direction flip: `flex-direction: column` (mobile) → `row` (tablet) without duplication

---

## 🎨 Design Tokens

Identical to P1 — shared design language across all projects.

| Token | Value |
|-------|-------|
| Background | `#0f0e0e` |
| Accent (amber) | `#e8c547` |
| Text | `#f0ede8` |
| Touch Target | `44px` |
| Breakpoints | `480px · 768px · 1024px` |

---

## ✅ Quality Checklist

- [x] Mobile-first — all base styles target smallest viewport
- [x] `min-width` queries only — progressive enhancement
- [x] `clamp()` for all headings and body text — no stepped font breakpoints
- [x] `auto-fit` grid for skills — zero media queries needed
- [x] 44px minimum touch targets — all interactive elements
- [x] Zoom not disabled — WCAG 1.4.4 compliant
- [x] Hamburger menu — open, close, backdrop, resize all handled
- [x] Body scroll locked when mobile nav is open
- [x] `loading="lazy"` on below-fold images
- [x] Desktop nav hidden on mobile — no layout shift
- [x] W3C HTML Validator — zero errors
- [x] External CSS only — no inline styles
- [x] BEM methodology — consistent throughout

---

## 👤 Author

**Danish Saeed** — DecodeLabs Frontend Development Intern · Batch 2026
📧 [daanishsaeed593@gmail.com](mailto:daanishsaeed593@gmail.com)
🐙 [github.com/DanishCoderX](https://github.com/DanishCoderX)
