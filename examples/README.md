# Examples

Reference mockups showing the design system in use. Useful as **visual context for AI agents** (Claude Design, Stitch) when generating new mockups, and as a **fidelity checklist** for human implementers.

## Status

✅ **Populated**:
- [`site-2026/`](site-2026/) — 12 desktop mockups exported from the Figma site (snapshot)
- [`preview/`](preview/) — 22 Stitch-style preview cards (one HTML per design aspect)
- [`ui-kit-site/`](ui-kit-site/) — working HTML prototype of the marketing site, single page

> ⚠️ **`site-2026/` mockups still show the 2025 sponsor color model** (Gold yellow `#FFD428`, Silver/Other pink `#EE7CAD`). The 2026 4-pack model (Platinum Malachite / Gold Orange / Discovery Purple / Soutien Gray) is the canonical reference — see [`../DESIGN.md`](../DESIGN.md) and [`../brand/colors.md`](../brand/colors.md). Re-export from Figma when the Figma file is updated.

> 💡 `home.svg` is heavy (~29 MB) because it embeds raster PNG illustrations. A future optimization is to swap embedded PNGs for `<image>` references to [`../assets/illustrations/`](../assets/illustrations/).

## Content

Site DevFest Toulouse 2026 — desktop mockups (1440 px), exported as SVG from Figma.

| Page | File | Height | What it demonstrates |
|------|------|--------|----------------------|
| Home | `site-2026/home.svg` | 6436 px | Hero, statistics, sponsors, about, articles list |
| Conferences list | `site-2026/conferences.svg` | 1842 px | Session card grid |
| Conference detail | `site-2026/conference.slug.svg` | 1842 px | Session detail layout |
| Speakers list | `site-2026/speakers.svg` | 1842 px | Speaker card grid |
| Speaker detail | `site-2026/speaker.slug.svg` | 1842 px | Speaker profile (photo, bio, sessions) |
| Partners list | `site-2026/partners.svg` | 1842 px | Sponsor tiers |
| Partner detail | `site-2026/partner.slug.svg` | 1408 px | Two-column detail |
| News list | `site-2026/actualites.svg` | 1842 px | Article card grid |
| Article detail | `site-2026/actualite.slug.svg` | 2119 px | Rich text article |
| Contact | `site-2026/contact.svg` | 1949 px | Form layout |
| Code of conduct | `site-2026/code-de-conduite.svg` | 2119 px | Long-form policy page |
| Legal | `site-2026/mentions-legales.svg` | 2119 px | Long-form legal page |

## Source

- Figma file: [DevFestToulouse-2025](https://www.figma.com/design/5dw9ggMfrdFrB9qEKYvHH6/DevFestToulouse-2025?node-id=22-499)
- Site spec (FR): [`../../Site-Devfest-Toulouse-2026/docs/maquettes-figma.md`](../../Site-Devfest-Toulouse-2026/docs/maquettes-figma.md)

## Why this matters for AI agents

When a tool like Claude Design is asked to generate a new page (e.g. an FAQ or a 404), it produces drastically better results when it can see existing pages of the same brand. These SVGs are the visual companion to `DESIGN.md`'s tokens.
