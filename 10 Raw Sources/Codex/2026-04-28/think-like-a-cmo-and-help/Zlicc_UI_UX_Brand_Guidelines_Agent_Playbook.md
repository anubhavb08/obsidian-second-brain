# Zlicc UI/UX Brand Guidelines

## Agent-Ready Brand Playbook for Premium Glossy Applications

**Version:** 1.1  
**Date:** April 28, 2026  
**Audience:** Product designers, frontend engineers, coding agents, AI app builders  
**Primary goal:** Every Zlicc application should feel Apple-grade premium: luminous, glossy, dimensional, tactile, calm, fast, and conversion-minded without sacrificing usability.

---

## 1. Executive Brand Direction

Zlicc should feel like a premium digital product: sharp, polished, fast, modern, and quietly luxurious. The interface language should signal trust and sophistication at first glance, then reward use with smooth interactions, clear hierarchy, and tactile controls.

When this guide says **3D depth** and **glossy finish**, it does not mean loud gaming-style bevels or cheap glassmorphism. It means the Apple/iCloud/Mac quality bar: luminous material, softened light, deep but quiet shadows, tactile controls, crisp typography, generous breathing room, and refined motion.

The brand experience should be:

- **Glossy:** Surfaces should catch light through controlled highlights, reflections, and luminous edges.
- **Dimensional:** Buttons, panels, toggles, and controls should feel physically present and pressable.
- **Premium:** Restraint matters. Use gloss and depth intentionally, not everywhere at maximum intensity.
- **Apple-grade:** The interface should feel closer to iCloud, macOS, and high-end native app surfaces than a generic web dashboard.
- **Clear:** Every screen should be easy to scan, understand, and act on.
- **Fast:** Motion should feel crisp and responsive, never slow or theatrical.
- **Agent-consumable:** The system should translate into tokens, reusable components, and clear acceptance criteria.

### CMO-Level Positioning

Zlicc should not look like a basic SaaS dashboard or a generic AI tool. It should look like a product that understands status, confidence, and momentum. The visual language should make the user feel they are operating something premium and capable.

Use this guiding phrase:

> Zlicc interfaces should feel like Apple-grade polished command surfaces: luminous, precise, dimensional, and built for confident action.

---

## 2. Logo System and Brand Colors

The Zlicc logo system has three supplied PNG variations. The extracted production color anchors are black, white, electric cyan, and premium yellow.

### Supplied Logo Variations

| Logo | File | Primary Use |
|---|---|---|
| Cyan mark only | `brand-assets/zlicc-mark-cyan.png` | Favicon, app icon, collapsed sidebar, loading mark, product watermark |
| White wordmark with cyan mark | `brand-assets/zlicc-logo-cyan.png` | Primary logo on black or very dark premium surfaces |
| White wordmark with yellow mark | `brand-assets/zlicc-logo-yellow.png` | Premium, Pro, upgrade, launch, celebratory, or limited-edition contexts |

![Zlicc cyan mark](brand-assets/zlicc-mark-cyan.png)
![Zlicc cyan logo](brand-assets/zlicc-logo-cyan.png)
![Zlicc yellow premium logo](brand-assets/zlicc-logo-yellow.png)

### Extracted Brand Palette

| Token | Hex | Role |
|---|---:|---|
| Zlicc Black | `#000000` | Logo background, dark premium UI, high-contrast shells |
| Zlicc White | `#FFFFFF` | Wordmark, text on dark, clean surfaces |
| Zlicc Cyan | `#13CDE9` | Primary luminous brand accent, focus, active states, signature mark |
| Zlicc Yellow | `#FFE24C` | Premium accent, Pro states, highlights, upgrade moments |
| Soft Cloud | `#F5F7FB` | Apple-grade page background |
| Cloud Edge | `#E7ECF4` | Hairline borders, dividers |
| Graphite | `#111318` | Premium dark surface, near-black UI |
| Slate Text | `#596171` | Secondary text |

