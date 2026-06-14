# Zlicc Corporate Website

Comprehensive static multi-page website for Zlicc based on the master context and sitemap. This is no longer a one-page prototype: the generated site contains 63 pages across the full corporate architecture.

## Open

Open `index.html` directly, or run a local server from this folder:

```bash
python3 -m http.server 4173 --bind 127.0.0.1
```

Then visit `http://127.0.0.1:4173/index.html`.

## Generated Sitemap

See `SITEMAP_GENERATED.md` for the complete page list.

Major sections:

- Home
- Solutions: overview plus ZliccSync, ZliccPulse, ZliccAI, ZliccXR, ZliccLive, ZliccStudio
- Use Cases: overview plus 12 use-case pages
- Industries: overview plus 10 industry pages
- Work: overview plus case studies, gallery, results, product demos
- Insights: overview plus 9 editorial/authority pages
- Capabilities: managed deployment, experience intelligence, integrations, governance
- Company: about, story, leadership, culture, careers, partners
- Contact
- Legal / Utility: privacy, terms, accessibility

## Reset Visual Direction

This version is a full design-language reset. It moves away from the earlier dark SaaS layout pattern and reframes Zlicc as the operating layer behind unforgettable brand, event, exhibition and enterprise experiences.

The site now uses:

- Floating command-bar header with `Brief Zlicc` as the primary CTA
- Cinematic hero with an editorial side narrative instead of a standard left/center SaaS hero
- Positioning strip, connected six-pillar diagram, attendee journey map and interactive pillar selector
- Masonry-style capability modules, proof wall, industry worlds and cinematic final CTA
- Inner pages with editorial/media-led layouts instead of repeated card grids
- Official Zlicc logo assets only, never generated or distorted logos

The colour system follows the Zlicc blue-yellow-dark rule:

- 80% dark premium base: `#050814`, `#08111F`, `#111827`
- 15% blue intelligence: `#00AEEF`, `#0077FF`, `#38BDF8`
- 5% yellow energy: `#FFD500`, `#FFB800`

The interaction system includes a short Zlicc preloader, branded wipe route transition, command-panel menu transition, split-text reveal, journey path animation, interactive pillar switching, scroll-triggered reveals, count-up proof stats, cinematic image reveal treatment and glossy magnetic CTAs.

The homepage uses the premium generated event imagery in `assets/generated-2026/`, with supporting site imagery in `assets/site-images/`. The site reuses the previously generated imagery for photographic/hero sections, and adds two fresh process visuals:

- `process-stack-map.svg` for the six-pillar ecosystem map
- `process-experience-loop.svg` for the Zlicc experience loop

## Build

The site is generated from `scripts/build-site.mjs`.

```bash
node scripts/build-site.mjs
```

Generated files are also mirrored into `build/` for handoff.
