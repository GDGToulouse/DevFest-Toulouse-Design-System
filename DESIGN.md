---
version: alpha
name: DevFest Toulouse
description: >-
  Visual identity of DevFest Toulouse, the largest tech conference in the
  Toulouse area, organized by GDG Toulouse. Anchors two universes: Toulouse
  (terracotta brick, space, Occitan cross) and the global DevFest brand
  (Google palette, dev community).

colors:
  # --- Identity (Toulouse + complementary) ---
  bismarck:        "#B94420"   # warm dark accent, article author
  terracotta:      "#EC6839"   # identity — "Toulouse" wordmark, H1 accent, CTA hover
  incarnadin:      "#F4A598"   # warm light accent
  malachite:       "#109E6E"   # identity — "DevFest" wordmark, footer, accented headings
  emerald:         "#41B38E"   # accent green — historical Platinum tier color, still in palette
  mint:            "#8BCBB7"   # light green accent
  water:           "#C0E1D7"   # very light green surface

  # --- Secondary palette ---
  blue:            "#507BBD"   # primary CTA background
  sky:             "#63C6F2"   # light blue accent
  sky-soft:        "#C4E6F1"   # very light blue surface
  google-green:    "#31A853"
  google-green-2:  "#72BA69"
  google-green-3:  "#CDE3C0"
  google-orange:   "#F8AB06"
  red:             "#E84336"   # errors, alerts

  # --- Sponsor tier colors (DevFest Toulouse 2026 — 4-pack model) ---
  # Source: Dossier_Sponsoring_2026.pdf. Banner color is FIXED per tier;
  # banners are always uppercase white text on the tier color.
  tier-platinum:        "#109E6E"   # Platinum (4 max, 8 000 € HT, 12 m²) — Malachite
  tier-platinum-soft:   "#C0E1D7"
  tier-gold:            "#FFAB40"   # Gold (20 max, 4 000 € HT, 6 m²) — warm orange
  tier-gold-soft:       "#FFE0B8"
  tier-discovery:       "#7E60C9"   # Discovery (8 max, 1 200 € HT, 2 m² corner) — saturated purple
  tier-discovery-soft:  "#D5C7ED"
  tier-soutien:         "#CCCCCC"   # Soutien (∞, 500 € HT, no stand) — neutral light gray
  tier-soutien-soft:    "#E5E5E5"

  # --- Neutrals ---
  ink:             "#1D1D1B"   # body text, headings
  gray:            "#777776"   # nav text
  gray-light:      "#8E8E8D"   # secondary text (dates, mentions)
  gray-placeholder:"#808080"   # tertiary text (sponsor baselines)
  white:           "#FFFFFF"
  off-white:       "#FDF0EB"   # footer link text

  # --- Semantic roles ---
  primary:         "{colors.blue}"
  on-primary:      "{colors.white}"
  secondary:       "{colors.terracotta}"
  on-secondary:    "{colors.white}"
  tertiary:        "{colors.malachite}"
  on-tertiary:     "{colors.white}"
  surface:         "{colors.white}"
  on-surface:      "{colors.ink}"
  surface-muted:   "{colors.off-white}"
  error:           "{colors.red}"
  on-error:        "{colors.white}"
  link:            "{colors.bismarck}"
  link-on-dark:    "{colors.off-white}"

