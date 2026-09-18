# Komorebi — Where Stillness Finds You

A single-page landing page for **Komorebi**, a fictional dawn wellness retreat brand, built entirely with vanilla HTML, CSS, and JavaScript. The design follows the **Japandi** aesthetic — a convergence of Scandinavian functional warmth and Japanese wabi-sabi elegance.

> **木漏れ日** (*komorebi*) — sunlight filtering through leaves.

---

## What This Site Is

Komorebi is a concept brand for immersive dawn retreats that blend Japanese contemplative practices (tea ceremony, forest bathing, ceramics) with Scandinavian hygge living. The landing page serves as the brand's digital front door — a meditative scroll experience designed to make visitors *slow down* before they read a single word.

The entire site lives in a single `index.html` file with no build tools, no frameworks, and no external dependencies beyond Google Fonts and Unsplash photography.

---

## Design Philosophy

| Principle | How It's Applied |
|---|---|
| **Negative space** | Generous padding (`10rem` section spacing), `max-width: 38em` paragraphs, and restrained content density |
| **Warm neutrals** | Base palette of creams (`#F6F1EB`), warm sands (`#EDE7DF`), and soft charcoal (`#2C2A25`) — never pure black or white |
| **Muted accent pops** | Persimmon (`#C4704B`), moss green (`#7B8B6F`), and sun-warmed clay (`#C9A882`) used sparingly for emotional vitality |
| **Humanist typography** | Cormorant (serif) for headings, DM Sans (sans-serif) at weight 300 for body — quiet confidence, not corporate volume |
| **Balanced asymmetry** | Overlapping image compositions, offset decorative frames, and the incomplete ensō circle |
| **Raw materiality** | Subtle SVG paper-grain texture overlay across the entire page at 3% opacity |

---

## Page Structure

The page unfolds as a single continuous scroll through seven sections:

```
┌─────────────────────────────────┐
│  Navigation (fixed, blurs on    │
│  scroll)                        │
├─────────────────────────────────┤
│  1. HERO                        │
│     Background photo (18%       │
│     opacity) + gradient overlay │
│     Title, tagline, CTA         │
│     Scroll indicator animation  │
├─────────────────────────────────┤
│  2. PHILOSOPHY                  │
│     2-column: text + layered    │
│     photo composition           │
├─────────────────────────────────┤
│  3. RITUALS                     │
│     3 cards with photos:        │
│     Tea · Forest · Craft        │
│     Ensō circle SVG             │
├─────────────────────────────────┤
│  4. CRAFTSMANSHIP               │
│     2-column: layered photos +  │
│     text with 4 value pillars   │
├─────────────────────────────────┤
│  5. SEASONAL MOMENTS            │
│     Dark background, horizontal │
│     scroll gallery (4 cards)    │
├─────────────────────────────────┤
│  6. TESTIMONIAL                 │
│     Centered quote + ensō       │
├─────────────────────────────────┤
│  7. CONNECT                     │
│     2-column: form + photo      │
│     Gentle CTA                  │
├─────────────────────────────────┤
│  Footer (dark)                  │
└─────────────────────────────────┘
```

---

## Animations & Interactions

All animations mimic organic physical phenomena — nothing snappy or mechanical.

