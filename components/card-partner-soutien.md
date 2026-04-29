# Partner Card — Soutien

Token group: `components.card-sponsor-soutien` in [`../DESIGN.md`](../DESIGN.md).

The Soutien card is the **smallest and most modest** sponsor surface, dedicated to the *Soutien* pack of the 2026 sponsoring model. Soutien sponsors do not have a stand; their pack is purely about **visibility**. The card reflects that: smaller than Gold/Discovery, no name typography by default, logo-forward.

The pack has **no quota** — any number of Soutien sponsors can co-exist. The grid must therefore degrade gracefully from a few logos to several dozen.

## Anatomy

```
┌─────────────────────────────────────────┐  ← width 340, height 120
│ ████████████████████████████████████████│  ← top banner: 24 px, gray
├─────────────────────────────────────────┤
│                                         │
│       ┌──────────────────────┐          │
│       │                      │          │
│       │   Logo (200×60)      │          │  Logo: rounded.s (12)
│       │   contained          │          │
│       └──────────────────────┘          │
│                                         │
└─────────────────────────────────────────┘
```

The sponsor's name is **not displayed** on the default Soutien card. It appears as the logo's `alt` text and on hover (tooltip). This keeps the visual rhythm calm when the page lists 30+ Soutien sponsors.

## Tokens

| Property | Token | Value |
|----------|-------|-------|
| width | — | `340px` |
| height | — | `120px` |
| backgroundColor | `{colors.surface}` | `#FFFFFF` |
| textColor | `{colors.on-surface}` | `#1D1D1B` |
| rounded | `{rounded.m}` (top corners only) | `border-radius: 16px 16px 0 0` |
| boxShadow | `shadow-card` | — |

### Banner

| Property | Value |
|----------|-------|
| height | `24px` |
| backgroundColor | `{colors.tier-soutien}` `#CCCCCC` |
| label color | **Ink** `#1D1D1B` (white fails WCAG on this gray) |
| label typography | `{typography.body-bold}` 16 px Bold (or 16 px Bold for the optional decreasing-size variant) |

### Logo zone

| Property | Value |
|----------|-------|
| width | `200px` |
| height | `60px` (smaller than Gold/Discovery's 150 px) |
| rounded | `{rounded.s}` (12 px) |
| object-fit | `contain` |

A wider, shorter logo zone fits modest sponsors that often only have a horizontal logo to share.

## Layout

```
┌─ banner (24)
├─ space-l (16)
├─ logo (200×60, rounded-s)
├─ space-l (16)
└─ end
```

The grid is more permissive than Gold/Discovery: **4 to 6 columns** on desktop depending on the count, `gap: space-l` (16 px) — denser to fit larger lists.

## States

| State | Visual |
|-------|--------|
| **Default** | as drawn |
| **Hover** | shadow deepens, translate `-2px`, transition `var(--duration-base) var(--ease-default)` (200 ms); a small label "Sponsor Name" appears in a tooltip below the card |
| **Focus (keyboard)** | 3 px terracotta outline, offset 4 px |
| **Logo missing** | gray placeholder with Font Awesome `fa-image` |

## Do / Don't

✅ **Do**

- Group all Soutien cards in a single section *« Sponsors Soutien »* with a one-line description of the pack ("Sans stand, focus visibilité.").
- Use a denser grid (4–6 columns) — Soutien sponsors can be numerous, and visual rhythm is more important than per-card prominence.
- Sort Soutien logos alphabetically — there is no other ranking signal.

❌ **Don't**

- Don't show a sponsor name typography by default. The logo carries the name (with `alt` and tooltip).
- Don't try to elevate one Soutien sponsor over the others (no "featured" variant). The pack is intentionally egalitarian.
- Don't put a Soutien card alongside Gold/Discovery cards in the same row. Soutien lives in its own grid below the others.
- Don't write "SOUTIEN" in white — it fails WCAG AA on the light gray (`#CCCCCC`). Use ink.

## Reference HTML

```html
<a href="/partenaire/community-fund" class="dft-card-sponsor dft-card-sponsor--soutien">
  <span class="dft-card-sponsor__banner" aria-hidden="true">SOUTIEN</span>
  <div class="dft-card-sponsor__logo">
    <img src="/uploads/sponsors/community-fund-logo.svg" alt="Community Fund" loading="lazy">
  </div>
</a>
```

## Reference CSS

```css
.dft-card-sponsor--soutien .dft-card-sponsor__banner {
  background: var(--tier-soutien);  /* #CCCCCC */
  color: var(--ink);                /* WCAG: white fails on this gray */
}
.dft-card-sponsor--soutien {
  width: 340px;
  height: 120px;
}
.dft-card-sponsor--soutien .dft-card-sponsor__logo img {
  width: 200px;
  height: 60px;
  border-radius: 12px;
  object-fit: contain;
}
```

## Accessibility

- The card is a single `<a>`; the logo `<img>` carries the sponsor name as `alt`.
- The banner label is decorative (`aria-hidden="true"`) — the section heading "Sponsors Soutien" already announces the tier.
- Tooltip with the sponsor name on hover/focus must also be **announced to screen readers** (`aria-describedby` pointing at a hidden text node, or a `<title>` on the `<a>`).
