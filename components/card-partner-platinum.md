# Partner Card — Platinum

Token group: `components.card-sponsor-platinum` in [`../DESIGN.md`](../DESIGN.md).

The Platinum card is the largest sponsor surface. It exists because Platinum sponsors deserve more space than Gold/Silver — both vertically (room for a baseline) and visually (a saturated emerald banner on top).

There is **one Platinum card** size; do not introduce variants. The brand's clarity comes from the strict tier-to-component mapping.

## Anatomy

```
┌─────────────────────────────────────────┐  ← width 340, height 481
│ ████████████████████████████████████████│  ← top banner: 24 px, emerald
├─────────────────────────────────────────┤
│                                         │
│        ┌─────────────────────┐          │
│        │                     │          │
│        │     Logo (267×200)  │          │  Logo: rounded.2xl (24)
│        │     contained       │          │  background can be set
│        └─────────────────────┘          │
│                                         │
│        Sponsor Name                     │  Bold 40 px
│                                         │
│        Baseline en italique             │  Italic Regular 16 px gray
│                                         │
└─────────────────────────────────────────┘
   ↑ outer card: rounded-top.m (16) only on the top corners
   ↑ outer card: shadow-card
```

## Tokens

| Property | Token | Value |
|----------|-------|-------|
| width | — | `340px` |
| height | — | `481px` |
| backgroundColor | `{colors.surface}` | `#FFFFFF` |
| textColor | `{colors.on-surface}` | `#1D1D1B` |
| rounded | `{rounded.m}` (top corners only) | `border-radius: 16px 16px 0 0` (the bottom is implicitly cut by the parent grid) |
| boxShadow | `shadow-card` (see DESIGN.md § Elevation & Depth) | `0 12px 16px 4px rgba(29,29,27,0.14)` |

> ⚠️ **Top-corners-only radius.** The Platinum card sits at the top of a tier section; only the top corners are rounded. The card's bottom edge is straight, allowing it to sit flush against the page background. This contrasts with the Article Card which is rounded on all 4 corners.

### Banner

| Property | Token | Value |
|----------|-------|-------|
| height | — | `24px` |
| backgroundColor | `{colors.emerald}` | `#41B38E` |

The banner color is **fixed** to emerald for Platinum. It is the brand's sponsor-tier signal — never change it on a per-sponsor basis.

### Logo zone

| Property | Value |
|----------|-------|
| width | `267px` |
| height | `200px` |
| rounded | `{rounded.2xl}` (24 px) |
| backgroundColor | optional white surface; inherits transparency unless the logo needs contrast |
| object-fit | `contain` (never `cover`) |
| margin | centered horizontally; top offset `space-3xl` (48 px) below the banner |

### Sponsor name

`{typography.card-title-l}` → Google Sans **Bold 40 px**, line-height 1.2, color `{colors.on-surface}`. Centered.

### Baseline (Platinum only)

Google Sans **Italic Regular 16 px**, color `{colors.gray-placeholder}` (`#808080`), centered.

The Italic font weight is reserved for this exact use case.

## Layout

```
┌─ banner (24)
├─ space-3xl (48)
├─ logo (267×200, rounded-2xl)
├─ space-2xl (32)
├─ name
├─ space-l (16)
├─ baseline
├─ space-3xl (48)
└─ end
```

## States

| State | Visual |
|-------|--------|
| **Default** | as drawn |
| **Hover** (whole card is a link to sponsor detail) | shadow deepens (`y: 16, blur: 24, alpha: 0.18`), translate `-2px`, transition 160 ms |
| **Focus (keyboard)** | 3 px terracotta outline, offset 4 px |
| **Logo broken / missing** | placeholder logo block: gray fill `{colors.gray-light}` at 10 % opacity, centered Font Awesome `fa-image` icon |

## Do / Don't

✅ **Do**

- Use the sponsor's **horizontal logo** when available (the 267×200 zone is wider than tall).
- Pad the logo inside its 267×200 box with `object-fit: contain` so logos of different aspect ratios stay visually balanced.
- Write the baseline in **the sponsor's voice** but constrained to 1 line (≈ 60 chars).

❌ **Don't**

- Don't put a CTA on the card. Sponsor cards are entries to detail pages; the whole card is the link.
- Don't add a "Platinum" label on the card. The emerald banner *is* the label.
- Don't tilt or rotate the logo for design effect.
- Don't show the Platinum card without a baseline. If the sponsor hasn't provided one, ask them — Platinum tier requires it.

## Reference HTML

```html
<a href="/partenaire/acme" class="dft-card-platinum">
  <span class="dft-card-platinum__banner" aria-hidden="true"></span>
  <div class="dft-card-platinum__logo">
    <img src="/uploads/sponsors/acme-logo.svg" alt="Acme" loading="lazy">
  </div>
  <h3 class="dft-card-platinum__name">Acme Corporation</h3>
  <p class="dft-card-platinum__baseline">L'industrie au service du futur.</p>
</a>
```

## Accessibility

- The whole card is one `<a>` link.
- Banner is `aria-hidden` — its meaning ("Platinum") is communicated separately by the section heading ("Partenaires Platinum").
- Logo `<img>` has the sponsor name as `alt` (the `<h3>` then duplicates it for screen readers; this is acceptable for SEO and clarity — and many SR users navigate by headings).
- Hover shadow + translate is also applied on focus to give equivalent affordance to keyboard users.
