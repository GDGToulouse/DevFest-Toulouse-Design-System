# Header

Token group: `components.header` in [`../DESIGN.md`](../DESIGN.md).

The header is **persistent across every page** of the site. It is the only horizontal surface that crosses the entire viewport. Keep it light, light, light: white background, single ink color, no decorative illustrations.

## Anatomy

```
┌──────────────────────────────────────────────────────────────────────────────────┐
│  [Logo 48×48]  Programme  Speakers  Partenaires  Actus     [in][▶][𝕏][bs]  [Btn][Btn]│
└──────────────────────────────────────────────────────────────────────────────────┘
                                                              ↑              ↑
   ← left cluster (logo + nav) →                              social icons   2 CTAs (Small)
                                              ←        right cluster        →
```

| Slot | Content | Width |
|------|---------|-------|
| **Logo** | Minimal logo (avatar 48×48 px), see [`../brand/logo.md`](../brand/logo.md) | 48 px |
| **Nav** | 4 text links: Programme, Speakers, Partenaires, Actus | flexible |
| **Socials** | 4 icons (LinkedIn, YouTube, X, Bluesky), 24 px each | ~120 px |
| **CTAs** | 2 Small buttons: 1 Primary + 1 Secondary | ~280 px |

> The 4 nav links are **fixed** (`Programme`, `Speakers`, `Partenaires`, `Actus`). Adding a fifth requires re-thinking the layout — do not just shoehorn it in.

## Tokens

| Property | Token | Value |
|----------|-------|-------|
| backgroundColor | `{colors.surface}` | `#FFFFFF` |
| textColor (nav) | `{colors.gray}` | `#777776` |
| textColor (logo area) | `{colors.on-surface}` | `#1D1D1B` |
| height | — | `60px` |
| boxShadow | `shadow-header` (see DESIGN.md § Elevation & Depth) | `0 4px 12px rgba(29,29,27,0.10)` |
| nav typography | `{typography.body}` | Google Sans Regular 16 px, letter-spacing `0.4px` |

## Layout

- Total height: **60 px** (fixed).
- Position: `position: sticky; top: 0; z-index: 100;` — stays on screen during scroll.
- Lateral padding: matches the page (`100 px` desktop), reduce to `24px` ≤ 768 px.
- Vertical centering: the 60 px row is a flex container with `align-items: center; justify-content: space-between;`.
- Nav gap: `space-l` (16 px) between links.
- Socials gap: `space-m` (12 px) between icons.
- CTA pair gap: `space-m` (12 px).

## Responsive

> ⚠️ Mobile mockups are **not yet finalized in Figma**. The pattern below is a defensible default until the official mobile maquette arrives.

| Breakpoint | Behavior |
|------------|----------|
| ≥ 1024 px (desktop) | Full layout as drawn |
| 768–1023 px | Hide socials cluster, keep nav + CTAs |
| < 768 px (mobile) | Replace nav + socials + CTAs with a hamburger button (right) revealing a full-screen drawer; logo stays left |

## States

| State | Tokens | Visual |
|-------|--------|--------|
| **Default** | white surface | — |
| **On scroll** | unchanged | shadow already accounts for separation; do not deepen on scroll |
| **Active nav link** | `{colors.terracotta}` text + 2 px underline `{colors.terracotta}` | The page the user is currently on |
| **Hover nav link** | `{colors.on-surface}` (`#1D1D1B`) | Darken from gray to ink |
| **Focus nav link** | 2 px terracotta outline (keyboard nav) | Always keep keyboard ring |

## Do / Don't

✅ **Do**

- Use the **minimal logo** (Avatar 400×400 PNG or `LOGO_DevFest_Secondaire_*.svg`) — never the full wordmark, the header is too short.
- Keep the 4 nav labels in **camelCase-free single words** ("Programme", not "Le programme").
- Honor the social icon order on every screen: LinkedIn → YouTube → X → Bluesky.

❌ **Don't**

- Don't put the full DevFest+Toulouse wordmark in a 60 px row — it crashes the typography.
- Don't add a search bar or an account dropdown to the header without re-designing it (the slot space is gone).
- Don't deepen the shadow on scroll. The default `shadow-header` is enough; layered shadows make it look "stickier" than the rest of the page.
- Don't change nav text color on a per-page basis (e.g. inverting on a dark hero) — keep it consistent; the hero overlap is small.

## Reference HTML

```html
<header class="dft-header">
  <a href="/" class="dft-header__logo" aria-label="Accueil DevFest Toulouse">
    <img src="/assets/logo/Avatar_400x400px.png" alt="" width="48" height="48">
  </a>

  <nav class="dft-header__nav" aria-label="Navigation principale">
    <a href="/programme">Programme</a>
    <a href="/speakers">Speakers</a>
    <a href="/partenaires">Partenaires</a>
    <a href="/actualites" aria-current="page">Actus</a>
  </nav>

  <div class="dft-header__socials">
    <a href="…" aria-label="LinkedIn"><i class="fa-brands fa-linkedin"></i></a>
    <a href="…" aria-label="YouTube"><i class="fa-brands fa-youtube"></i></a>
    <a href="…" aria-label="X"><i class="fa-brands fa-x-twitter"></i></a>
    <a href="…" aria-label="Bluesky"><i class="fa-brands fa-bluesky"></i></a>
  </div>

  <div class="dft-header__cta">
    <button class="dft-button dft-button--secondary dft-button--small">Proposer un talk</button>
    <button class="dft-button dft-button--primary   dft-button--small">Devenir partenaire</button>
  </div>
</header>
```

## Accessibility

- Use `<header>` (semantic landmark) and `<nav aria-label="Navigation principale">`.
- The logo is wrapped in a link to `/` with `aria-label="Accueil DevFest Toulouse"` (the image has `alt=""` since the surrounding link supplies the name).
- Mark the active page with `aria-current="page"` (drives the underline state, not just the visual).
- Tab order: logo → nav links → socials → CTAs.
- Skip-link "Aller au contenu" lives **before** the header in DOM, visible on focus.
