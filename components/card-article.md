# Article Card

Token group: `components.card-article` in [`../DESIGN.md`](../DESIGN.md).

The Article Card is the unit of the news grid. It is **the only card** in the brand that has a thumbnail above the text — sponsor cards are logo-only, speaker cards are photo-on-top. Keeping these distinct helps users scan a page without reading.

## Anatomy

```
┌─────────────────────────────────┐  ← width 300, height 400, radius 32
│  ┌───────────────────────────┐  │
│  │                           │  │  Thumbnail
│  │        IMAGE              │  │  280 × 210, radius 26
│  │                           │  │  10 px margin top/sides
│  └───────────────────────────┘  │
│                                 │
│  Article title spanning up      │  Title — Google Sans Bold 24, ink
│  to two lines, ellipsis on 3rd  │  max-width 260
│                                 │
│  by Author Name                 │  by + author, caption row
│  — — — — — — — — — — — —       │  hairline rule (#1D1D1B 10%)
│  29 Apr 2026          Lire →    │  small + body row, justified
└─────────────────────────────────┘
```

## Tokens

| Property | Token | Value |
|----------|-------|-------|
| backgroundColor | `{colors.surface}` | `#FFFFFF` |
| textColor | `{colors.on-surface}` | `#1D1D1B` |
| rounded | `{rounded.3xl}` | 32 px |
| width | — | `300px` |
| height | — | `400px` |
| boxShadow | `shadow-card` (see DESIGN.md § Elevation & Depth) | `0 12px 16px 4px rgba(29,29,27,0.14)` |

### Inner zones

| Zone | Token / value |
|------|---------------|
| Thumbnail | `width 280 × height 210`, `border-radius 26`, `margin 10` from card edges, `object-fit: cover` |
| Title | `{typography.card-title-s}` (Google Sans Bold 24, line-height 1.1), `max-width 260`, `margin: 16 auto` |
| Author "by" prefix | `{typography.small}` (Regular 10), `{colors.gray-light}` |
| Author name | `{typography.caption}` (Bold 12), `{colors.bismarck}` |
| Hairline | 1 px solid `rgba(29,29,27,0.10)`, full width inside card padding |
| Date | `{typography.small}` (Regular 10), `{colors.gray-light}` |
| "Lire" link | `{typography.body}` (Regular 16), `{colors.on-surface}`, letter-spacing `0.4px` |

## Layout

- Card uses **flex column** with three rows: thumbnail (fixed), main (title + author, fills), footer (date + Lire).
- Card padding: `10px` for the thumbnail offset, then `space-l` (16 px) horizontal for text.
- Bottom padding: `space-l` (16 px) above the date / Lire row.
- Hairline rule sits between author name and date row — it is `1 px solid rgba(29,29,27,0.10)`.

## Grid

The grid hosting Article Cards uses:

| Property | Value |
|----------|-------|
| Columns | 4 (desktop ≥ 1240 px), 2 (tablet 768-1239 px), 1 (mobile < 768 px) |
| Gap | `space-3xl` (48 px) |

Two rows of 4 = 8 articles per page (the home page surfaces 4; the news index surfaces 7-8).

## States

| State | Visual |
|-------|--------|
| **Default** | as drawn |
| **Hover** | shadow deepens slightly (`y: 16, blur: 24, alpha: 0.18`), card translates `-2 px` up, transition `var(--duration-base) var(--ease-default)` (200 ms) |
| **Focus (keyboard, whole card is a link)** | 3 px terracotta outline at card border, offset 4 px |
| **Visited** | no visual change (the brand chooses unread/read parity) |
| **Pressed** | shadow returns to default, `scale(0.99)` |

> The whole card is **one link** — no nested links inside. The "Lire" text is a visual cue, not a separate target.

## Variants

The Article Card has **one official size**. If a layout needs a smaller article surface, use a list row, not a shrunken card.

