# Partner Card — Medium (Gold & Discovery)

Token group: `components.card-sponsor-gold`, `components.card-sponsor-discovery` in [`../DESIGN.md`](../DESIGN.md).

This single component covers the **two medium-size sponsor tiers** of the 2026 model: **Gold** and **Discovery**. They share dimensions (340 × 240) and structure (banner + logo + name); only the banner color and the audience differ.

Platinum has its own file ([`card-partner-platinum.md`](card-partner-platinum.md)) because it has different dimensions and a baseline. Soutien has its own file ([`card-partner-soutien.md`](card-partner-soutien.md)) because it is smaller and logo-only.

## Anatomy

```
┌─────────────────────────────────────────┐  ← width 340, height 240
│ ████████████████████████████████████████│  ← top banner: 24 px, color per tier
├─────────────────────────────────────────┤
│                                         │
│       ┌──────────────────────┐          │
│       │                      │          │
│       │   Logo (200×150)     │          │  Logo: rounded.2xl (24)
│       │   contained          │          │
│       └──────────────────────┘          │
│                                         │
│         Sponsor Name                    │  Bold 32 px, centered
│                                         │
└─────────────────────────────────────────┘
```

> No baseline on this card. The baseline is a Platinum-tier signal.

## Tokens

| Property | Token | Value |
|----------|-------|-------|
| width | — | `340px` |
| height | — | `240px` |
| backgroundColor | `{colors.surface}` | `#FFFFFF` |
| textColor | `{colors.on-surface}` | `#1D1D1B` |
| rounded | `{rounded.m}` (top corners only) | `border-radius: 16px 16px 0 0` |
| boxShadow | `shadow-card` (see DESIGN.md § Elevation & Depth) | — |

### Banner color & label (per tier)

| Tier | Banner background | Banner label color | Quota | Tarif | Eligibility |
|------|-------------------|--------------------|-------|-------|-------------|
| **Gold** | `{colors.tier-gold}` `#FFAB40` | **Ink** `#1D1D1B` (white fails WCAG) | 20 max | 4 000 € HT | Open |
| **Discovery** | `{colors.tier-discovery}` `#7E60C9` | White `#FFFFFF` | 8 max | 1 200 € HT | **New sponsors, startups, very small businesses, non-profits only** |

Banner default size: 24 px tall, label `{typography.body-bold}` (16 px) — uniform across tiers in standalone grids.

When a layout intentionally compares all 4 tiers in one row (e.g. sponsoring page), the optional **decreasing-size** variant kicks in:

| Tier | Banner label size | Banner padding |
|------|-------------------|----------------|
| Gold | 26 px Bold | 6 px / 14 px |
| Discovery | 20 px Bold | 5 px / 12 px |

> ⚠️ For Gold the banner label must be **ink**, not white — the contrast of white-on-orange fails WCAG AA. This is the only sponsor banner exception to the white-label rule.

### Logo zone

| Property | Value |
|----------|-------|
| width | `200px` |
| height | `150px` |
| rounded | `{rounded.2xl}` (24 px) |
| object-fit | `contain` |

Logo files should be **horizontal**.

### Sponsor name

`{typography.card-title-m}` → Google Sans **Bold 32 px**, line-height 1.2, color `{colors.on-surface}`. Centered. Single line — long names are truncated with ellipsis.

## Layout

```
┌─ banner (24)
├─ space-l (16)
├─ logo (200×150, rounded-2xl)
├─ space-l (16)
├─ name
└─ end
```

## States

Same as `card-partner-platinum`:

| State | Visual |
|-------|--------|
| **Default** | as drawn |
| **Hover** | shadow deepens, translate `-2px`, transition `var(--duration-base) var(--ease-default)` (200 ms) |
| **Focus (keyboard)** | 3 px terracotta outline, offset 4 px |
| **Logo missing** | gray placeholder with Font Awesome `fa-image` |

## Do / Don't

✅ **Do**

- Lay out cards in a 4-column grid on desktop (`gap: space-3xl` 48 px), within their tier section.
- Group cards by tier with a section heading per tier ("Partenaires Gold", "Partenaires Discovery").
- For Discovery, **always include a one-line eligibility hint** in the section heading or directly above the grid (e.g. *« Nouveaux partenaires, startups, TPE et associations »*). It avoids confusion with a "discount" tier.
- For Gold, write the banner label "GOLD" in **ink** (`#1D1D1B`); for Discovery, write "DISCOVERY" in white.

❌ **Don't**

- Don't put a Gold sponsor under the Discovery purple banner (or vice versa). The banner color is the tier signal; mismatching is a category error.
- Don't add a baseline. Baseline is reserved for Platinum.
- Don't change the card height to fit a logo. Resize the logo to fit the 200×150 zone.
- Don't add hover content (e.g. revealing a CTA). The whole card is the link to detail.
- Don't write "DISCOVERY" in ink — the contrast on `#7E60C9` is fine in white (5.4:1) and using ink would muddy the tier signal.
- Don't reuse the Discovery purple `#7E60C9` outside its tier (e.g. as a generic accent). Sponsor tier colors are signals, not a general palette.

## Reference HTML

```html
<!-- Gold sponsor -->
<a href="/partenaire/acme" class="dft-card-sponsor dft-card-sponsor--gold">
  <span class="dft-card-sponsor__banner" aria-hidden="true">GOLD</span>
  <div class="dft-card-sponsor__logo">
    <img src="/uploads/sponsors/acme-logo.svg" alt="Acme" loading="lazy">
  </div>
  <h3 class="dft-card-sponsor__name">Acme</h3>
</a>

<!-- Discovery sponsor -->
<a href="/partenaire/contoso" class="dft-card-sponsor dft-card-sponsor--discovery">
  <span class="dft-card-sponsor__banner" aria-hidden="true">DISCOVERY</span>
  <div class="dft-card-sponsor__logo">
    <img src="/uploads/sponsors/contoso-logo.svg" alt="Contoso" loading="lazy">
  </div>
  <h3 class="dft-card-sponsor__name">Contoso</h3>
</a>
```

## Reference CSS (banner color modifier)

```css
.dft-card-sponsor--gold      .dft-card-sponsor__banner {
  background: var(--tier-gold);       /* #FFAB40 */
  color: var(--ink);                  /* WCAG: white fails on this orange */
}
.dft-card-sponsor--discovery .dft-card-sponsor__banner {
  background: var(--tier-discovery);  /* #7E60C9 */
  color: var(--white);
}
```

## Accessibility

- Whole card is one `<a>`.
- Banner color carries no semantic info on its own (the tier is announced by the section heading); the banner span carries `aria-hidden` if the visible label duplicates the section heading, otherwise leave it readable.
- Logo `<img>` has the sponsor name as `alt`.
- Hover and focus styles match (keyboard parity).
