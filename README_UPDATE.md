# Koboku — Update Package v3 (April 2026)

## What changed since v2
- **New hero on `index.html`**: the old typographic hero is replaced by a full-bleed scroll-driven image stack with 5 Italian campaign frames. Cross-fade + subtle Ken-Burns scale on each frame, driven by scroll progress (GSAP ScrollTrigger). Right-side dot rail shows which frame you're on; caption at bottom updates live.
- **The old tagline is not lost**. "Where the Sword Meets the Screen / Frame / Brand" now lives just below the hero as a chapter heading — same type, same rotator, same copy. So the brand message still lands, just at the second beat.
- **`netherlands.html`** gets an 8th plate (the Nike diner interior shot) inserted right after the palette strip — palette shown as abstract swatches, then immediately shown "in the wild".
- New image assets in `assets/`.

## Files
| File | What |
|---|---|
| `index.html` | Homepage — full-bleed hero stack + chapter heading + rest unchanged |
| `netherlands.html` | Sundae Social editorial — now with plate 08 |
| `assets/hero-01-port.png` | Man profile at port (Puglia) |
| `assets/hero-02-dock.png` | Man on dock, shirt open |
| `assets/hero-03-collar.png` | Woman covering face with white collar |
| `assets/hero-04-villa.png` | Woman in Tuscan villa, golden hour |
| `assets/hero-05-espresso.png` | Redhead drinking espresso, Florence alley |
| `assets/sundae-01` … `sundae-07` | Sundae Social plates 01–07 |
| `assets/sundae-08-nike-interior.png` | New — Nike sweatshirt + diner interior |

## Install
1. Replace `index.html` and `netherlands.html` in the repo root.
2. Drop the `assets/` folder (with all 13 PNGs) into the repo root.
3. Commit & push. Done.

## How the hero behaves
- The hero section is 500vh tall. The image stage inside is `position: sticky; height: 100svh;` — so on scroll, the user sees the images cross-fading while the page appears to pause. Each frame occupies ~100vh of scroll distance.
- The overlay (Koboku wordmark at top, caption at bottom, dot rail on right) is `position: fixed` during the hero. When the user has fully scrolled past, the overlay fades and goes `visibility: hidden` so it doesn't overlap later content.
- Everything uses `mix-blend-difference` to stay legible regardless of which photo is behind.
- Mobile: same system, dot rail hidden, topbar slightly smaller.
- Keyboard / reduced-motion users: Lenis auto-disables; images still cross-fade but without smooth scroll interpolation.

## The 6th photo
You uploaded 6 new images. 5 are in the hero, 1 (the Nike diner shot) went into `netherlands.html` as plate 08 — it fits the Sundae Social world, not the Italian Mediterranean world.

## What you still want to address
- **SSL certificate** on `www.koboku.it` — the cert hostname-mismatch issue from before is probably still there. Fix at hosting level.
- **Tailwind CDN** — still the prototyping version. Migrate to Tailwind CLI when you have time.
- **`about.html`** is still truncated — needs either a second founder's bio or a rewrite as solo-founder.
- **Image weight**: the 5 hero PNGs total ~1 MB. For production, convert to WebP quality 82 (cuts to ~350 KB). Consider `<picture>` with `sizes` for responsive loading so mobile doesn't download the desktop-size file.
- **Preloading**: in production, add `<link rel="preload" as="image" href="assets/hero-01-port.png">` in the `<head>` so the first frame paints instantly.

Ping me for any of the above, or:
- A real NL GeoJSON map
- Finishing `about.html`
- Adding "Beyond the Rack" as a long-form post in `blog.html`
- Adjusting the hero photo order or adding/removing frames
