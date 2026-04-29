# Components

Per-component specifications. Each component gets its own markdown file with:

1. **Anatomy** — labelled diagram of the visual structure
2. **Tokens used** — references to `DESIGN.md` (e.g. `{colors.primary}`, `{rounded.s}`)
3. **States** — default, hover, active, disabled, focus
4. **Variants** — sizes (Small / Medium / Large), styles (Primary / Secondary)
5. **Do / Don't**
6. **Reference implementation** — minimal HTML/CSS snippet, framework-agnostic

## Status

🟢 **P0 components specified.** P1 / P2 components still to be written.

## Components à documenter

Liste issue des maquettes du site DevFest Toulouse 2026. À transformer en fichiers `<name>.md` dans ce dossier au fur et à mesure.

| Composant | Priorité | Fichier | Status |
|-----------|----------|---------|--------|
| Button (Primary / Secondary, Small / Large) | P0 | [`button.md`](button.md) | ✅ |
| Header | P0 | [`header.md`](header.md) | ✅ |
| Footer | P0 | [`footer.md`](footer.md) | ✅ |
| Article Card (300×400 px) | P0 | [`card-article.md`](card-article.md) | ✅ |
| Partner Card Platinum (340×481 px) | P1 | `card-partner-platinum.md` | ⏳ |
| Partner Card Gold/Other (340×240 px) | P1 | `card-partner-gold.md` | ⏳ |
| Hero Section | P1 | `hero.md` | ⏳ |
| Statistics Block | P1 | `stat-block.md` | ⏳ |
| Breadcrumb | P2 | `breadcrumb.md` | ⏳ |
| Form Inputs (text, select, textarea, label) | P2 | `form-inputs.md` | ⏳ |
| Socials | P2 | `socials.md` | ⏳ |
| Speaker Card | P2 | `card-speaker.md` | ⏳ |
| Session Card | P2 | `card-session.md` | ⏳ |

## Source visuelle

Les maquettes Figma sont la référence visuelle. Voir [`../examples/`](../examples/) pour les exports SVG locaux.

## Convention de fichier

Chaque fichier `<name>.md` suit ce squelette :

```markdown
# Component Name

> Token group: `components.<name>` in [`../DESIGN.md`](../DESIGN.md)

## Anatomy
…

## Tokens
- backgroundColor: `{colors.primary}`
- textColor: `{colors.on-primary}`
- …

## States
| State | Tokens |
|-------|--------|
| Default | … |
| Hover | … |
| Active | … |
| Disabled | … |

## Variants
…

## Do / Don't
…

## Reference HTML
```html
…
```
```