The card is **not** used for sessions or speakers — those have their own components (`card-session`, `card-speaker`, P2). Reusing the article card for those would muddle the brand's information hierarchy.

## Do / Don't

✅ **Do**

- Use a **landscape thumbnail** (4:3 or wider). The 280×210 zone is 4:3.
- Keep titles to **≤ 60 characters**; longer titles overflow and get truncated.
- Use **author's display name** with an accent color on the body author link (`{colors.bismarck}`).
- Wrap the entire card in `<a>` for a single-target click area.

❌ **Don't**

- Don't put a category badge or tag pill on the thumbnail. The grid is curated; categorization happens at the page level (e.g. "Actus 2026").
- Don't replace the thumbnail with a colored block. Articles always have an image (use a default illustration from `assets/illustrations/` if needed — Bismarck variant for the news section).
- Don't add a "Read more" CTA button below the card. The "Lire →" text inside the card is the affordance.
- Don't break the 300×400 ratio for desktop. The grid math depends on it.

## Reference HTML

```html
<a href="/actualite/devfest-toulouse-2026-est-en-route" class="dft-card-article">
  <img
    class="dft-card-article__thumb"
    src="/uploads/articles/devfest-2026-en-route.jpg"
    alt=""
    width="280" height="210"
    loading="lazy">

  <h3 class="dft-card-article__title">
    DevFest Toulouse 2026 est en route !
  </h3>

  <p class="dft-card-article__author">
    <span class="dft-card-article__by">by</span>
    <span class="dft-card-article__author-name">Julien Del Rio</span>
  </p>

  <hr class="dft-card-article__rule">

  <p class="dft-card-article__meta">
    <time datetime="2026-04-29">29 avril 2026</time>
    <span class="dft-card-article__cta">Lire →</span>
  </p>
</a>
```

## Reference CSS (sketch)

```css
.dft-card-article {
  display: flex;
  flex-direction: column;
  width: 300px;
  height: 400px;
  background: var(--dft-color-surface);
  color: var(--dft-color-on-surface);
  border-radius: 32px;
  box-shadow: var(--dft-shadow-card);
  text-decoration: none;
  padding: 10px 16px 16px;
  transition: transform var(--duration-base) var(--ease-default),
              box-shadow var(--duration-base) var(--ease-default);
}
.dft-card-article:hover {
  transform: translateY(-2px);
  box-shadow: 0 16px 24px 4px rgba(29,29,27,0.18);
}

.dft-card-article__thumb {
  width: 280px;
  height: 210px;
  border-radius: 26px;
  object-fit: cover;
  align-self: center;
}
.dft-card-article__title {
  font: 700 24px/1.1 "Google Sans", sans-serif;
  margin: 16px auto 0;
  max-width: 260px;
}
.dft-card-article__author {
  margin-top: auto;
  display: flex;
  gap: 4px;
  align-items: baseline;
}
.dft-card-article__by   { font: 400 10px/1.2 "Google Sans"; color: var(--dft-color-gray-light); }
.dft-card-article__author-name { font: 700 12px/1.2 "Google Sans"; color: var(--dft-color-bismarck); }

.dft-card-article__rule {
  border: 0;
  border-top: 1px solid rgba(29,29,27,0.10);
  margin: 12px 0;
  width: 100%;
}

.dft-card-article__meta {
  display: flex;
  justify-content: space-between;
  align-items: center;
}
.dft-card-article__meta time { font: 400 10px/1.2 "Google Sans"; color: var(--dft-color-gray-light); }
.dft-card-article__cta { font: 400 16px/1 "Google Sans"; letter-spacing: 0.4px; }
```

## Accessibility

- Card is a single `<a>` — keyboard users tab once to reach the whole card.
- Thumbnail uses `alt=""` (decorative); the title element (`<h3>`) supplies the accessible name.
- Date uses `<time datetime="…">` with ISO 8601 attribute for assistive tech and SEO.
- Hover/focus indicator: keep the **same** transform on hover and focus so keyboard users see the same affordance as mouse users.
