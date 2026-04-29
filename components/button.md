# Button

Token group: `components.button-primary`, `button-primary-large`, `button-primary-hover`, `button-secondary`, `button-secondary-large` in [`../DESIGN.md`](../DESIGN.md).

The button is the **action surface** of the brand. It is always blue (`{colors.primary}`) when filled — never an identity color. The terracotta and malachite identity colors live elsewhere (typography, sponsor bands, footer); putting them on a CTA breaks the action/identity separation.

## Anatomy

```
┌────────────────────────────────────┐
│   ↕ padding-y                      │
│ ↔   Label (Google Sans Bold)    ↔  │
│   ↕ padding-y                      │
└────────────────────────────────────┘
       ↑                       ↑
       └── radius (rounded.s or rounded.l)
```

A button is **always** label-only (no leading icon, no trailing arrow). For navigation affordances, use a plain link with a Font Awesome chevron — not a button.

## Variants

The button has **two axes** giving 4 official combinations:

| | Small (header, footer, dense) | Large (hero, page CTAs) |
|---|---|---|
| **Primary** (filled) | `button-primary` | `button-primary-large` |
| **Secondary** (outlined) | `button-secondary` | `button-secondary-large` |

### Primary, Small

| Property | Token | Value |
|----------|-------|-------|
| backgroundColor | `{colors.primary}` | `#507BBD` |
| textColor | `{colors.on-primary}` | `#FFFFFF` |
| typography | `{typography.body-bold}` | Google Sans Bold 16 px |
| rounded | `{rounded.s}` | 12 px |
| padding | — | `12px 18px` |

Use for: header CTAs, footer "Contactez nous", inline actions in dense layouts.

### Primary, Large

| Property | Token | Value |
|----------|-------|-------|
| backgroundColor | `{colors.primary}` | `#507BBD` |
| textColor | `{colors.on-primary}` | `#FFFFFF` |
| typography | `{typography.stat-label}` | Google Sans Bold 24 px |
| rounded | `{rounded.l}` | 18 px |
| padding | — | `20px 32px` |

Use for: hero CTAs ("Devenir partenaire"), page-level CTAs ("Proposer un talk").

> ⚠️ The Large variant uses **Bold 24 px** even though the typography token referenced (`stat-label`) is Regular 24 px in `DESIGN.md`. Buttons override `fontWeight` to `700`. This is intentional: stat-label is for stat label text, but the size scale is reused for buttons. A future cleanup could introduce a dedicated `button-label-l` typography token.

### Secondary, Small

| Property | Value |
|----------|-------|
| backgroundColor | `transparent` |
| border | `2px solid {colors.primary}` |
| textColor | `{colors.primary}` |
| typography | `{typography.body-bold}` |
| rounded | `{rounded.s}` |
| padding | `12px 18px` (offset for border) |

### Secondary, Large

| Property | Value |
|----------|-------|
| backgroundColor | `transparent` |
| border | `3px solid {colors.primary}` |
| textColor | `{colors.primary}` |
| typography | `{typography.stat-label}` (Bold 24 px) |
| rounded | `{rounded.l}` |
| padding | `20px 32px` |

## States

| State | Tokens | Visual |
|-------|--------|--------|
| **Default** | as above | — |
| **Hover** | `{button-primary-hover}` → backgroundColor `{colors.secondary}` (terracotta), keeps text white | Primary buttons warm to terracotta on hover. Secondary buttons fill with primary color, text turns white. |
| **Active / Pressed** | scale(0.98), no color change | Subtle press feedback |
| **Focus (keyboard)** | `outline: 3px solid {colors.terracotta}` with `outline-offset: 2px` | Visible ring, never `outline: none` without replacement |
| **Disabled** | opacity 0.5, `cursor: not-allowed`, no hover | Avoid disabled buttons when possible — prefer hiding the action |
| **Loading** | text replaced by inline spinner, button keeps width | Width-locked to prevent layout shift |

## Do / Don't

✅ **Do**

- Pair Primary and Secondary side-by-side when there are two equal-rank actions ("Devenir partenaire" Primary + "Proposer un talk" Secondary).
- Keep button labels in **infinitive or imperative**: "Devenir partenaire", "Contactez nous", "Proposer un talk".
- Limit to **one Primary** per visual region — multiple primaries dilute the action hierarchy.

❌ **Don't**

- Don't use **terracotta or malachite** as the button background. They are identity colors, not action colors.
- Don't introduce new sizes (XS, XL) — Small and Large cover every documented case.
- Don't right-align a CTA pair on desktop unless it is the hero (which left-aligns its CTA pair anchored to the bottom of the description block).
- Don't put body copy inside a button. If the action needs explanation, use surrounding paragraph + short button.

## Reference HTML

```html
<!-- Primary, Small -->
<button type="button" class="dft-button dft-button--primary dft-button--small">
  Contactez nous
</button>

<!-- Primary, Large -->
<button type="button" class="dft-button dft-button--primary dft-button--large">
  Devenir partenaire
</button>

<!-- Secondary, Large -->
<button type="button" class="dft-button dft-button--secondary dft-button--large">
  Proposer un talk
</button>
```

## Reference CSS (CSS variables draft)

```css
.dft-button {
  font-family: "Google Sans", sans-serif;
  font-weight: 700;
  cursor: pointer;
  transition: background-color var(--duration-fast) var(--ease-default),
              color            var(--duration-fast) var(--ease-default),
              transform        var(--duration-fast) var(--ease-default);
  border: 0;
  display: inline-flex;
  align-items: center;
  justify-content: center;
}

.dft-button--small  { font-size: 16px; padding: 12px 18px; border-radius: 12px; }
.dft-button--large  { font-size: 24px; padding: 20px 32px; border-radius: 18px; }

.dft-button--primary {
  background-color: var(--dft-color-primary);   /* #507BBD */
  color: var(--dft-color-on-primary);           /* #FFFFFF */
}
.dft-button--primary:hover {
  background-color: var(--dft-color-secondary); /* #EC6839 terracotta */
}

.dft-button--secondary {
  background-color: transparent;
  color: var(--dft-color-primary);
  border: 2px solid var(--dft-color-primary);
}
.dft-button--secondary.dft-button--large { border-width: 3px; }
.dft-button--secondary:hover {
  background-color: var(--dft-color-primary);
  color: var(--dft-color-on-primary);
}

.dft-button:active { transform: scale(0.98); }

.dft-button:focus-visible {
  outline: 3px solid var(--dft-color-secondary);
  outline-offset: 2px;
}

.dft-button:disabled {
  opacity: 0.5;
  cursor: not-allowed;
}
```
