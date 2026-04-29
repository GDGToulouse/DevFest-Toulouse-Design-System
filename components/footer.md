# Footer

Token group: `components.footer` in [`../DESIGN.md`](../DESIGN.md).

The footer is the **emotional sign-off** of every page. It is the only large malachite surface in the layout, and it carries the tagline "Sans bug depuis 2016". It must feel warm and rounded — the opposite of a corporate footer.

## Anatomy

```
┌────────────────────────────────────────────────────────────────────┐
│                                                                    │
│  [Full logo]               Navigation     Écosystèmes    Éditions  │
│  333×150 px                  link 1         link 1        link 1   │
│                              link 2         link 2        link 2   │
│  Suivez l'aventure :         link 3         link 3        link 3   │
│  [in] [▶] [𝕏] [bs]                                                │
│                                                                    │
│      [Contactez nous] (Small Primary, centered under socials)      │
│                                                                    │
│  ┌──────────────────────────────────────────────────────────────┐ │
│  │ Sans bug depuis 2016    Mentions légales · Code · Plan       │ │
│  └──────────────────────────────────────────────────────────────┘ │
│                                                                    │
└────────────────────────────────────────────────────────────────────┘
   ↑ background: malachite     ↑ inner bar: white 75% opacity
   ↑ outer radius: 32 px       ↑ inner bar radius: 18 px
```

## Tokens

| Property | Token | Value |
|----------|-------|-------|
| backgroundColor | `{colors.tertiary}` | `#109E6E` (malachite) |
| textColor | `{colors.on-tertiary}` | `#FFFFFF` |
| linkColor | `{colors.link-on-dark}` | `#FDF0EB` (off-white) |
| rounded | `{rounded.3xl}` | 32 px |
| boxShadow | `shadow-section` (see DESIGN.md § Elevation & Depth) | `0 4px 64px 4px rgba(29,29,27,0.12)` |
| height | — | ~496 px (varies with column content) |

| Inner "tagline bar" | Value |
|---------------------|-------|
| backgroundColor | `rgba(255,255,255,0.75)` |
| textColor | `{colors.on-surface}` (`#1D1D1B`) |
| rounded | `{rounded.l}` (18 px) |

## Layout

- Container width: matches the page, with **lateral padding `100px`**.
- Top padding inside the malachite block: `space-4xl` (64 px).
- Bottom padding: `space-2xl` (32 px) above the inner tagline bar.

### Top section — 2-column inversion grid

| Left column (40 % width) | Right column (60 % width, 3 sub-columns) |
|--------------------------|------------------------------------------|
| Full DevFest Toulouse logo (333 × 150 px), Brique Light Mode variant | "Navigation", "Écosystèmes tech", "Éditions précédentes" |
| Caption "Suivez l'aventure en ligne :" | Each sub-column: heading + 3-6 links |
| 4 social icons (48 px) | |
| "Contactez nous" CTA (Small Primary), centered below socials | |

### Footer column headings

`{typography.footer-heading}` → Google Sans Bold 20 px, line-height 1.3.

### Footer link text

`{typography.footer-text}` → Google Sans Regular 16 px, line-height 1.6, color off-white `#FDF0EB`.

### Tagline bar (bottom)

- Spans the full width inside the lateral padding.
- Left: tagline "Sans bug depuis 2016" — `{typography.body}` ink color.
- Right: 3 inline links (Mentions légales · Code de conduite · Plan du site), separated by `·` middle-dots, also ink color.

## States

| Element | State | Visual |
|---------|-------|--------|
| Footer link | hover | underline appears, color stays off-white |
| Footer link | focus (keyboard) | 2 px terracotta outline, offset 2 px |
| Social icon | hover | scale 1.1, transition `var(--duration-fast) var(--ease-default)` (150 ms) |
| CTA | as `button-primary` (small) | see [button.md](button.md) |
| Tagline-bar link | hover | underline, color stays ink |

## Do / Don't

✅ **Do**

- Use the **full Brique Light Mode logo** (333×150 px) here — the header takes the minimal logo, the footer takes the full one.
- Keep social icons large (**48 px**) — the footer is where users go *looking* for social links.
- Keep the link order in the columns stable across the year (don't shuffle when adding new pages — append to the bottom).

❌ **Don't**

- Don't darken the malachite or shift it to a more "corporate" gradient — the flat `#109E6E` is the brand.
- Don't put the tagline in malachite text on the malachite background. It lives in the white tagline bar.
- Don't add a newsletter form to the footer; if a newsletter exists, it gets its own section above the footer.
- Don't put an illustration in the footer (the croix occitane lives in the sponsors section, La Grave in the stats — neither belongs here).

## Reference HTML

```html
<footer class="dft-footer" role="contentinfo">
  <div class="dft-footer__top">
    <div class="dft-footer__brand">
      <img
        src="/assets/logo/Principal/RVB/svg/LOGO_DevFest_BriqueLightMode.svg"
        alt="DevFest Toulouse"
        width="333" height="150">
      <p class="dft-footer__caption">Suivez l'aventure en ligne :</p>
      <ul class="dft-footer__socials">
        <li><a href="…" aria-label="LinkedIn"><i class="fa-brands fa-linkedin fa-2x"></i></a></li>
        <li><a href="…" aria-label="YouTube"><i class="fa-brands fa-youtube fa-2x"></i></a></li>
        <li><a href="…" aria-label="X"><i class="fa-brands fa-x-twitter fa-2x"></i></a></li>
        <li><a href="…" aria-label="Bluesky"><i class="fa-brands fa-bluesky fa-2x"></i></a></li>
      </ul>
      <button class="dft-button dft-button--primary dft-button--small">Contactez nous</button>
    </div>

    <nav class="dft-footer__nav" aria-label="Navigation du pied de page">
      <section>
        <h3>Navigation</h3>
        <ul>
          <li><a href="/programme">Programme</a></li>
          <li><a href="/speakers">Speakers</a></li>
          <li><a href="/partenaires">Partenaires</a></li>
          <li><a href="/actualites">Actualités</a></li>
        </ul>
      </section>
      <section>
        <h3>Écosystèmes tech</h3>
        <ul>
          <li><a href="…">ToulouseTech</a></li>
          <li><a href="…">CloudToulouse</a></li>
          <li><a href="…">GDG Toulouse</a></li>
        </ul>
      </section>
      <section>
        <h3>Éditions précédentes</h3>
        <ul>
          <li><a href="/2025">2025</a></li>
          <li><a href="/2024">2024</a></li>
          <li><a href="/historique">Historique complet</a></li>
        </ul>
      </section>
    </nav>
  </div>

  <div class="dft-footer__tagline">
    <p>Sans bug depuis 2016</p>
    <ul>
      <li><a href="/mentions-legales">Mentions légales</a></li>
      <li><a href="/code-de-conduite">Code de conduite</a></li>
      <li><a href="/plan-du-site">Plan du site</a></li>
    </ul>
  </div>
</footer>
```

## Accessibility

- Use `<footer role="contentinfo">` (the role is implicit but explicit here for older AT).
- Each column heading is `<h3>` (the page `<h1>` is the page title; the footer never has an `<h2>` — it is informational, not a section).
- Social links have `aria-label` (no visible text).
- The logo image carries `alt="DevFest Toulouse"` because here it is **the only signifier of the brand** in the footer (unlike the header, where the link `aria-label` provides the name).
