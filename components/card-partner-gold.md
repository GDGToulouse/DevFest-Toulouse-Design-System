# Partner Card — Gold / Silver / Other

Token group: `components.card-sponsor-gold` in [`../DESIGN.md`](../DESIGN.md).

The medium sponsor card is shared across **Gold, Silver, and other tiers** — the only thing that changes is the banner color. Keeping the geometry constant lets the brand communicate "all secondary tiers" with a single visual rhythm.

The Platinum tier uses [`card-partner-platinum.md`](card-partner-platinum.md) instead.

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

### Banner color (per tier)

| Tier | Token | Hex |
|------|-------|-----|
| **Gold** | `{colors.gold}` | `#FFD428` |
| **Silver** | `{colors.pink}` | `#EE7CAD` |
| **Other / community / media** | `{colors.pink}` | `#EE7CAD` |

> 🟡 **Yes, "Silver" is pink, not silver.** The brand chose a recognizable, named color over a literal metal — silver-grey would muddy with the neutrals. This is a deliberate choice; do not "fix" it.

### Logo zone

| Property | Value |
|----------|-------|
| width | `200px` |
| height | `150px` |
| rounded | `{rounded.2xl}` (24 px) |
| object-fit | `contain` |

The logo zone is smaller than Platinum (200×150 vs 267×200) because the card itself is shorter. Logo files should still be **horizontal**.

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
| **Hover** | shadow deepens, translate `-2px`, transition 160 ms |
| **Focus (keyboard)** | 3 px terracotta outline, offset 4 px |
| **Logo missing** | gray placeholder with Font Awesome `fa-image` |

## Do / Don't

✅ **Do**

- Lay out Gold cards in a 4-column grid on desktop (`gap: space-3xl` 48 px).
- Group cards by tier with a section heading per tier ("Partenaires Gold", "Partenaires Silver", etc.).
- Mix Silver and "other" partners under the same pink banner if the page is short — the visual signal is still consistent.

❌ **Don't**

- Don't put a Gold sponsor under a pink banner (or vice versa). The banner color is the tier signal; mismatching it is a category error.
- Don't add a baseline. Baseline is reserved for Platinum.
- Don't change the card height to fit a logo. Resize the logo to fit the 200×150 zone.
- Don't add hover content (e.g. revealing a CTA). The whole card is the link to detail.

## Reference HTML

```html
<!-- Gold sponsor -->
<a href="/partenaire/acme" class="dft-card-sponsor dft-card-sponsor--gold">
  <span class="dft-card-sponsor__banner" aria-hidden="true"></span>
  <div class="dft-card-sponsor__logo">
    <img src="/uploads/sponsors/acme-logo.svg" alt="Acme" loading="lazy">
  </div>
  <h3 class="dft-card-sponsor__name">Acme</h3>
</a>

<!-- Silver / other sponsor -->
<a href="/partenaire/contoso" class="dft-card-sponsor dft-card-sponsor--silver">
  <span class="dft-card-sponsor__banner" aria-hidden="true"></span>
  <div class="dft-card-sponsor__logo">
    <img src="/uploads/sponsors/contoso-logo.svg" alt="Contoso" loading="lazy">
  </div>
  <h3 class="dft-card-sponsor__name">Contoso</h3>
</a>
```

## Reference CSS (banner color modifier)

```css
.dft-card-sponsor--gold   .dft-card-sponsor__banner { background: var(--dft-color-gold); }   /* #FFD428 */
.dft-card-sponsor--silver .dft-card-sponsor__banner { background: var(--dft-color-pink); }   /* #EE7CAD */
.dft-card-sponsor--other  .dft-card-sponsor__banner { background: var(--dft-color-pink); }   /* #EE7CAD */
```

## Accessibility

- Whole card is one `<a>`.
- Banner color carries no semantic info (the tier is announced by the section heading); banner is `aria-hidden`.
- Logo `<img>` has the sponsor name as `alt`.
- Hover and focus styles match (keyboard parity).
