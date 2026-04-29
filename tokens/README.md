# Tokens

Machine-readable design tokens, **derived from [`../DESIGN.md`](../DESIGN.md)** (the single source of truth).

## Available now

| File | Format | Consumer |
|------|--------|----------|
| [`colors_and_type.css`](colors_and_type.css) | CSS custom properties + `@font-face` for self-hosted Google Sans | Direct `<link>` from any HTML page, the UI kit, prototypes |

`colors_and_type.css` exposes every DESIGN.md token as a CSS variable: identity colors, sponsor tier colors (Platinum / Gold / Discovery / Soutien — 2026 model), typography scale (with Medium 500), spacing, radii, shadows, motion easing/durations. It also contains an opt-in `@font-face` block pointing at `../assets/fonts/`; comment it out if you load Google Sans from the Google Fonts CDN.

## Planned

When the [`design-md` CLI](https://github.com/google-labs-code/design.md) export pipeline is wired up (`npx design-md export`), this folder will also contain:

| File | Format | Consumer |
|------|--------|----------|
| `tokens.dtcg.json` | [W3C Design Tokens Community Group](https://www.designtokens.org/) | Style Dictionary, Token Studio, generic tooling |
| `tokens.tailwind.js` | Tailwind config fragment | Tailwind v4+ themes |
| `tokens.scss` | SCSS variables | Sass-based projects |

## Generation (planned)

```bash
# From repo root, once design-md CLI is available
npx design-md export tokens.dtcg.json --format=dtcg
npx design-md export tokens.tailwind.js --format=tailwind
npx design-md export tokens.css --format=css
```

## ⚠️ Editing rules

Once the export pipeline is in place, **do not edit generated files directly**. Edit `../DESIGN.md` then regenerate. Hand-edits would be overwritten by the next export.

`colors_and_type.css` is currently **hand-maintained** as a stopgap — keep it in sync with `../DESIGN.md` until `design-md export` is wired up.

## Linting

Run before committing token changes:

```bash
npx design-md lint ../DESIGN.md
```

Expected to pass: `broken-ref`, `missing-primary`, `contrast-ratio`, `orphaned-tokens`, `section-order`.
