# Hero

The Hero is the **first impression** of the site, used only on the home page. It carries the year's announcement (date, place, two CTAs) and the brand wordmark in its full identity colors.

It is **not** a generic banner — every page has a breadcrumb, but only the home has the Hero. Internal pages start with their `<h1>` directly.

## Anatomy

```
┌──────────────────────────────────────────────────────────────────────────────────┐
│                                                                                  │
│  ┌─────────────────────────┐  ┌──────────────────────────────────────────┐       │
│  │  DevFest Toulouse       │  │                                          │       │
│  │  ─────  ─────────       │  │            Hero image                    │       │
│  │  malachite  terracotta  │  │            (1024 × 768)                  │       │
│  │  display 112 px         │  │            radius hero (64) on left      │       │
│  └─────────────────────────┘  │            corners only                  │       │
│                                │            overlay 30 % black            │       │
│  La conférence Toulousaine    │                                          │       │
│  par les **devs** et pour     │                                          │       │
│  les **devs**.                │                                          │       │
│                                │                                          │       │
│  📅 13 novembre 2026 · Diagora                                            │       │
│                                                                                  │
│  ┌────────────────────────┐  ┌────────────────────────┐                          │
│  │  Devenir partenaire    │  │   Proposer un talk     │                          │
│  └────────────────────────┘  └────────────────────────┘                          │
│       Primary, Large            Secondary, Large                                  │
└──────────────────────────────────────────────────────────────────────────────────┘
```

The Hero is a **two-column desktop layout**:

| Left column (~50 %) | Right column (~50 %) |
|---------------------|----------------------|
| Title block (DevFest + Toulouse, stacked) | Hero image with rounded-hero on the **left corners only** |
| Description (multi-line, blocks of white with rounded bottom-right) | Subtle dark overlay (30 % black) for legibility of any overlaid text |
| Date + place line | (image bleeds to the right edge of the viewport) |
| CTA pair (Primary + Secondary, Large) | |

## Tokens

| Property | Token / Value |
|----------|---------------|
| Title — "DevFest" | `{typography.display}` (112 px Bold), `{colors.tertiary}` (`#109E6E` malachite) |
| Title — "Toulouse" | `{typography.display}` (112 px Bold), `{colors.secondary}` (`#EC6839` terracotta) |
| Description | `{typography.description}` (32 px Regular), `{colors.on-surface}` |
| Emphasised words in description | `{typography.description-bold}` (32 px Bold) |
| Date / place line | `{typography.body}` (16 px Regular), `{colors.gray}` |
| Hero image | rounded-left only: `border-radius: 64px 0 0 64px` (= `{rounded.hero}` on top-left and bottom-left) |
| Image overlay | `rgba(29,29,27,0.30)` |
| Title background | white blocks, `border-radius: 0 0 24px 0` (= `{rounded.2xl}` bottom-right only) |

## Layout

- Total height: ~850 px desktop.
- Title block sits anchored to the **bottom-left** of its column (it grows upward as text wraps).
- "DevFest" and "Toulouse" are on **two separate lines**, never on one — the rhythm is part of the brand.
- Description is composed of small white pill-blocks (each block is a separate text line with its own rounded bottom-right corner).
- CTAs sit at the bottom-left, separated by `space-2xl` (32 px).

## States

The hero is mostly static. Two interactive states:

| State | Visual |
|-------|--------|
| Image hover (whole hero) | no change — the image is decorative, not a link |
| CTA hover | as `button-primary-large` and `button-secondary-large` (see [button.md](button.md)) |

## Conditional content

The home hero has **three modes** depending on the year's lifecycle (per `Site-Devfest-Toulouse-2026/docs/fonctionnalites-2026.md`):

| Mode | When | Title block | Date line | CTAs |
|------|------|-------------|-----------|------|
| **Preparation** | Default, before announcement | "DevFest Toulouse" | "Édition 2026 en préparation" | "Devenir partenaire" + "Proposer un talk" |
| **Announcement** | Date + place locked | "DevFest Toulouse" | "13 novembre 2026 · Diagora Labège" | "Réserver ma place" + "Proposer un talk" |
| **See you next year** | After the event | "DevFest Toulouse" | "Rendez-vous en 2027" | "Voir les replays" + (Secondary muted) |

The wordmark colors and image stay identical across modes — only date copy and CTAs change.

## Do / Don't

✅ **Do**

- Always use **two CTAs** — Primary + Secondary, equal weight.
- Keep the title on **two lines**, malachite then terracotta.
- Use a real photo of the event for the hero image (last edition's atmosphere shot is preferred).
- Crop the image so the focal point sits in the **right-third** — the left-third is covered by the title overlap.

❌ **Don't**

- Don't put the wordmark over the image (white-on-photo). It belongs on the white left column.
- Don't use a single CTA — the pair is part of the design.
- Don't replace the photo with an illustration. Illustrations live elsewhere ([illustrations.md](../brand/illustrations.md)).
- Don't reverse the column order (image left, text right) — the brand reads left-to-right title → image.

## Reference HTML

```html
<section class="dft-hero" aria-labelledby="hero-title">
  <div class="dft-hero__text">
    <h1 id="hero-title" class="dft-hero__title">
      <span class="dft-hero__title-devfest">DevFest</span>
      <span class="dft-hero__title-toulouse">Toulouse</span>
    </h1>
    <p class="dft-hero__description">
      La conférence Toulousaine par les <strong>devs</strong>
      et pour les <strong>devs</strong>.
    </p>
    <p class="dft-hero__when">📅 13 novembre 2026 · Diagora Labège</p>
    <div class="dft-hero__cta">
      <a href="/partenaires" class="dft-button dft-button--primary dft-button--large">Devenir partenaire</a>
      <a href="/cfp"          class="dft-button dft-button--secondary dft-button--large">Proposer un talk</a>
    </div>
  </div>
  <div class="dft-hero__media" aria-hidden="true">
    <img src="/assets/photos/hero-2025.jpg" alt="">
  </div>
</section>
```

## Accessibility

- The hero is a `<section>` with `aria-labelledby` pointing to the title.
- "DevFest Toulouse" is one `<h1>` (the page's only one); the two color spans are inside it.
- Image has `alt=""` because it is decorative atmosphere — the title supplies the page's accessible name.
- Date line uses an emoji `📅` for visual flair; if accessibility audits flag it, replace with a Font Awesome `fa-calendar-days` icon and `aria-hidden="true"`.
