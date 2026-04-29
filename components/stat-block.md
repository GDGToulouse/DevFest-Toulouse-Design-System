# Statistics Block

A floating white encart used on the home page to surface 4 numerical highlights of the event ("1 day", "1500 participants", "40 talks", "30 partners"). It carries the **only** mixed-color title in the brand: an inline composition of malachite + terracotta words.

## Anatomy

```
┌────────────────────────────────────────────────────────────────────────┐
│                                                                        │
│         L'événement tech Toulousain                                    │
│                                                                        │
│                                                                        │
│   ┌──────────────┐   ┌──────────────┐   ┌──────────────┐   ┌─────────┐ │
│   │ 📅 calendar  │   │ 👥 users     │   │ 🎤 mic       │   │ 🤝 hand │ │
│   │              │   │              │   │              │   │         │ │
│   │     1        │   │   1500       │   │     40       │   │   30    │ │
│   │              │   │              │   │              │   │         │ │
│   │   Journée    │   │ Participants │   │ Conférences  │   │ Stands  │ │
│   └──────────────┘   └──────────────┘   └──────────────┘   └─────────┘ │
│                                                                        │
│  [La Grave illustration in bottom-left, 30 % opacity, tucks behind]    │
│                                                                        │
└────────────────────────────────────────────────────────────────────────┘
   ↑ outer encart: surface, rounded.4xl (40), shadow-section, padding 64
```

## Tokens

### Outer encart

| Property | Token | Value |
|----------|-------|-------|
| backgroundColor | `{colors.surface}` | `#FFFFFF` |
| textColor | `{colors.on-surface}` | `#1D1D1B` |
| rounded | `{rounded.4xl}` | 40 px |
| boxShadow | `shadow-section` (see DESIGN.md § Elevation & Depth) | `0 4px 64px 4px rgba(29,29,27,0.12)` |
| padding | `{spacing.4xl}` | 64 px (top/bottom), 100 px (lateral) |

### Title

The title is a mixed-color composition:

| Word | Color | Weight |
|------|-------|--------|
| "L'événement" | `{colors.on-surface}` ink | Regular (`{typography.heading-2}` Bold weight is overridden to 400) |
| "tech" | `{colors.tertiary}` malachite | Bold |
| "Toulousain" | `{colors.secondary}` terracotta | Bold |

Use `{typography.heading-2}` (48 px) as the size base, with per-word weight overrides.

### Stat block (4 of them, in a row)

| Property | Token | Value |
|----------|-------|-------|
| backgroundColor | `{colors.surface}` | inherits or stays white |
| rounded | `{rounded.xl}` | 20 px |
| width | — | 298 px |
| height | — | 192 px |
| Icon size | — | 48 px (Font Awesome, brand color) |
| Icon color | `{colors.bismarck}` | `#B94420` |
| Value typography | `{typography.stat-value}` | Google Sans Bold 64 px |
| Value color | `{colors.on-surface}` | `#1D1D1B` |
| Label typography | `{typography.stat-label}` | Google Sans Regular 24 px |
| Label color | `{colors.gray}` | `#777776` |

### Icon set

Font Awesome (free tier), one icon per block:

| Stat | Font Awesome class |
|------|---------------------|
| Journée(s) | `fa-calendar-days` |
| Participants | `fa-users` |
| Conférences | `fa-microphone` |
| Stands / partenaires | `fa-handshake` |

## Layout

- The 4 stat blocks sit in a row with `display: flex; gap: space-2xl (32 px); justify-content: space-between;`.
- The row is centered horizontally inside the encart.
- The **La Grave illustration** (`assets/illustrations/Bismarck/LaGraveIlluDevFest.png`) sits in the **bottom-left** of the encart, ~30 % opacity, partially clipped by the encart's rounded corner. It is decorative.
- Below ≤ 768 px, the row collapses to a 2×2 grid.

## States

The block is decorative; only the optional "see all stats" link below (when present) interacts.

| State | Visual |
|-------|--------|
| Block hover | none — these are display blocks, not links |
| Numeric tick (animation, optional) | count from 0 to value over 1 s when entering viewport, ease-out, run once |

## Do / Don't

✅ **Do**

- Use **exactly 4 stats**. Three feels weak; five overflows the row width.
- Use **whole, round numbers** — "1500", not "1487". Stats are emotional, not exact.
- Pair each stat with an icon from the table above. Don't substitute icons.

❌ **Don't**

- Don't add a CTA inside the encart. The encart is *informational closure* — the CTA belongs in the section before or after.
- Don't recolor the value digits. They are always ink black.
- Don't replace the La Grave illustration with another monument. La Grave is the home-page signature; if a different page needs a stat block, drop the illustration entirely rather than swap it.
- Don't make the stat blocks clickable; if a "Voir les stats détaillées" affordance is needed, place a Secondary Small button below the row, outside the encart.

## Reference HTML

```html
<section class="dft-stats" aria-labelledby="stats-title">
  <h2 id="stats-title" class="dft-stats__title">
    <span class="dft-stats__title-base">L'événement</span>
    <span class="dft-stats__title-tech">tech</span>
    <span class="dft-stats__title-tls">Toulousain</span>
  </h2>

  <ul class="dft-stats__row" role="list">
    <li class="dft-stats__block">
      <i class="fa-solid fa-calendar-days" aria-hidden="true"></i>
      <span class="dft-stats__value">1</span>
      <span class="dft-stats__label">Journée</span>
    </li>
    <li class="dft-stats__block">
      <i class="fa-solid fa-users" aria-hidden="true"></i>
      <span class="dft-stats__value">1500</span>
      <span class="dft-stats__label">Participants</span>
    </li>
    <li class="dft-stats__block">
      <i class="fa-solid fa-microphone" aria-hidden="true"></i>
      <span class="dft-stats__value">40</span>
      <span class="dft-stats__label">Conférences</span>
    </li>
    <li class="dft-stats__block">
      <i class="fa-solid fa-handshake" aria-hidden="true"></i>
      <span class="dft-stats__value">30</span>
      <span class="dft-stats__label">Stands</span>
    </li>
  </ul>

  <img
    src="/assets/illustrations/Bismarck/LaGraveIlluDevFest.png"
    alt=""
    class="dft-stats__illustration">
</section>
```

## Accessibility

- Each stat is a `<li>` for assistive tech to announce the count ("list of 4 items").
- The icon is `aria-hidden`; the value + label provide the spoken information.
- If the count-up animation is enabled, respect `prefers-reduced-motion: reduce` and snap directly to the final value.
