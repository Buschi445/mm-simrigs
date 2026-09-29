# MEMORY.md

## Business Overview
- **Name:** MM Simrigs
- **Industry:** Premium Motorsport Simulators & Luxury E-Commerce
- **Location:** South Tyrol, Italy
- **What they do:** Design, engineer, and manufacture elite, turnkey sim racing cockpits

## Brand Aesthetic
- **Theme:** Dark mode, sleek, high-tech, industrial luxury, aggressive
- **Palette:** Deep blacks, carbon fiber textures, metallic greys, accent `#50a9b9` (teal/cyan), anodized aluminum accents
- **Typography:** Modern, bold, highly legible — reflecting precision engineering
- **Vibe:** Precision engineering, motorsport performance; editorial layout with "liquid-glass" treatment
- **Reference inspiration:** mm-race.de (motorsport editorial direction) + superlogica.com (editorial layout language, not pixel-copy)
- **Liquid-glass elements:** Semi-transparent surfaces inspired by Apple's glass treatment
- **Site-wide dynamic background:** Blurred gradient background made uniform across whole site; per-section variants (color/position shifts) for orientation + identity
- **Subtle 3D parallax:** Background reacts to mouse movement; intentionally very subtle; must work on EVERY page — hosted in `Base.astro`

## Tech Stack
- Astro framework
- Pexels for stock photos
- Image generation integrated (hero imagery)
- Stripe integration available via Kleap one-click connect (no keys, no commission)

## Known Files
- `src/pages/index.astro` — main landing page (lineup/hero); text boxes centered within bounds, adequate top spacing
- `src/pages/customize.astro` — rig configurator (`?rig=<name>` + `#<name>` fallback); gallery has arrow nav + auto-rotate
- `src/pages/cart.astro` — cart preview page
- `src/pages/checkout.astro` — checkout page
- `src/pages/request.astro` — bespoke rig request page (name, phone, email, rig requirements)
- `src/styles/global.css` — global styles + liquid-glass utilities + site-wide dynamic gradient + mouse-reactive parallax
- `src/layouts/Base.astro` — base layout (hosts site-wide background + parallax layer for ALL routes)
- `src/components/SiteHeader.astro` — site header component

## Customizer / Configurator
- Each rig card on index links to `/customize?rig=<RigName>` (Clubsport, Sprint, GT, etc.)
- Layout: scrollable product images on left, options/addons panel on right
- Gallery images auto-rotate and are manually navigable with left/right arrows
- Rig-specific options: Sprint Cup & GT offer Motion ready toggle (yes/no checkbox)
- Universal options: checkbox menu of preinstallable games; open request field for notes; Add to Cart flows to cart/checkout

## Lineup Section (index.astro)
- Rendered as darker, readable product panels
- Each tier has a background image slot with `#50a9b9` teal tint on hover
- Visible "Customize & reserve" button per tier; CTA passes rig name to configurator
- "Start from scratch" section → routes to bespoke request page
- Edge grid uses `gap: 18px` between cards so boxes are not touching

## Bespoke Request Flow
- "Start from scratch" CTA on homepage links to `/request`
- Request page collects: Name, Phone number, Email, free-text rig requirements

## Known Issues / Fixes
- Bug: clicking "Configure" on GT card always loaded Clubsport — fixed via rig param
- Bug: "Customize & reserve" text wasn't a real button and didn't select the correct rig — fixed
- Lineup section background too bright (full white) — darkened to readable product panels
- Direct purchase section on homepage removed per user preference
- Bug: mouse-responsive parallax only worked on configurator — fixed by hosting layer in `Base.astro`
- Bug: homepage misaligned text boxes + hero too close to top — fixed
- Bug: lineup cards were touching — fixed by adding `gap: 18px` to `.edge-grid` in index.astro
- Bug: parallax depth effect broke again (likely initial page-level handler conflict) — fixed by initializing parallax directly in Base.astro script

## Recent Changes
- Replaced all design reds with `#50a9b9` accent
- Wired product CTAs on `index.astro` to `/customize?rig=` configurator (hash fallback)
- Added `src/pages/customize.astro` (gallery + options panel)
- Added `src/pages/cart.astro` and `src/pages/checkout.astro` for Add to Cart flow
- Adjusted lineup section to darker product panels with teal hover tint
- Added `src/pages/request.astro` (bespoke rig request form)
- Refreshed homepage visual language toward mm-race.de-inspired motorsport editorial with liquid-glass accents
- Site-wide polish: uniform dynamic blurred-gradient background with per-section variants; subtle mouse-reactive 3D parallax in `Base.astro`
- Homepage polish: centered text in boxes, improved top spacing, `gap: 18px` between lineup cards
- Files updated this session: `src/pages/index.astro`, `src/layouts/Base.astro`