typography:
  # Google Sans (formerly Product Sans), released under SIL OFL in November
  # 2025. https://fonts.google.com/specimen/Google+Sans
  # Weights bundled / loaded: 400 (Regular), 500 (Medium), 700 (Bold), each
  # with an italic. Default loading is via Google Fonts CDN; .ttf files in
  # /assets/fonts/ enable self-hosted fallback (see /tokens/colors_and_type.css).
  display:
    fontFamily: "Google Sans"
    fontSize: 112px
    fontWeight: 700
    lineHeight: 1.0
  heading-1:
    fontFamily: "Google Sans"
    fontSize: 64px
    fontWeight: 700
    lineHeight: 1.2
  heading-2:
    fontFamily: "Google Sans"
    fontSize: 48px
    fontWeight: 700
    lineHeight: 1.2
  heading-3:
    fontFamily: "Google Sans"
    fontSize: 40px
    fontWeight: 700
    lineHeight: 1.2
  heading-4:
    fontFamily: "Google Sans"
    fontSize: 36px
    fontWeight: 700
    lineHeight: 1.2
  description:
    fontFamily: "Google Sans"
    fontSize: 32px
    fontWeight: 400
    lineHeight: 1.4
  description-bold:
    fontFamily: "Google Sans"
    fontSize: 32px
    fontWeight: 700
    lineHeight: 1.4
  card-title-l:
    fontFamily: "Google Sans"
    fontSize: 40px
    fontWeight: 700
    lineHeight: 1.2
  card-title-m:
    fontFamily: "Google Sans"
    fontSize: 32px
    fontWeight: 700
    lineHeight: 1.2
  card-title-s:
    fontFamily: "Google Sans"
    fontSize: 24px
    fontWeight: 700
    lineHeight: 1.1
  stat-value:
    fontFamily: "Google Sans"
    fontSize: 64px
    fontWeight: 700
    lineHeight: 1.4
  stat-label:
    fontFamily: "Google Sans"
    fontSize: 24px
    fontWeight: 400
    lineHeight: 1.2
  body:
    fontFamily: "Google Sans"
    fontSize: 16px
    fontWeight: 400
    lineHeight: 1.6
  body-medium:
    fontFamily: "Google Sans"
    fontSize: 16px
    fontWeight: 500
    lineHeight: 1.6
  body-bold:
    fontFamily: "Google Sans"
    fontSize: 16px
    fontWeight: 700
    lineHeight: 1.0
  caption:
    fontFamily: "Google Sans"
    fontSize: 12px
    fontWeight: 700
    lineHeight: 1.2
  small:
    fontFamily: "Google Sans"
    fontSize: 10px
    fontWeight: 400
    lineHeight: 1.2

spacing:
  xs:  4px
  s:   8px
  m:   12px
  l:   16px
  xl:  24px
  2xl: 32px
  3xl: 48px
  4xl: 64px
  5xl: 80px

rounded:
  s:    12px
  m:    16px
  l:    18px
  xl:   20px
  2xl:  24px
  3xl:  32px
  4xl:  40px
  5xl:  56px
  hero: 64px

components:
  # --- Buttons ---
  button-primary:
    backgroundColor: "{colors.primary}"
    textColor:       "{colors.on-primary}"
    typography:      "{typography.body-bold}"
    rounded:         "{rounded.s}"
    padding:         "12px 18px"
  button-primary-hover:
    backgroundColor: "{colors.secondary}"
    textColor:       "{colors.on-secondary}"
  button-primary-large:
    backgroundColor: "{colors.primary}"
    textColor:       "{colors.on-primary}"
    typography:      "{typography.stat-label}"
    rounded:         "{rounded.l}"
    padding:         "20px 32px"
  button-secondary:
    backgroundColor: "{colors.surface}"
    textColor:       "{colors.primary}"
    typography:      "{typography.body-bold}"
    rounded:         "{rounded.s}"
    padding:         "12px 18px"
  button-secondary-large:
    backgroundColor: "{colors.surface}"
    textColor:       "{colors.primary}"
    typography:      "{typography.stat-label}"
    rounded:         "{rounded.l}"
    padding:         "20px 32px"

  # --- Cards ---
  card-article:
    backgroundColor: "{colors.surface}"
    textColor:       "{colors.on-surface}"
    rounded:         "{rounded.3xl}"
    width:           300px
    height:          400px
  card-sponsor-platinum:
    backgroundColor: "{colors.surface}"
    textColor:       "{colors.on-surface}"
    rounded:         "{rounded.m}"
    width:           340px
    height:          481px
  card-sponsor-gold:
    backgroundColor: "{colors.surface}"
    textColor:       "{colors.on-surface}"
    rounded:         "{rounded.m}"
    width:           340px
    height:          240px
  card-sponsor-discovery:
    backgroundColor: "{colors.surface}"
    textColor:       "{colors.on-surface}"
    rounded:         "{rounded.m}"
    width:           340px
    height:          240px
  card-sponsor-soutien:
    backgroundColor: "{colors.surface}"
    textColor:       "{colors.on-surface}"
    rounded:         "{rounded.m}"
    width:           340px
    height:          120px

  # --- Layout ---
  header:
    backgroundColor: "{colors.surface}"
    textColor:       "{colors.gray}"
    height:          60px
  footer:
    backgroundColor: "{colors.tertiary}"
    textColor:       "{colors.on-tertiary}"
    rounded:         "{rounded.3xl}"
  stat-block:
    backgroundColor: "{colors.surface}"
    textColor:       "{colors.on-surface}"
    rounded:         "{rounded.xl}"
    width:           298px
    height:          192px