### Production Token Palette

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
  --zlicc-graphite-soft: #242832;
  --zlicc-ink: #101318;
  --zlicc-ink-soft: #596171;
  --zlicc-cloud: #F5F7FB;
  --zlicc-cloud-edge: #E7ECF4;
  --zlicc-surface-raised: #FFFFFF;
  --zlicc-surface-dark: #050608;
  --zlicc-border: rgba(17, 19, 24, 0.12);

  --zlicc-success: #18C98B;
  --zlicc-warning: #FFB547;
  --zlicc-danger: #FF4D6D;
}
```

### Logo Usage Rules

- Use the **white wordmark with cyan mark** as the default brand signature on dark surfaces.
- Use the **cyan mark-only logo** for compact app areas, favicons, loading states, and icon-led product moments.
- Use the **yellow mark variation** only for premium, Pro, monetization, launch, celebration, or high-value conversion moments.
- Do not place the white wordmark on light backgrounds unless it sits inside a dark glossy container.
- Do not recolor the logo casually. If a monochrome version is required, use pure black or pure white only.
- Maintain clear space around the logo equal to at least the height of the cyan/yellow mark.
- The mark should feel like a directional, upward-moving signal. Do not rotate, mirror, skew, stretch, bevel, or add drop shadows directly to the logo file.

### Palette Rule

Zlicc should feel black, white, cyan, and premium yellow, supported by cloud-like neutral surfaces. Avoid making the interface entirely cyan or entirely black. The cyan should behave like luminous energy; the yellow should behave like premium emphasis.

---

## 3. Visual Identity Principles

### 3.1 Gloss Must Follow a Light Source

Glossy UI fails when highlights are random. Assume one consistent light source:

- **Primary light:** top-left
- **Secondary glow:** soft cyan ambient light, with yellow reserved for premium moments
- **Shadow direction:** down and slightly right
- **Specular highlight:** top edge or upper third of surfaces

All components should follow this same lighting logic.

### 3.1.1 Apple-Grade Material Standard

The desired finish should feel closer to macOS/iCloud surfaces than glossy plastic. Use:

- Large, quiet gradients instead of harsh bevels.
- Soft, layered shadows instead of one visible shadow.
- Thin luminous borders on dark surfaces.
- Frosted translucency only when content behind it remains calm and readable.
- Rounded geometry that feels native and precise.
- High-resolution logo assets, never pixelated or stretched.

### 3.2 Depth Should Be Functional

Depth should clarify interaction:

- Primary actions get the most depth.
- Secondary actions get reduced depth.
- Disabled states flatten and lose shine.
- Pressed states move downward and reduce shadow.
- Hover states lift slightly and brighten.

### 3.3 Premium Means Controlled Contrast

Premium finish comes from details:

- Thin borders with partial opacity.
- Layered shadows, not one harsh shadow.
- Subtle inner highlights.
- Smooth gradients with small hue shifts.
- Rounded corners that feel precise, not cartoon-like.
- Motion that is quick and confident.

### 3.4 No Generic Glassmorphism

Zlicc can use translucent panels, but avoid overused frosted-glass blur everywhere. Use glass only where it improves hierarchy or creates a premium control-surface effect.

---

## 4. UI Design Tokens

### 4.1 Color Tokens

Use semantic tokens instead of hardcoded colors.

```css
:root {
  --color-brand-primary: var(--zlicc-cyan);
  --color-brand-primary-hover: color-mix(in srgb, var(--zlicc-cyan) 82%, white);
  --color-brand-primary-active: color-mix(in srgb, var(--zlicc-cyan) 78%, black);
  --color-brand-secondary: var(--zlicc-black);
  --color-brand-premium: var(--zlicc-yellow);

  --color-bg-page: var(--zlicc-cloud);
  --color-bg-shell: #FFFFFF;
  --color-bg-elevated: #FFFFFF;
  --color-bg-dark: var(--zlicc-surface-dark);

  --color-text-primary: var(--zlicc-ink);
  --color-text-secondary: var(--zlicc-ink-soft);
  --color-text-muted: #7C8497;
  --color-text-inverse: #FFFFFF;

  --color-border-subtle: rgba(17, 19, 24, 0.10);
  --color-border-strong: rgba(17, 19, 24, 0.20);
  --color-focus: var(--zlicc-cyan);
}
```

### 4.2 Gloss Tokens

```css
:root {
  --gloss-highlight-top: linear-gradient(
    180deg,
    rgba(255, 255, 255, 0.42) 0%,
    rgba(255, 255, 255, 0.16) 38%,
    rgba(255, 255, 255, 0.03) 100%
  );

  --gloss-brand: linear-gradient(
    145deg,
    color-mix(in srgb, var(--zlicc-cyan) 62%, white) 0%,
    var(--zlicc-cyan) 46%,
    color-mix(in srgb, var(--zlicc-cyan-deep) 90%, black) 100%
  );

  --gloss-premium: linear-gradient(
    145deg,
    #FFF9C8 0%,
    var(--zlicc-yellow) 45%,
    var(--zlicc-yellow-deep) 100%
  );

  --gloss-metal: linear-gradient(
    145deg,
    #FFFFFF 0%,
    #EEF1F8 42%,
    #C9CEDA 100%
  );

  --gloss-dark: linear-gradient(
    145deg,
    #252932 0%,
    #111318 48%,
    #050608 100%
  );

  --gloss-cloud: linear-gradient(
    180deg,
    rgba(255,255,255,0.96) 0%,
    rgba(245,247,251,0.92) 100%
  );
}
```

### 4.3 Shadow Tokens

Use layered shadows for a 3D premium finish.

```css
:root {
  --shadow-button-rest:
    0 1px 0 rgba(255, 255, 255, 0.42) inset,
    0 -1px 0 rgba(0, 0, 0, 0.18) inset,
    0 10px 22px rgba(19, 205, 233, 0.24),
    0 2px 6px rgba(17, 19, 24, 0.16);

  --shadow-button-hover:
    0 1px 0 rgba(255, 255, 255, 0.50) inset,
    0 -1px 0 rgba(0, 0, 0, 0.16) inset,
    0 16px 34px rgba(19, 205, 233, 0.30),
    0 5px 12px rgba(17, 19, 24, 0.18);

  --shadow-button-pressed:
    0 1px 1px rgba(0, 0, 0, 0.18) inset,
    0 2px 6px rgba(17, 19, 24, 0.18);

  --shadow-card:
    0 1px 0 rgba(255, 255, 255, 0.70) inset,
    0 24px 54px rgba(17, 19, 24, 0.10),
    0 4px 14px rgba(17, 19, 24, 0.07);

  --shadow-panel-dark:
    0 1px 0 rgba(255, 255, 255, 0.12) inset,
    0 24px 60px rgba(0, 0, 0, 0.38);

  --shadow-premium-yellow:
    0 1px 0 rgba(255, 255, 255, 0.58) inset,
    0 -1px 0 rgba(128, 86, 0, 0.22) inset,
    0 14px 28px rgba(255, 226, 76, 0.30),
    0 3px 8px rgba(17, 19, 24, 0.15);
}
```

### 4.4 Radius Tokens

Rounded, but not soft-toy rounded.

```css
:root {
  --radius-xs: 6px;
  --radius-sm: 8px;
  --radius-md: 12px;
  --radius-lg: 16px;
  --radius-xl: 24px;
  --radius-pill: 999px;
}
```

Use:

| Component | Radius |
|---|---:|
| Compact buttons | `8px` |
| Primary buttons | `10px` to `12px` |
| Inputs | `10px` |
| Cards | `12px` to `16px` |
| Modals | `16px` to `24px` |
| Pills/badges | `999px` |

### 4.5 Spacing Tokens

```css
:root {
  --space-1: 4px;
  --space-2: 8px;
  --space-3: 12px;
  --space-4: 16px;
  --space-5: 20px;
  --space-6: 24px;
  --space-8: 32px;
  --space-10: 40px;
  --space-12: 48px;
  --space-16: 64px;
}
```

Keep operational screens dense but comfortable. Marketing pages can breathe more; application screens should prioritize repeated use.

### 4.6 Typography Tokens

Recommended typefaces:

- **Primary UI font:** Inter, SF Pro, Geist, or similar modern sans serif.
- **Display font:** Same family in heavier weight unless Zlicc has a custom brand typeface.
- **Numerics:** Use tabular numbers for dashboards, pricing, timers, analytics, and financial values.

```css
:root {
  --font-sans: Inter, ui-sans-serif, system-ui, -apple-system, BlinkMacSystemFont, "Segoe UI", sans-serif;
  --font-mono: "SF Mono", "Roboto Mono", ui-monospace, monospace;

  --text-xs: 12px;
  --text-sm: 14px;
  --text-md: 16px;
  --text-lg: 18px;
  --text-xl: 22px;
  --text-2xl: 28px;
  --text-3xl: 36px;
  --text-4xl: 48px;

  --leading-tight: 1.15;
  --leading-body: 1.5;
  --leading-relaxed: 1.65;
}
```

Typography rules:

- Do not scale font size with viewport width.
- Letter spacing should generally be `0`.
- Use weight and spacing for hierarchy before adding more colors.
- Keep dashboards compact and scannable.
- Use short, action-oriented labels.

---

## 5. Surface System

Zlicc should use a layered surface model.

### 5.1 Page Background

Use an off-white or deep-dark base, never pure flat gray. Add subtle ambient lighting only when it supports the content.

Light mode:

```css
.z-page {
  background:
    radial-gradient(circle at 18% 0%, rgba(19, 205, 233, 0.12), transparent 30%),
    linear-gradient(180deg, #FFFFFF 0%, var(--zlicc-cloud) 100%);
  color: var(--color-text-primary);
}
```

Dark mode:

```css
.z-page-dark {
  background:
    radial-gradient(circle at 20% 0%, rgba(19, 205, 233, 0.18), transparent 28%),
    linear-gradient(180deg, #161A20 0%, #050608 100%);
  color: var(--color-text-inverse);
}
```

### 5.2 Raised Panels

Raised panels should feel like polished plates.

```css
.z-panel {
  background:
    var(--gloss-cloud),
    var(--color-bg-elevated);
  border: 1px solid rgba(255,255,255,0.70);
  border-radius: var(--radius-lg);
  box-shadow: var(--shadow-card);
}
```

### 5.3 Dark Premium Panels

Use dark panels for high-value moments: command centers, upgrade flows, pro features, AI copilots, and hero sections.

```css
.z-panel-premium {
  background:
    var(--gloss-highlight-top),
    var(--gloss-dark);
  border: 1px solid rgba(255, 255, 255, 0.12);
  border-radius: var(--radius-xl);
  box-shadow: var(--shadow-panel-dark);
  color: #FFFFFF;
}
```

### 5.4 Apple-Grade Frosted Shells

Use frosted translucency for app chrome, floating command surfaces, and contextual side panels. It should feel like macOS material, not a decorative blur layer.

```css
.z-frosted-shell {
  background:
    linear-gradient(180deg, rgba(255,255,255,0.78), rgba(245,247,251,0.66));
  border: 1px solid rgba(255,255,255,0.72);
  box-shadow:
    0 1px 0 rgba(255,255,255,0.82) inset,
    0 22px 60px rgba(17,19,24,0.12);
  backdrop-filter: blur(22px) saturate(1.25);
  -webkit-backdrop-filter: blur(22px) saturate(1.25);
}
```

---

## 6. Component Guidelines

### 6.1 Buttons

Buttons are the signature tactile element of Zlicc.

#### Primary Button

Use primary buttons for the main action per view. They should be glossy, dimensional, and unmistakably clickable. The default primary button uses Zlicc Cyan and should feel like a luminous native control.

```css
.z-btn-primary {
  appearance: none;
  position: relative;
  min-height: 44px;
  padding: 0 18px;
  border: 1px solid color-mix(in srgb, var(--zlicc-cyan) 72%, white);
  border-radius: 12px;
  background:
    var(--gloss-highlight-top),
    var(--gloss-brand);
  box-shadow: var(--shadow-button-rest);
  color: white;
  font: 700 14px/1 var(--font-sans);
  cursor: pointer;
  transform: translateY(0);
  transition:
    transform 140ms ease,
    box-shadow 140ms ease,
    filter 140ms ease;
}

.z-btn-primary:hover {
  transform: translateY(-1px);
  box-shadow: var(--shadow-button-hover);
  filter: saturate(1.05) brightness(1.03);
}

.z-btn-primary:active {
  transform: translateY(1px);
  box-shadow: var(--shadow-button-pressed);
}

.z-btn-primary:focus-visible {
  outline: 3px solid color-mix(in srgb, var(--color-focus) 58%, transparent);
  outline-offset: 3px;
}
```

#### Button Anatomy

Every primary button should include:

- A glossy gradient.
- An inner top highlight.
- A lower inner shadow.
- A soft projected shadow.
- A pressed state that visually moves down.
- A clear focus state.

#### Premium Yellow Button

Use the yellow variant only for premium or high-value moments: Upgrade, Go Pro, Launch, Publish, Confirm purchase, or celebratory completion. It should feel rich and luminous, not alarming.

```css
.z-btn-premium {
  min-height: 44px;
  padding: 0 18px;
  border: 1px solid rgba(255, 249, 200, 0.92);
  border-radius: 12px;
  background:
    var(--gloss-highlight-top),
    var(--gloss-premium);
  box-shadow: var(--shadow-premium-yellow);
  color: #171400;
  font: 760 14px/1 var(--font-sans);
}
```

#### Secondary Button

Secondary buttons should feel premium but less loud.

```css
.z-btn-secondary {
  min-height: 40px;
  padding: 0 16px;
  border: 1px solid rgba(16, 19, 26, 0.12);
  border-radius: 10px;
  background:
    linear-gradient(180deg, rgba(255,255,255,0.96), rgba(238,241,248,0.92));
  box-shadow:
    0 1px 0 rgba(255,255,255,0.9) inset,
    0 6px 14px rgba(16,19,26,0.08);
  color: var(--color-text-primary);
  font: 650 14px/1 var(--font-sans);
}
```

#### Button Usage Rules

- One primary action per screen section.
- Use icons for clear tool actions.
- Use text labels for business-critical actions.
- Avoid large pill buttons everywhere; reserve pill shape for filters and segmented controls.
- Disabled buttons should flatten, desaturate, and reduce shadow.

### 6.2 Inputs

Inputs should feel precise, clean, and high-quality.

```css
.z-input {
  min-height: 44px;
  padding: 0 14px;
  border: 1px solid rgba(16,19,26,0.14);
  border-radius: 10px;
  background:
    linear-gradient(180deg, #FFFFFF 0%, #F7F8FC 100%);
  box-shadow:
    0 1px 0 rgba(255,255,255,0.8) inset,
    0 1px 2px rgba(16,19,26,0.05);
  color: var(--color-text-primary);
  font: 500 14px/1.4 var(--font-sans);
}

.z-input:focus {
  border-color: var(--color-focus);
  box-shadow:
    0 0 0 3px color-mix(in srgb, var(--color-focus) 20%, transparent),
    0 1px 0 rgba(255,255,255,0.8) inset;
  outline: none;
}
```

Input rules:

- Labels should be concise and outside the input.
- Placeholder text should give an example, not replace the label.
- Error text should be specific and human.
- Required fields should be obvious but not visually noisy.

### 6.3 Cards

Cards should be used for repeated items, product entities, metric blocks, and content groupings. Do not place cards inside cards unless there is a strong structural reason.

```css
.z-card {
  border: 1px solid rgba(255,255,255,0.72);
  border-radius: 16px;
  background:
    linear-gradient(180deg, rgba(255,255,255,0.96), rgba(246,248,253,0.92));
  box-shadow: var(--shadow-card);
}
```

Card rules:

- Keep card radius between `12px` and `16px`.
- Use a thin top highlight for premium finish.
- Do not make every section a floating card.
- Use clear spacing between cards.
- Keep headings inside cards compact.

### 6.4 Navigation

Navigation should feel like part of the product shell, not decoration.

Desktop app shell:

- Left sidebar for complex SaaS/productivity apps.
- Top nav for simpler apps or public web pages.
- Use icon + label for main sections.
- Use active state with a glossy brand accent, not only text color.
- Keep the logo visible and respected with clear spacing.

Active nav example:

```css
.z-nav-item-active {
  background:
    linear-gradient(180deg, rgba(255,255,255,0.30), rgba(255,255,255,0.08)),
    color-mix(in srgb, var(--zlicc-cyan) 16%, transparent);
  border: 1px solid color-mix(in srgb, var(--zlicc-cyan) 24%, transparent);
  box-shadow: inset 0 1px 0 rgba(255,255,255,0.35);
}
```

### 6.5 Modals and Dialogs

Modals should feel important, calm, and structured.

Rules:

- Use a subtle backdrop blur or dark overlay.
- Modal surfaces should be raised with layered shadow.
- Primary action should be glossy.
- Destructive action should not use the primary brand button.
- Keep title, body, and actions clearly separated.
- On mobile, use bottom sheets for short tasks.

### 6.6 Tables and Data Grids

Zlicc tables should feel operational and premium, not spreadsheet-like.

Rules:

- Use sticky headers for long data sets.
- Use row hover with a subtle glossy tint.
- Use tabular numbers.
- Align numbers right, labels left, statuses center.
- Avoid heavy borders; use hairlines and spacing.
- Use compact density controls if the product is data-heavy.

```css
.z-table thead th {
  background: linear-gradient(180deg, #FFFFFF, #EEF1F8);
  border-bottom: 1px solid rgba(16,19,26,0.12);
  color: var(--color-text-secondary);
  font-size: 12px;
  font-weight: 700;
  text-transform: uppercase;
}

.z-table tbody tr:hover {
  background: color-mix(in srgb, var(--zlicc-cyan) 6%, white);
}
```

### 6.7 Badges and Status Pills

Badges should be compact, readable, and semantically colored.

Examples:

- Success: green tint with dark green text.
- Warning: amber tint with brown/ink text.
- Error: red tint with red text.
- Premium: brand gradient or metallic gloss.
- Neutral: gray/ink tint.

Avoid vague colors without labels.

### 6.8 Toolbars

Use icon buttons for tools, with tooltips for anything not universally obvious.

Rules:

- Icon buttons should be square or circular with stable dimensions.
- Hover states should not shift layout.
- Active tool buttons should use a brand-tinted glossy fill.
- Use grouped segmented controls for mutually exclusive modes.

---

## 7. Motion and Interaction

Motion should make the product feel responsive and expensive.

### Motion Principles

- Keep microinteractions between `120ms` and `220ms`.
- Use ease-out for entrances.
- Use ease-in for exits.
- Avoid bouncy motion in serious workflows.
- Use spring motion only for playful or celebratory moments.
- Respect `prefers-reduced-motion`.

```css
@media (prefers-reduced-motion: reduce) {
  * {
    animation-duration: 0.01ms !important;
    animation-iteration-count: 1 !important;
    scroll-behavior: auto !important;
    transition-duration: 0.01ms !important;
  }
}
```

### Interaction States

Every interactive component must define:

- Rest
- Hover
- Active/pressed
- Focus-visible
- Disabled
- Loading
- Success/failure feedback where relevant

### Loading States

Loading should feel refined:

- Use skeletons for content areas.
- Use inline spinners only for compact actions.
- Buttons should show loading state without changing width.
- Avoid full-page blocking loaders unless unavoidable.

---

## 8. UX Strategy

### 8.1 Experience Goals

Every Zlicc application should help users feel:

- **In control:** Actions are clear and reversible where possible.
- **Confident:** The UI makes next steps obvious.
- **Fast:** Repeated workflows are efficient.
- **Upgraded:** Premium finish reinforces the value of the product.

### 8.2 Information Architecture

For application products:

- Start with the user’s main job, not a marketing hero.
- Place primary workflows within one click from the main shell.
- Keep navigation labels concrete.
- Use dashboard summaries only when they help a user decide what to do next.
- Avoid empty decorative panels.

### 8.3 Screen Layout

Recommended layout for operational apps:

- Persistent sidebar or top shell.
- Page header with title, context, and primary action.
- Main content area with clear sections.
- Right-side contextual panel only when it improves workflow.
- Modals for focused tasks.

Page header pattern:

| Area | Content |
|---|---|
| Left | Page title, short context, breadcrumb if needed |
| Right | Primary action, secondary actions, filters |
| Below | Tabs, metrics, or search if relevant |

### 8.4 Empty States

Empty states should be helpful, not cute.

Each empty state should include:

- Clear title.
- One-sentence explanation.
- Primary action.
- Optional secondary action.
- A small brand-relevant visual if available.

### 8.5 Error States

Errors should be direct and calm.

Good error copy:

- Says what happened.
- Says how to fix it.
- Preserves user input.
- Offers retry if relevant.

Avoid blame language.

### 8.6 Onboarding

Premium onboarding should be brief and action-led.

Rules:

- Do not over-explain the product.
- Ask only for necessary setup information.
- Show progress when setup has multiple steps.
- Use progressive disclosure.
- Celebrate completion subtly.

---

## 9. Glossy 3D Finish Specification

This is the most important visual requirement.

The reference quality bar is Apple-grade iCloud/Mac UI: soft luminous surfaces, precise depth, native-feeling controls, and premium restraint. Avoid heavy bevels, thick borders, cartoon shine, noisy gradients, or shadows that make components look detached from the page.

### 9.1 The Zlicc Button Finish

Primary buttons must appear like a polished, elevated object.

Required visual layers:

1. **Base fill:** Cyan brand gradient for default CTAs, yellow gradient for premium CTAs.
2. **Top reflection:** Semi-transparent white gradient.
3. **Edge definition:** Thin lighter top border and darker bottom edge.
4. **Projected shadow:** Soft cyan or yellow aura plus neutral contact shadow.
5. **Inset shadow:** Adds material depth.
6. **Pressed state:** Moves down, shadow collapses.

### 9.2 The Zlicc Surface Finish

Premium panels should feel like high-grade coated material.

Required visual layers:

1. Background gradient.
2. Hairline border.
3. Inner highlight.
4. Soft drop shadow.
5. Optional ambient brand glow.

### 9.3 The Apple-Grade Depth Formula

Use this depth model for premium surfaces:

| Layer | Purpose | Guidance |
|---|---|---|
| Ambient gradient | Creates luminous material | Very soft; should barely be noticed |
| Top highlight | Suggests polished surface | White at 8-42% opacity depending on surface |
| Hairline edge | Defines the object | 1px border with translucent white or graphite |
| Contact shadow | Grounds the object | Soft blur, low opacity, down/right direction |
| Brand aura | Adds Zlicc energy | Cyan by default; yellow only for premium moments |
| Pressed state | Makes it tactile | Translate down 1px and collapse shadow |

### 9.4 Gloss Restraint Rules

Do not apply intense gloss to everything.

Use high gloss on:

- Primary CTAs.
- Premium upgrade actions.
- Important toggles.
- Hero product moments.
- Selected state of high-value controls.

Use low gloss on:

- Cards.
- Inputs.
- Tables.
- Navigation.
- Utility buttons.

Use no gloss on:

- Body text.
- Error text.
- Long-form content.
- Dense data rows.

---

## 10. Accessibility Requirements

Premium cannot come at the cost of usability.

### Contrast

- Body text must meet WCAG AA.
- Button text must meet WCAG AA.
- Do not rely on gradient alone for contrast.
- If using translucent surfaces, test contrast against actual backgrounds.

### Focus

- Every interactive element must have a visible focus state.
- Focus rings should be brand-aligned and high contrast.
- Keyboard navigation must follow visual order.

### Motion

- Respect reduced motion.
- Avoid flashing.
- Keep animations non-essential.

### Hit Targets

- Minimum touch target: `44px x 44px`.
- Icon-only controls need labels via `aria-label`.
- Tooltips do not replace accessible names.

---

## 11. Responsive Behavior

### Desktop

- Use spacious app shells.
- Keep page headers compact.
- Use sidebars for multi-section apps.
- Use tables with sticky headers for data-heavy tools.

### Tablet

- Reduce sidebars into collapsible rail navigation.
- Preserve primary actions in the header.
- Avoid cramped multi-column forms.

### Mobile

- Prioritize one-column layouts.
- Use bottom sheets for short modals.
- Keep primary action sticky only when it directly supports task completion.
- Avoid tiny icon-only controls unless obvious and accessible.

### Breakpoints

```css
:root {
  --bp-sm: 640px;
  --bp-md: 768px;
  --bp-lg: 1024px;
  --bp-xl: 1280px;
  --bp-2xl: 1536px;
}
```

---

## 12. Application Archetypes

### 12.1 SaaS Dashboard

Best for analytics, business tools, admin products.

Must include:

- Left navigation.
- Compact page header.
- Metric cards.
- Data tables.
- Filters and search.
- Clear primary action.

Avoid:

- Oversized hero banners.
- Decorative cards with no workflow value.
- Excessive gradients in every metric.

### 12.2 AI Tool or Copilot

Best for prompt-driven products and intelligent workflows.

Must include:

- Conversation or command area.
- Clear input affordance.
- Output cards with actions.
- Trust indicators: timestamps, sources, status, confidence where relevant.
- Interrupt/cancel controls for long-running tasks.

Premium treatment:

- Dark glossy command panel.
- Brand-colored active input glow.
- Subtle animated processing state.

### 12.3 Marketplace or Catalog

Best for browsing products, plugins, agents, templates, or assets.

Must include:

- Search.
- Filters.
- Sort.
- Card grid or list toggle.
- Detail view.
- Clear primary conversion action.

Premium treatment:

- High-quality thumbnails.
- Glossy premium badges.
- Refined hover previews.

### 12.4 Mobile App

Must include:

- Bottom navigation for 3-5 primary destinations.
- Large touch targets.
- Native-feeling transitions.
- Reduced visual density.
- Bottom sheets for contextual actions.

Premium treatment:

- Glossy primary FAB or sticky CTA.
- Polished cards with depth.
- Haptic-like pressed states through animation.

---

## 13. Content and Voice

Zlicc copy should be confident, concise, and useful.

### Voice Attributes

- Direct
- Premium
- Capable
- Clear
- Calm
- Action-oriented

### Button Copy

Use verbs:

- Create
- Launch
- Continue
- Upgrade
- Connect
- Generate
- Review
- Publish

Avoid vague labels:

- Submit
- Click here
- Go
- Next step

### UI Copy Rules

- Keep labels short.
- Explain outcomes, not implementation.
- Use sentence case.
- Avoid jargon unless the user segment expects it.
- Do not overload empty states with marketing copy.

---

## 14. Implementation Instructions for Coding Agents

Any coding agent building a Zlicc UI should follow this sequence.

### Step 1: Confirm Brand Inputs

Before building, locate:

- Zlicc logo files from `brand-assets/`.
- Official color values from the token table in this guide.
- Existing design components.
- Target platform and framework.
- Target user and product type.

Use `#13CDE9` as the default luminous brand accent and `#FFE24C` only for premium/high-value moments.

### Step 2: Create Design Tokens

Implement tokens first:

- Color tokens.
- Shadow tokens.
- Radius tokens.
- Typography tokens.
- Motion tokens.
- Component size tokens.

Do not scatter hardcoded values through components.

### Step 3: Build Core Components

At minimum, build:

- App shell.
- Button variants.
- Input fields.
- Select/dropdown.
- Checkbox/toggle.
- Modal/dialog.
- Card.
- Badge.
- Tooltip.
- Tabs.
- Table/list.
- Toast/alert.

### Step 4: Apply Premium Finish

For each component:

- Add top highlight where appropriate.
- Add inner edge definition.
- Add layered shadows.
- Add hover and pressed states.
- Tune the finish toward Apple-grade iCloud/Mac material, not loud bevels.
- Confirm depth does not create visual clutter.

### Step 5: Validate UX

Check:

- Is the primary action obvious?
- Can the user complete the main task quickly?
- Are errors recoverable?
- Is the information hierarchy clear?
- Is the UI accessible by keyboard?
- Does it remain polished on mobile?

### Step 6: Visual QA

Before delivery:

- Screenshot desktop and mobile.
- Check text overflow.
- Check contrast.
- Check disabled/loading states.
- Check hover/active/focus states.
- Check that the logo is crisp.
- Check that glossy finish is visible but not noisy.

---

## 15. Agent Prompt Template

Use this prompt when asking another coding agent to build a Zlicc interface:

```text
Build this product using the Zlicc UI/UX brand guidelines.

The UI must feel Apple-grade premium, glossy, dimensional, luminous, and conversion-focused. Use the Zlicc logo variations and official brand colors: black #000000, white #FFFFFF, cyan #13CDE9, and premium yellow #FFE24C.

Required visual style:
- Apple/iCloud/Mac-grade glossy finish on primary actions and premium surfaces.
- 3D button depth with top highlights, inner shadows, projected shadows, hover lift, and pressed compression.
- Cyan is the default luminous action color; yellow is reserved for premium, Pro, launch, or high-value moments.
- Clean premium surfaces with layered shadows and subtle borders.
- Strong hierarchy, high readability, and accessible contrast.
- Crisp, fast motion with reduced-motion support.

Implementation requirements:
- Create reusable design tokens.
- Build components from tokens rather than hardcoded styles.
- Include button, input, card, modal, nav, badge, table/list, toast, and tooltip states.
- Provide desktop and mobile responsive layouts.
- Verify hover, active, focus, disabled, loading, empty, and error states.
- Avoid generic flat SaaS styling and avoid excessive decorative gradients.

Acceptance criteria:
- The primary CTA looks tactile, glossy, and premium.
- The finish feels Apple-grade and restrained, not loud, plastic, or gaming-like.
- The app is usable and scannable before it is decorative.
- All interactive elements have visible states.
- Text does not overflow on mobile or desktop.
- The brand logo is respected with proper spacing and contrast.
- The interface feels like a polished Zlicc product, not a template.
```

---

## 16. Design QA Checklist

Use this checklist before accepting any Zlicc UI.

### Brand

- [ ] Official logo is present and crisp.
- [ ] Official colors are mapped to semantic tokens.
- [ ] Brand color is used with restraint and purpose.
- [ ] UI does not look like a generic template.

### Gloss and Depth

- [ ] Primary buttons have visible 3D depth.
- [ ] Pressed states visually compress.
- [ ] Hover states lift or brighten subtly.
- [ ] Gloss follows a consistent top-left light source.
- [ ] Shadows are layered and not harsh.

### UX

- [ ] The main user action is obvious.
- [ ] Navigation is clear.
- [ ] Empty states guide action.
- [ ] Errors explain recovery.
- [ ] Loading states preserve layout.

### Accessibility

- [ ] Contrast meets WCAG AA.
- [ ] Keyboard focus is visible.
- [ ] Icon-only buttons have accessible names.
- [ ] Touch targets are at least `44px`.
- [ ] Reduced-motion support is implemented.

### Responsive

- [ ] Desktop layout is polished.
- [ ] Tablet layout does not feel cramped.
- [ ] Mobile layout is one-column where appropriate.
- [ ] Text never overlaps controls.
- [ ] Buttons and cards maintain stable dimensions.

### Engineering

- [ ] Tokens are centralized.
- [ ] Components are reusable.
- [ ] Styling is not hardcoded per screen.
- [ ] States are implemented consistently.
- [ ] Screenshots or visual checks were completed.

---

## 17. Do and Do Not

### Do

- Use glossy primary CTAs.
- Use 3D depth where it improves interaction.
- Use semantic tokens.
- Use premium gradients with subtle shifts.
- Use restrained shadows.
- Use crisp typography.
- Use real product visuals when possible.
- Use icons for tool actions.
- Use accessible focus states.

### Do Not

- Do not make everything glossy.
- Do not use random highlights.
- Do not create flat, generic SaaS screens.
- Do not bury the primary action.
- Do not use low-contrast text on gradients.
- Do not rely on blur-heavy glassmorphism.
- Do not put cards inside cards as a default pattern.
- Do not create oversized marketing heroes for operational apps.
- Do not use decorative blobs or generic abstract backgrounds.
- Do not ship without mobile checks.

---

## 18. Final North Star

When judging a Zlicc interface, ask:

**Does this feel like a premium product that a user can trust, understand, and act inside immediately?**

If the answer is yes, the design is on-brand. If it only looks shiny but does not make the workflow clearer, reduce the decoration and strengthen the UX.

---

## 19. Reference Implementation

A sample Zlicc CRM dashboard has been created as a living implementation reference:

| Artifact | Path | Purpose |
|---|---|---|
| CRM dashboard | `zlicc-crm-dashboard/index.html` | Static Apple-grade glossy CRM dashboard using the Zlicc logo, cyan/yellow palette, dimensional buttons, cards, charts, pipeline data, and analytics |

Agents should use this dashboard as a concrete example of how the brand system should translate into application UI. It demonstrates:

- Dark premium command surfaces with the cyan Zlicc wordmark.
- Luminous cyan primary CTAs and yellow premium CTAs.
- Complex CRM metrics, funnel analytics, pipeline boards, tables, activity feeds, and charts.
- Soft Apple-grade depth through layered shadows, frosted shell treatment, glossy highlights, and precise radius.
- Responsive behavior for desktop, compact desktop/tablet, and mobile layouts.
