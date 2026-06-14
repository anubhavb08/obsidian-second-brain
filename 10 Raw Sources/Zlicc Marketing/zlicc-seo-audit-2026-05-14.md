# Zlicc Website SEO Audit — 2026-05-14
Audited build: `/Users/anubhavbajpai/Downloads/08 Project Folders/zlicc-website-work-updates-v3-working-2026-05-13`
Pages crawled: **47** HTML pages
Build size: **76.6 MB HTML only**; folder size **78.1 MB**
SEO readiness score: **50/100** (custom technical/on-page heuristic)

## Executive Verdict
**Not SEO-ready yet; technical basics need work.** No website is realistically “100% SEO optimized,” and this build still has technical SEO gaps before launch: sitemap/robots/canonicals, oversized base64 HTML, and missing/weak structured data coverage.

## Findings

### High Priority
1. **Indexability** — robots.txt is missing. Search engines can still crawl, but you cannot declare sitemap location or crawl rules.
   Affected examples: `robots.txt`
2. **Indexability** — sitemap.xml is missing. A 47-page static site should publish all canonical URLs for discovery.
   Affected examples: `sitemap.xml`
3. **Canonicals** — 47/47 pages have no canonical URL.
   Affected examples: `about.html, agm.html, ai.html, anamorphic-camera.html, ar-earns-its-place.html, auto-anamorphic-reveal.html, auto.html, axis-employee-ai.html +39 more`
4. **Performance** — 36 HTML files exceed 1 MB, mainly because images are embedded as base64. This hurts crawl/render performance and cacheability.
   Affected examples: `about.html (1.2 MB), ai.html (1.2 MB), anamorphic-camera.html (1.6 MB), ar-earns-its-place.html (1.2 MB), auto-anamorphic-reveal.html (2.2 MB), auto.html (2.9 MB), axis-employee-ai.html (1.5 MB), bfsi.html (1.7 MB) +28 more`

### Medium Priority
1. **Metadata** — 25 pages have long meta descriptions over 165 chars.
   Affected examples: `agm.html, ai.html, auto.html, axis-employee-ai.html, bfsi.html, brand-activation.html, conference.html, dealer-meet.html +17 more`
2. **Metadata** — 11 pages have missing, short or long titles outside 25–70 chars.
   Affected examples: `auto.html, brand-ai-checks.html, contact.html, cookies.html, hybrid-casting.html, index.html, live-event-stack-ai-peer.html, mice.html +3 more`
3. **Metadata** — 1 duplicate description groups found.
   Affected examples: `Hallucination, voice drift, prompt injection and consent — the safety : brand-ai-checks.html, live-event-stack-ai-peer.html`
4. **Social metadata** — 47 pages missing og:image.
   Affected examples: `about.html, agm.html, ai.html, anamorphic-camera.html, ar-earns-its-place.html, auto-anamorphic-reveal.html, auto.html, axis-employee-ai.html +39 more`
5. **Structured data** — 47 pages have no JSON-LD structured data.
   Affected examples: `about.html, agm.html, ai.html, anamorphic-camera.html, ar-earns-its-place.html, auto-anamorphic-reveal.html, auto.html, axis-employee-ai.html +39 more`
6. **Images** — 43 pages rely heavily on CSS background images. These visuals have no alt text and are weaker for image search/accessibility.
   Affected examples: `about.html (10 CSS background images), agm.html (8 CSS background images), ai.html (11 CSS background images), anamorphic-camera.html (10 CSS background images), ar-earns-its-place.html (10 CSS background images), auto-anamorphic-reveal.html (10 CSS background images), auto.html (13 CSS background images), axis-employee-ai.html (10 CSS background images) +12 more`

## Positive Checks
- Viewport meta present on **47/47** pages.
- Exactly one H1 on **47/47** pages.
- Internal HTML file links: **0 missing file links** found.
- Legal/general email and HQ fixes were not part of this crawl's scoring, but the build still appears internally consistent from the latest pass.

## Largest HTML Files
- `index.html` — 7.20 MB
- `studio.html` — 3.82 MB
- `auto.html` — 2.86 MB
- `live.html` — 2.70 MB
- `work.html` — 2.60 MB
- `use-cases.html` — 2.49 MB
- `pharma.html` — 2.45 MB
- `fmcg.html` — 2.27 MB
- `industries.html` — 2.27 MB
- `xr.html` — 2.22 MB

## Recommended Fix Order
1. Add `robots.txt` and `sitemap.xml` with the final production domain.
2. Add unique canonical URLs to every page.
3. Move major images out of embedded base64 and into real image files with descriptive filenames, width/height, lazy loading and compression.
4. Add JSON-LD: Organization, WebSite, BreadcrumbList globally; Article for insights; Service/Product or FAQ where appropriate.
5. Review meta descriptions and titles for the outlier pages once final production URLs and priority keywords are confirmed.
6. Add descriptive alt text for content images; keep decorative logo/intro images empty only where appropriate.
7. Add final Open Graph image URLs that are crawlable files, not embedded data or missing metadata.