| Animation | Technique | Trigger |
|---|---|---|
| **Scroll reveal** | `IntersectionObserver` adds `.visible` class → CSS `opacity` + `translateY` transition (1.2s) with staggered delays | Element enters viewport |
| **Ensō circle draw** | SVG `stroke-dashoffset` transition from 220 → 18 (intentionally incomplete, true to wabi-sabi) | Scrolled into view |
| **Falling leaves** | Canvas 2D particle system — 8 leaf shapes with bezier curves, individual sway/rotation/drift physics | Always running (fixed canvas) |
| **Breathing glows** | Radial gradient `opacity` + `scale` keyframes (12–15s cycle) | Always running |
| **Nav blur** | `backdrop-filter: blur(20px)` + background opacity transition on scroll past 80px | Scroll position |
| **Image hover zoom** | `transform: scale(1.03–1.05)` with 6–8s ease transition for slow, organic feel | Mouse hover |
| **Card accent bar** | Top border `scaleX(0→1)` on hover, colored per card (persimmon / moss / clay) | Mouse hover |
| **Custom cursor** | Persimmon dot with `requestAnimationFrame` lerp (0.12 factor) + expansion on interactive elements | Mouse movement (desktop only) |
| **Scroll indicator** | Thin line with a `scrollDrop` keyframe cycling a highlight, fades out on scroll | Page load → scroll |
| **Form submit** | Button text → "Sent with care ✓", background → moss green, resets after 3s | Form submission |

---

## Photography

All images are served from the **Unsplash CDN** — royalty-free, no attribution required.

| Section | Subject | Unsplash Photo ID |
|---|---|---|
| Hero (background) | Morning light through wooden blinds | `photo-1617104678098-de229db51175` |
| Philosophy (main) | Minimal interior with warm light on oak floor | `photo-1522771739844-6a9f6d5f14af` |
| Philosophy (accent) | Dried botanicals in ceramic vase | `photo-1545239705-1564e58b9e4a` |
| Ritual: Tea | Matcha in handmade bowl with bamboo whisk | `photo-1563822249366-3efb23b8e0c9` |
| Ritual: Forest | Sunlight through green forest canopy | `photo-1448375240586-882707db888b` |
| Ritual: Craft | Hands shaping clay on pottery wheel | `photo-1565193566173-7a0ee3dbe261` |
| Craft (main) | Stoneware bowls on timber shelf | `photo-1610701596007-11502861dcfa` |
| Craft (detail) | Nordic wood furniture detail | `photo-1533090161767-e6ffed986c88` |
| Autumn moment | Golden forest path with fallen leaves | `photo-1507041957456-9c397ce39c97` |
| Spring moment | Cherry blossoms in soft morning light | `photo-1462688681110-15bc88b1497c` |
| Summer moment | Golden hour meadow grasses | `photo-1500382017468-9049fed747ef` |
| Winter moment | Snow-covered birch trees in mist | `photo-1491002052546-bf38f186af56` |
| Connect | Ceramic cup on linen with window light | `photo-1604079628040-94301bb21b91` |

---

## How to Run

The site must be served over HTTP (not opened directly as a `file://` URL) because browsers block cross-origin resources like Google Fonts and canvas operations under the `file://` protocol.

### Quick start with Python

```bash
cd /path/to/komorebi
python3 -m http.server 8090
```

Then open **http://localhost:8090** in your browser.

### Other options

Any static file server works:

```bash
# Node.js (npx, no install needed)
npx serve .

# PHP
php -S localhost:8090

# Ruby
ruby -run -ehttpd . -p8090
```

---

## Tech Stack

| Layer | Choice |
|---|---|
| Markup | Semantic HTML5 |
| Styling | Vanilla CSS (custom properties, grid, flexbox) |
| Scripting | Vanilla ES6 JavaScript (no libraries) |
| Fonts | [Cormorant](https://fonts.google.com/specimen/Cormorant) + [DM Sans](https://fonts.google.com/specimen/DM+Sans) via Google Fonts |
| Images | [Unsplash](https://unsplash.com) CDN |
| Build tools | None |
| Dependencies | None |

---

## Browser Support

Tested on modern evergreen browsers. Key features used:

- CSS `clamp()`, custom properties, `backdrop-filter`
- `IntersectionObserver` API
- Canvas 2D
- `scroll-snap-type`
- ES6 classes

---

## File Structure

```
komorebi/
├── index.html    ← Everything lives here (HTML + CSS + JS)
└── README.md     ← This file
```

---

## License

This is a concept/demo project. The code is free to use and modify. Photography is sourced from Unsplash under their [license](https://unsplash.com/license) (free for commercial and non-commercial use).
