# Zlicc Live Corporate Website SEO Audit — 2026-05-16

Live site audited: [https://website.zlicc.io/](https://website.zlicc.io/)

Pages crawled: **48** HTML pages discovered from live internal links.

Unique image URLs discovered: **200** across **749** usage occurrences.

SEO readiness score: **42/100**.

## Executive Verdict

**Not launch-ready for corporate SEO yet.** The CDN/image update appears to have helped dramatically: the homepage is now ~156 KB HTML rather than multi-megabyte base64 HTML. However, corporate-site SEO is still blocked by missing robots/sitemap, missing OG image coverage, incomplete structured data, three broken placeholder image URLs, and missing cache headers. Canonicals are now present on all crawled pages, but they point to the staging domain `website.zlicc.io`; switch them if the final corporate domain is different.

## Crawl Summary

- Homepage HTTP status: **200**
- `robots.txt`: **HTTP 404**
- `sitemap.xml`: **HTTP 404**
- Homepage size: **155.8 KB**
- Homepage server: **nginx/1.24.0 (Ubuntu)**
- HTML compression detected: **gzip**
- Home Cache-Control: **not set**

## Image/CDN Check

- Embedded `data:image` pages: **48**
- Unique image URL status counts: **{'200': 196, 'data': 1, '404': 3}**
- Image domains:
  - `zlicc-content.s3.ap-south-1.amazonaws.com` — 196
  - `website.zlicc.io` — 3
  - `data-url` — 1

## Findings

### Critical Priority

1. **Indexability** — robots.txt returns HTTP 404.
   Examples:
   - `https://website.zlicc.io/robots.txt`

2. **Indexability** — sitemap.xml returns HTTP 404.
   Examples:
   - `https://website.zlicc.io/sitemap.xml`

### High Priority

1. **Social metadata** — 48 pages missing og:image.
   Examples:
   - `https://website.zlicc.io/`
   - `https://website.zlicc.io/index.html`
   - `https://website.zlicc.io/solutions.html`
   - `https://website.zlicc.io/sync.html`
   - `https://website.zlicc.io/pulse.html`
   - `https://website.zlicc.io/ai.html`
   - `https://website.zlicc.io/xr.html`
   - `https://website.zlicc.io/live.html`

2. **Structured data** — 36 pages have no JSON-LD structured data.
   Examples:
   - `https://website.zlicc.io/`
   - `https://website.zlicc.io/index.html`
   - `https://website.zlicc.io/solutions.html`
   - `https://website.zlicc.io/work.html`
   - `https://website.zlicc.io/npci-ai-summit.html`
   - `https://website.zlicc.io/siemens-ai-video.html`
   - `https://website.zlicc.io/hdfc-engagement-map.html`
   - `https://website.zlicc.io/axis-employee-ai.html`

3. **Images** — 3 unique image URLs returned non-2xx or failed.
   Examples:
   - `https://website.zlicc.io/{{HERO_BG}} -> 404`
   - `https://website.zlicc.io/{{CASE_NPCI}} -> 404`
   - `https://website.zlicc.io/{{FINAL_BG}} -> 404`

### Medium Priority

1. **Metadata** — 1 duplicate title groups found.
   Examples:
   - `Zlicc · Experience Infrastructure for Events & Brands: https://website.zlicc.io/, https://website.zlicc.io/index.html`

2. **Metadata** — 1 duplicate description groups found.
   Examples:
   - `Experiences that look spectacular. Systems that work under pressure. Z: https://website.zlicc.io/, https://website.zlicc.io/index.html`

3. **Images** — 48 pages still contain embedded data:image assets.
   Examples:
   - `https://website.zlicc.io/ (1 data images)`
   - `https://website.zlicc.io/index.html (1 data images)`
   - `https://website.zlicc.io/solutions.html (2 data images)`
   - `https://website.zlicc.io/sync.html (2 data images)`
   - `https://website.zlicc.io/pulse.html (2 data images)`
   - `https://website.zlicc.io/ai.html (2 data images)`
   - `https://website.zlicc.io/xr.html (2 data images)`
   - `https://website.zlicc.io/live.html (2 data images)`

4. **Server headers** — Home page has no Cache-Control header. Add sensible cache rules for HTML and long immutable caching for assets.
   Examples:
   - `https://website.zlicc.io/`

### Low Priority

1. **Images** — 199 unique images are used as CSS backgrounds. Fine for decorative imagery, but important content visuals should ideally be real <img>/<picture> with alt text.

## Positive Checks

- Canonical tags are present on **48/48** pages and currently point to `website.zlicc.io`.
- Exactly one H1 on **48/48** pages.
- Internal missing-file links found: **0**.
- Missing internal anchors found: **0**.
- Base64 image issue is mostly resolved: **48 pages still include data images** versus the old build where nearly all major images were embedded.
- Duplicate title groups found: **1** (`/` and `/index.html`, both canonicalized to `/`; ideally redirect `/index.html` to `/`).

## Largest Live HTML Pages

- `https://website.zlicc.io/studio.html` — 178.8 KB
- `https://website.zlicc.io/ai.html` — 178.5 KB
- `https://website.zlicc.io/mice.html` — 177.6 KB
- `https://website.zlicc.io/auto.html` — 177.5 KB
- `https://website.zlicc.io/xr.html` — 177.5 KB
- `https://website.zlicc.io/fmcg.html` — 177.4 KB
- `https://website.zlicc.io/live.html` — 177.4 KB
- `https://website.zlicc.io/pulse.html` — 177.3 KB
- `https://website.zlicc.io/tech.html` — 177.2 KB
- `https://website.zlicc.io/pharma.html` — 177.1 KB
- `https://website.zlicc.io/sync.html` — 177.1 KB
- `https://website.zlicc.io/bfsi.html` — 177.0 KB

## Recommended Launch Fix Order

1. Publish `robots.txt` and `sitemap.xml` immediately. Include all canonical page URLs.
2. Add canonical tags to every page. If the final corporate domain is not `website.zlicc.io`, canonicals should point to the final production domain, not this staging domain.
3. Add JSON-LD: Organization, WebSite, BreadcrumbList globally; Article schema for insights; Service schema for solution/use-case pages; CaseStudy/CreativeWork where appropriate for Work pages.
4. Add `og:image` to every page using CDN-hosted 1200×630 images.
5. Enable gzip or Brotli compression and cache headers at Nginx/CDN level.
6. Tighten long meta descriptions and title outliers.
7. Review CSS-background images: keep decorative backgrounds as CSS, but convert content-bearing visuals to `<img>`/`picture` with descriptive alt text.

CSV page export: `/Users/anubhavbajpai/Documents/New project 2/zlicc-live-seo-pages-2026-05-16.csv`

CSV image export: `/Users/anubhavbajpai/Documents/New project 2/zlicc-live-seo-images-2026-05-16.csv`
