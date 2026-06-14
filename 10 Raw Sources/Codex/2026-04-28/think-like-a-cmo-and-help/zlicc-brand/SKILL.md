---
name: zlicc-brand
description: Apply the Zlicc brand system when designing or implementing apps, dashboards, websites, prototypes, decks, or UI artifacts for Zlicc. Use when the user asks for Zlicc-branded UI/UX, Apple-grade glossy/3D depth, premium CRM/SaaS dashboards, or asks to follow the Zlicc brand guidelines, colors, logo, or visual system.
---

# Zlicc Brand

## Core Direction

Use this skill to produce Zlicc-branded digital experiences that feel Apple-grade premium: luminous, glossy, dimensional, calm, fast, and conversion-minded. The finish should feel closer to iCloud/macOS native surfaces than loud gaming bevels or generic glassmorphism.

If the task is substantial, read `references/zlicc-ui-ux-brand-guidelines.md` before implementation. For quick UI work, apply the essentials below.

## Brand Essentials

- Use black, white, Zlicc Cyan, and premium yellow as the core palette.
- Treat cyan as the default luminous action/accent color.
- Treat yellow as a premium/Pro/upgrade/high-value accent, not a general highlight.
- Use glossy depth through soft highlights, hairline borders, layered shadows, and pressed states.
- Keep UI usable and scannable before making it decorative.
- Avoid all-purple, all-blue, beige, brown, loud neon, or generic template aesthetics.

### Color Tokens

```css
:root {
  --zlicc-black: #000000;
  --zlicc-white: #FFFFFF;
  --zlicc-cyan: #13CDE9;
  --zlicc-cyan-deep: #0798B0;
  --zlicc-cyan-soft: #BDF5FF;
  --zlicc-yellow: #FFE24C;
  --zlicc-yellow-deep: #D4A900;
  --zlicc-yellow-soft: #FFF6B8;
  --zlicc-graphite: #111318;
  --zlicc-ink: #101318;
  --zlicc-ink-soft: #596171;
  --zlicc-cloud: #F5F7FB;
  --zlicc-cloud-edge: #E7ECF4;
}
```

## Logo Assets

Use bundled logo files from `assets/logos/`:

- `zlicc-logo-cyan.png`: primary wordmark for dark premium surfaces.
- `zlicc-mark-cyan.png`: favicon, app icon, collapsed nav, loaders, compact UI.
- `zlicc-logo-yellow.png`: premium/Pro/upgrade/launch moments.

Do not recolor, rotate, skew, stretch, bevel, or add effects directly to the logo. If the white wordmark is used, place it on black/graphite or a dark glossy container.

## Apple-Grade Glossy Depth

Use this depth formula:

- Ambient gradient: very soft, barely noticed.
- Top highlight: translucent white, usually 8-42% opacity.
- Hairline edge: 1px translucent white or graphite border.
- Contact shadow: soft blur, low opacity, down/right.
- Brand aura: cyan by default; yellow only for premium moments.
- Pressed state: translate down 1px and collapse shadow.

Primary CTA pattern:

```css
.z-btn-primary {
  min-height: 44px;
  padding: 0 18px;
  border: 1px solid color-mix(in srgb, var(--zlicc-cyan) 72%, white);
  border-radius: 12px;
  background:
    linear-gradient(180deg, rgba(255,255,255,.42), rgba(255,255,255,.16) 38%, rgba(255,255,255,.03)),
    linear-gradient(145deg, color-mix(in srgb, var(--zlicc-cyan) 62%, white), var(--zlicc-cyan) 46%, color-mix(in srgb, var(--zlicc-cyan-deep) 90%, black));
  box-shadow:
    0 1px 0 rgba(255,255,255,.52) inset,
    0 -1px 0 rgba(0,0,0,.18) inset,
    0 16px 34px rgba(19,205,233,.30),
    0 5px 12px rgba(17,19,24,.18);
  color: white;
  font-weight: 760;
}
```

Premium CTA pattern:

```css
.z-btn-premium {
  min-height: 44px;
  padding: 0 18px;
  border: 1px solid rgba(255,249,200,.92);
  border-radius: 12px;
  background:
    linear-gradient(180deg, rgba(255,255,255,.42), rgba(255,255,255,.16) 38%, rgba(255,255,255,.03)),
    linear-gradient(145deg, #FFF9C8, var(--zlicc-yellow) 45%, var(--zlicc-yellow-deep));
  box-shadow:
    0 1px 0 rgba(255,255,255,.58) inset,
    0 -1px 0 rgba(128,86,0,.22) inset,
    0 14px 28px rgba(255,226,76,.30),
    0 3px 8px rgba(17,19,24,.15);
  color: #171400;
  font-weight: 760;
}
```

## UI Guidance

- Use dark glossy command panels for high-value dashboards, AI copilots, revenue command centers, and hero surfaces.
- Use off-white cloud backgrounds with subtle cyan/yellow ambient light.
- Use frosted shells for app chrome, topbars, side panels, and floating controls.
- Use compact, utilitarian SaaS layouts for operational tools. Do not make a marketing landing page when the user asks for an app or dashboard.
- Use data-rich cards, tables, charts, filters, badges, and workflow surfaces for CRM/SaaS products.
- Use stable dimensions for buttons, cards, boards, toolbars, charts, and tables so hover/loading states do not shift layout.
- Keep text readable, never overlapping, and accessible against gradients.

## Workflow

1. Identify the product type and primary user workflow.
2. Load the full guideline reference for non-trivial work.
3. Copy or reference the needed logo asset from `assets/logos/`.
4. Implement tokens first: colors, radii, shadows, typography, motion.
5. Build reusable components: shell, nav, buttons, inputs, cards, badges, tables, charts, modals, toasts.
6. Apply Apple-grade depth to primary controls and premium surfaces only.
7. Verify desktop and mobile layouts visually before delivering.

## Reference Implementation

Use `assets/examples/zlicc-crm-dashboard.html` as a concrete reference for a complex CRM dashboard with Zlicc colors, logos, glossy CTAs, dark command panel, charts, cards, pipeline data, and analytics.

When creating a new static HTML sample, it is acceptable to adapt this file. Copy it into the working project first; do not modify the skill asset directly unless the user asks to update the skill.