---

# DevFest Toulouse — Design System

## Overview

DevFest Toulouse is the largest tech conference in the Toulouse area, organized by GDG Toulouse and held annually since 2016. The visual identity weaves two threads:

- **Toulouse** — terracotta brick (the city's signature material), the space industry (floating letters, pixel "stars"), the Occitan cross, the dome of La Grave, the violet.
- **Global DevFest** — the official DevFest chevron mark `<>`, Google's palette, a developer-community feel that is friendly, local, and never corporate.

Tone: **community-driven** ("by devs, for devs"), **local** (chocolatines, La Grave, croix occitane), **convivial** ("Bug-free since 2016"), **bilingual** (FR default, EN alternate).

## Colors

The palette is built around two identity colors and their semantic roles.

- **Terracotta `#EC6839`** carries the "Toulouse" wordmark and the warmth of the city's brick. Use it for identity moments, accents, and CTA hover states.
- **Malachite `#109E6E`** carries the "DevFest" wordmark and the footer. Use it as the calm anchor of a page and for accented headings.
- **Blue `#507BBD`** is the **primary CTA color** — buttons that drive action ("Become a partner", "Submit a talk"). It is *not* an identity color; it is a functional one.
- Neutrals: ink `#1D1D1B` for body text, off-white `#FDF0EB` for muted text on the green footer.

### Sponsor tiers (DevFest Toulouse 2026 — 4-pack model)

Source: `Dossier_Sponsoring_2026.pdf` (held by the organizing team). Four packs, each with a fixed banner color. Banners are **uppercase white labels on the tier color**.

| Pack | Token | Hex | Quota | Tarif | Stand |
|------|-------|-----|-------|-------|-------|
| **Platinum** | `tier-platinum` (= `malachite`) | `#109E6E` | 4 max | 8 000 € HT | 12 m² |
| **Gold** | `tier-gold` | `#FFAB40` | 20 max | 4 000 € HT | 6 m² |
| **Discovery** | `tier-discovery` | `#7E60C9` | 8 max | 1 200 € HT | 2 m² (corner) |
| **Soutien** | `tier-soutien` | `#CCCCCC` | ∞ | 500 € HT | none |

> **Discovery** is reserved for *new sponsors, startups, very small businesses, and associations* — not a generic "discount" tier. Communicate that in copy when introducing it.

Note that **Platinum re-uses the same hex as the Malachite identity color**. This is intentional: Platinum sponsors deserve the brand's calm anchor color. It does not violate the "Malachite = DevFest wordmark" rule because the banner is a contextual color band, not the wordmark.

Contrast: all text-on-surface and on-primary pairings target WCAG AA (4.5:1). Run `lint` before publishing changes.

## Typography

**Google Sans** (formerly Product Sans, released under SIL OFL in November 2025) is the single typeface. It carries the DevFest logo and every screen of the site.

- **Bold (700)** — headings, buttons, statistic numbers, names.
- **Medium (500)** — intermediate emphasis: in-line stress within a paragraph, secondary labels, button labels in dense areas.
- **Regular (400)** — body, descriptions, navigation, labels.
- **Italic (400, 500, or 700)** — sponsor baselines (Platinum tier only). Never use italic for emphasis in body copy — use Bold instead.

Loading: Google Fonts CDN by default. The `assets/fonts/` directory ships `.ttf` files (Regular, Italic, Medium, MediumItalic, Bold, BoldItalic) for self-hosted builds; the `@font-face` block in `tokens/colors_and_type.css` wires them up.

A secondary handwritten typeface, **CCSignLanguage**, is used *only* on print and social-media communications — never on the web.

## Layout

Reference width is **1440 px desktop**. Content sits in a 1240 px container with 100 px lateral padding. The mobile breakpoint set is to be defined as the responsive variants of the Figma file ship.

Spacing follows a 4-px-rooted scale (`xs` 4 → `5xl` 80). Compose paddings and gaps from these tokens; do not introduce magic numbers.

The page skeleton is invariant:

```
Header (60 px, fixed)
  └── Breadcrumb (all pages except home, top: 124 px, left: 100 px)
      └── Content
          └── Footer (~496 px, malachite background, rounded-3xl)
```

### Motion

A single timing function and a small set of durations cover every transition in the brand. No bounce, no spring.

| Token | Value | Use |
|-------|-------|-----|
| `ease-default` | `cubic-bezier(0.2, 0.6, 0.2, 1)` | Every transition / animation, no exception |
| `duration-fast` | `150ms` | Hover color shifts, button state changes |
| `duration-base` | `200ms` | Card lifts, footer link underlines, focus rings |
| `duration-slow` | `400ms` | Section reveals — only when justified by content density |

Honor `prefers-reduced-motion: reduce` at the consumer level (set durations to `0ms` in that media query). CSS variables are exported in [`tokens/colors_and_type.css`](tokens/colors_and_type.css).

## Elevation & Depth

Three shadow tokens cover every surface that needs to lift off the page:

| Token            | Value                                       | Use                                      |
|------------------|---------------------------------------------|------------------------------------------|
| `shadow-header`  | `0 4px 12px rgba(29,29,27,0.10)`            | Fixed header                             |
| `shadow-card`    | `0 12px 16px 4px rgba(29,29,27,0.14)`       | Article cards                            |
| `shadow-section` | `0 4px 64px 4px rgba(29,29,27,0.12)`        | Floating sections (stats, footer)        |

Shadows always cast in ink (`#1D1D1B`) at low alpha — never gray, never colored.

## Shapes

The brand is **roundedness-forward**. Rectangles with hard 0-radius corners feel off-brand; default to at least `rounded.s` (12 px) for any interactive element. The hero image carries the largest radius (`rounded.hero` 64 px) — it should always feel like a "soft window" cut into the page.

The Occitan cross and "DevFest" chevrons `<>` are the only geometric motifs allowed as decoration.

## Components

Components are typed at three sizes: **Small** (header, footer, dense areas), **Medium** (default), **Large** (hero CTAs, marquee statistics).

Variants of the same component (e.g. `button-primary` and `button-primary-hover`) are expressed as separate component entries with related key names, per the Stitch spec.

### Sponsor cards

The 4 sponsor tiers map to 4 component entries. By default, all banners are the **same size** — the tier is signaled by the banner color (see Colors § Sponsor tiers), not by the banner geometry.

When a section needs extra visual hierarchy between tiers (e.g. a single page that lists all 4 packs side by side), the banners may *opt in* to a decreasing size, expressing the hierarchy typographically:

| Tier | Banner label size | Banner padding |
|------|--------------------|----------------|
| Platinum | 36 px Bold | 8 px / 18 px |
| Gold | 26 px Bold | 6 px / 14 px |
| Discovery | 20 px Bold | 5 px / 12 px |
| Soutien | 16 px Bold | 4 px / 10 px |

Only deviate from the default uniform size when the visual gain is real (the same row mixes 4 tiers in a comparison context). Otherwise keep banners uniform across grids dedicated to a single tier.

For the full per-component spec (anatomy, states, do/don't), see [`components/`](components/).

## Do's and Don'ts

**Do**

- Use **terracotta** for the *Toulouse* word and **malachite** for *DevFest*. They are not interchangeable.
- Use **blue** as the action color. Identity colors do not drive CTAs.
- Keep the logo's protection zone clear; on photos, use a white semi-transparent container.
- Pair illustrations with their semantic color (Bismarck / Terracotta / Malachite); never recolor outside this set.
- Use Font Awesome (free tier) for functional icons; use the brand's hand-drawn illustration set for decoration.

**Don't**

- Don't deform, rotate, or recolor the logo.
- Don't put body text in italic Google Sans (italic is reserved for sponsor baselines).
- Don't use CCSignLanguage on the web — it lives on print and social only.
- Don't introduce a new color without adding it here first; ad-hoc hexes will be flagged by `lint`.
- Don't use 0-radius rectangles for interactive elements; use `rounded.s` minimum.
- Don't reuse a sponsor tier color outside its tier (e.g. Discovery purple as a generic accent). Sponsor tier colors are signals, not part of the general palette.
- Don't bounce or spring transitions. The brand uses a single easing curve — see Layout § Motion.
