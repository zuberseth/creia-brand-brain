# Creia Web Design System

This is the **single source of truth** for the website. Every new page or section must follow these rules exactly.

**Consolidation, July 2026.** This doc absorbs the former "Design System — Primary Reference" and both "Typography Reference" documents. Those are superseded stubs pending archive; nothing lives there that does not live here. The live site is **creia.com**.

---

## Scope

This document governs **website implementation**: the live Lovable-built creia.com — components, classnames, colour tokens, layout, motion, on-screen typography, button styles. Anything Creia ships as a web surface.

This document does **not** govern creative output. Ads, campaigns, photography, packaging, social, video, editorial copy, and voice live under the **Brand Bible — Creative**.

The two are *meant* to differ in places. The website is the calmer surface. Creative is the louder arrival.

When the two appear to conflict, scope decides. The website follows this document. Creative follows the Bible. Examples of the intentional split:

* Body text on the **website** uses Hubot Sans Light. **Creative** body type (packaging, print, campaign layouts) uses Area Extended at regular weight.
* Website palette is intentionally neutral-only (#FAFAFA → #171717). Creative colour follows **Brand Bible §14**; do not infer creative colour rules from the website palette.
* Website mood is "Apple-inspired liquid glass — translucent layers, soft blurs, restrained depth." **Creative** mood is "dark, high-contrast, direct-flash, it-girl," with a toy-ish pop register.

---

## 1. Brand Aesthetic (web)

* **Tone**: Premium, editorial wellness. Sophisticated and minimalist.
* **Mood**: Apple-inspired "liquid glass" — translucent layers, soft blurs, restrained depth.
* **Anti-patterns**: No gym-bro imagery, no neon gradients, no cluttered layouts, no generic SaaS aesthetics.

---

## 2. Colour System

All colours use **semantic tokens** defined in `index.css` and `tailwind.config.ts`.

**Never use raw hex/rgb in components.** Use `text-neutral-900`, `text-neutral-500`, `bg-neutral-50`, `bg-neutral-100`, `border-neutral-200` as the approved palette.

| Token / Class | Value | Usage |
| -- | -- | -- |
| `bg-neutral-50` | #FAFAFA | Page background, card backgrounds |
| `bg-neutral-100` | #F5F5F5 | Image panel backgrounds (e.g. product widget) |
| `text-neutral-900` | #171717 | All primary text, headings, body |
| `text-neutral-500` | #737373 | Secondary/helper text, labels, icons |
| `border-neutral-200` | #E5E5E5 | Borders, dividers, editorial grid gaps |
| `bg-neutral-200` | #E5E5E5 | Editorial grid gap fill (gap-px technique) |
| `text-foreground` | hsl(0 0% 9%) | Semantic alias for primary text |
| `text-muted-foreground` | hsl(0 0% 45%) | Semantic alias for secondary text |
| `bg-background` | hsl(0 0% 98%) | Semantic alias for page background |

### Theme Meta Tags

* Light mode Safari tab bar: **white** (`<meta name="theme-color" content="#ffffff" media="(prefers-color-scheme: light)">`)
* Dark mode Safari tab bar: **system default** (no override)

---

## 3. Typography

> This section is the complete typography reference. The former standalone "Typography Reference" doc is superseded.

### Fonts

| Token | Font Family | Usage |
| -- | -- | -- |
| `font-area` | Area Extended (Thin, Regular, Bold, ExtraBold supplied) | All headings, buttons, labels, prices, nav links |
| `font-display` | Area Extended (alias) | Same as font-area — use interchangeably |
| `font-body` | Hubot Sans (ExtraLight and Light supplied) | Body paragraphs, descriptions, newsletter input; Light is the default |

> **Instrument Serif is deprecated.** Do not use in any new components.

### Font Weights

| Weight | Supplied face | Usage |
| -- | -- | -- |
| `font-extralight` | Hubot Sans ExtraLight | Intentionally quieter supporting copy only |
| `font-light` | Hubot Sans Light | Default body and descriptive paragraphs |
| `font-thin` | Area Extended Thin | Deliberately light display treatments only |
| `font-normal` | Area Extended Regular | Fine print and regular-weight Area text |
| `font-bold` | Area Extended Bold | Headings, buttons, labels, prices, nav, feature headings |
| `font-extrabold` | Area Extended ExtraBold | Extra-emphasis display treatments only |

### Approved Font Sizes

| Class | Px | Font | Weight | Usage |
| -- | -- | -- | -- | -- |
| `text-[9px]` | 9 | area | bold | Save badges only (exception to 12px minimum) |
| `text-[10px]` | 10 | area | normal | Fine print (subscription details, strikethrough prices) |
| `text-[11px]` | 11 | area | bold | Mobile button text, widget labels (scales to text-xs on sm+) |
| `text-xs` (12px) | 12 | area | bold | Buttons, nav links, labels, per-sachet prices, shipping notes |
| `text-sm` (14px) | 14 | body | light | Ingredient descriptions, newsletter feedback, helper text |
| `text-base` (16px) | 16 | body | light | Standard body paragraphs (Benefits, TrustBar) |
| `text-lg` (18px) | 18 | area | bold | Sub-card titles (WhatsInside), TrustBar H3 (mobile), footer tagline (sm+) |
| `text-xl` (20px) | 20 | body | light | Feature body text (FeelTheDifference, VideoSection body) |
| `text-2xl` (24px) | 24 | area | bold | Card titles (ProductSection H3, BenefitCards mobile) |
| `text-3xl` (30px) | 30 | area | bold | Section titles H2 (mobile), BenefitCards H3 (sm+) |
| `text-5xl` (48px) | 48 | area | bold | Section titles H2 (sm+), Hero H1 (mobile fallback) |
| `text-6xl` (60px) | 60 | area | bold | Hero H1 (sm breakpoint) |
| `text-7xl` (72px) | 72 | area | bold | Hero H1 (lg+) |

**Rules:**

* Do NOT introduce any size outside this table.
* Minimum text size: **12px** (`text-xs`). Only save badges use 9px; fine print uses 10px.
* Mobile widget text may use `text-[11px]` scaling to `sm:text-xs`.

### Letter Spacing

| Class | Usage |
| -- | -- |
| `tracking-tight` | All headings H1–H4, card titles |
| `tracking-[0.05em]` | Per-sachet prices, shipping notes |
| `tracking-[0.1em]` | Mobile button/label text, save badges |
| `tracking-[0.15em]` | All buttons (sm+), nav links, labels |
| `tracking-[0.3em]` | Section eyebrow labels (deprecated style) |

### Line Height

| Class | Usage |
| -- | -- |
| `leading-[1.1]` | Large feature headings (VideoSection) |
| `leading-relaxed` | All body paragraphs |
| (default) | Buttons, labels, small text |

---

## 4. Heading Patterns

### Hero H1

```
font-area font-bold tracking-tight text-neutral-900
text-4xl sm:text-6xl lg:text-7xl
```

### Section H2 (standard)

```
font-area font-bold tracking-tight text-neutral-900
text-3xl sm:text-5xl
```

### Section H2 (feature / large)

```
font-display font-bold leading-[1.1] tracking-tight text-foreground
text-3xl sm:text-5xl lg:text-5xl
```

### Card H3 (BenefitCards, ProductSection)

```
font-area font-bold tracking-tight text-neutral-900
text-2xl sm:text-3xl
```

### Sub-card H4 (WhatsInside)

```
font-area font-bold tracking-tight text-neutral-900
text-lg sm:text-xl
```

---

## 5. Body Text Patterns

### Standard body paragraph

```
font-body text-base font-light leading-relaxed text-neutral-900
```

### Feature body paragraph (larger)

```
font-body text-xl font-light leading-relaxed text-neutral-900 sm:text-2xl lg:text-3xl
```

### Description / ingredient body

```
font-body text-sm font-light leading-relaxed text-neutral-900
```

### Helper / secondary text

```
font-body text-sm font-light text-neutral-500
```

---

## 6. Buttons

### Primary CTA (purchase / pre-order)

```
w-full glass-strong glass-inverted-hover py-3.5
font-area font-bold text-[11px] sm:text-xs uppercase
tracking-[0.1em] sm:tracking-[0.15em] text-neutral-900
transition-all duration-300
border-radius: 50px (via style prop)
```

### Secondary CTA (learn more, start trial, shop now)

```
inline-block glass glass-hover px-5 sm:px-8 py-3
font-area font-bold text-[11px] sm:text-xs uppercase
tracking-[0.1em] sm:tracking-[0.15em] text-neutral-900
transition-all duration-300 whitespace-nowrap
border-radius: 50px (via style prop)
```

### Hero CTA (pre-order on hero)

```
glass-strong glass-hover px-8 py-3
font-area text-xs font-bold uppercase tracking-[0.15em] text-neutral-900
transition-all
border-radius: 50px (via style prop)
```

### Icon button (carousel arrows, newsletter submit)

```
glass glass-hover p-2 text-neutral-500
transition-all duration-300
border-radius: 50px (via style prop)
```

### Pill selector (quantity toggle — active)

```
glass-inverted
font-area font-bold text-[11px] sm:text-xs uppercase
tracking-[0.1em] sm:tracking-[0.15em]
border-radius: 50px (via style prop)
padding: 16px 12px (via style prop)
```

### Pill selector (quantity toggle — inactive)

```
glass glass-hover
font-area font-bold text-[11px] sm:text-xs uppercase
tracking-[0.1em] sm:tracking-[0.15em]
border-radius: 50px (via style prop)
padding: 16px 12px (via style prop)
```

---

## 7. Glass Effects

Defined in `index.css`. Use the class names — never recreate inline.

| Class | Background | Blur | Usage |
| -- | -- | -- | -- |
| `.glass` | rgba(255,255,255,0.6) | blur(20px) | Default translucent container, buttons |
| `.glass-strong` | rgba(255,255,255,0.7) | blur(24px) | Primary CTAs, newsletter input wrapper |
| `.glass-inverted` | rgba(0,0,0,0.85) | blur(24px) | Active/selected state (dark + glass) |
| `.glass-hover` | — | — | Hover: darkens slightly on hover |
| `.glass-inverted-hover` | — | — | Hover: transitions to dark glass on hover |

---

## 8. Border Radius Hierarchy

| Radius | Implementation | Usage |
| -- | -- | -- |
| `50px` | `style={{ borderRadius: 50 }}` | Pills, buttons, nav bar, newsletter input |
| `24px` | `style={{ borderRadius: 24 }}` | Cards (purchase widget, plan selectors) |
| `16px` | `style={{ borderRadius: 16 }}` | Dropdown menus |
| `0` | (default) | Editorial grid containers, full-bleed sections |

> Always use `style={{ borderRadius: N }}` for 50px and 24px — Tailwind rounded classes are reserved for smaller radii.

---

## 9. Layout & Spacing

### Section Padding

```
px-6 py-16 md:px-10 md:py-24
```

> **No** `px-4` exceptions. Always `px-6 md:px-10` on padded sections.

### Full-bleed sections (no padding)

VideoSection, FeelTheDifference — these use edge-to-edge image grids with no section padding.

### Content Max Widths

* Text-heavy centered blocks: `max-w-3xl mx-auto`
* General content: no max-width (full-width grids)
* Purchase widget: contained by grid column

### Grid Patterns

#### Editorial card grid (BenefitCards, WhatsInside)

```
grid grid-cols-1 sm:grid-cols-2 md:grid-cols-3   (or lg:grid-cols-4)
gap-px bg-neutral-200
```

Cards inside: `bg-neutral-50` (creates 1px hairline borders between cards)

#### Two-column feature layout (VideoSection, FeelTheDifference)

```
grid grid-cols-1 lg:grid-cols-2
```

Image: `aspect-[4/3] sm:aspect-[7/4] lg:aspect-auto lg:min-h-[600px]`
Text: `px-6 py-12 sm:px-12 lg:px-16 lg:py-0`

#### Purchase widget

```
grid md:grid-cols-2 glass
style={{ borderRadius: 24 }}
```

---

## 10. Images & Aspect Ratios

| Ratio | Usage |
| -- | -- |
| `aspect-[3/4]` | Benefit card images (portrait editorial) |
| `aspect-square` | Ingredient card images (WhatsInside) |
| `aspect-[4/3]` | Feature image mobile (VideoSection) |
| `aspect-[7/4]` | Feature image tablet (sm breakpoint) |
| `lg:aspect-auto` | Feature image desktop (natural height) |

Image hover: `transition-transform duration-700 group-hover:scale-[1.03]`

---

## 11. Motion & Animation

All animations use **Framer Motion**.

### Standard fade-in (sections, cards)

```
const fade = (delay = 0) => ({
  initial: { opacity: 0, y: 16 },
  whileInView: { opacity: 1, y: 0 },
  viewport: { once: true, margin: "-60px" },
  transition: { duration: 0.7, delay },
});
```

### Hero entrance

```
initial: { opacity: 0, y: 20-30 }
animate: { opacity: 1, y: 0 }
transition: { duration: 0.8-1.0, delay: staggered 0.2-0.8 }
```

### Testimonial carousel

```
AnimatePresence mode="wait"
initial: { opacity: 0, y: 15 }
animate: { opacity: 1, y: 0 }
exit: { opacity: 0, y: -15 }
transition: { duration: 0.4 }
```

### Collapsible sections

```
initial: { height: 0, opacity: 0 }
animate: { height: "auto", opacity: 1 }
exit: { height: 0, opacity: 0 }
transition: { duration: 0.35, ease: "easeInOut" }
```

### Dropdown menus

Entry: `animate-in fade-in zoom-in-95 slide-in-from-top-2`

---

## 12. Navigation

### Header (fixed pill)

```
fixed left-4 right-4 top-4 z-50
Inner: glass flex items-center justify-between px-6 py-3
border-radius: 50px
White pill backdrop: absolute inset-0 bg-white border-radius: 50px
```

### Dropdown menu

```
min-w-[200px] border border-neutral-200
bg-white/80 backdrop-blur-[20px] backdrop-saturate-150
shadow-sm p-1
border-radius: 16px
```

Menu items:

```
font-area text-[11px] sm:text-xs font-bold uppercase
tracking-[0.1em] sm:tracking-[0.15em] text-neutral-900
px-4 py-2.5 focus:bg-neutral-100 rounded-xl
```

---

## 13. Footer

* Border top: `border-t border-neutral-200`
* Brand tagline: `font-body text-base font-light text-neutral-900 sm:text-lg`
* Newsletter input: glass pill (50px radius), `font-body font-light text-sm`
* Submit icon button: `glass-strong glass-hover` inside pill
* Instagram link: `font-area text-xs font-bold uppercase tracking-[0.15em]`
* Full-width logo at bottom: `<img className="w-full" />`

---

## 14. Component Patterns

### CollapsibleSection

* Section title + chevron toggle
* Title: `font-area text-3xl font-bold tracking-tight text-neutral-900 sm:text-5xl`
* Chevron: `h-5 w-5 text-neutral-500`, rotates 180° on open
* Content animates height with Framer Motion

### Testimonials Carousel

* Centered text, max-w-3xl
* Quote: `font-body text-xl font-light leading-relaxed text-neutral-900 sm:text-2xl lg:text-3xl`
* Navigation: glass icon buttons with chevrons
* Counter: `font-area text-xs font-bold tracking-[0.15em] text-neutral-900`

### TrustBar

* 2-column grid (`sm:grid-cols-2`)
* Icon: `h-6 w-6 text-neutral-500`
* Title: `font-area text-lg font-bold tracking-tight text-neutral-900 sm:text-xl`
* Body: `font-body text-base font-light leading-relaxed text-neutral-900`

---

## 15. Rules (Enforcement)

 1. **Never add a new font size** — pick the closest from the table above.
 2. **Always use neutral-\* classes** for colours — never raw hex/rgb in components.
 3. **All buttons** use `font-area font-bold uppercase` with appropriate tracking.
 4. **All section titles** use `font-area font-bold tracking-tight`.
 5. **No italics** — ever.
 6. **Sentence case** for all text. `uppercase` only on buttons, nav, and labels.
 7. **Minimum text size: 12px** — only save badges (9px) and fine print (10px) are exceptions.
 8. `px-6 md:px-10` everywhere — no `px-4` on padded sections.
 9. **Glass classes only** — never recreate blur/backdrop inline.
10. **Border radius via style prop** — use `style={{ borderRadius: N }}` for 50px, 24px, 16px.
11. **Editorial grids** use `gap-px bg-neutral-200` with `bg-neutral-50` cards.
12. **Image hover** is always `scale-[1.03]` with `duration-700`.
