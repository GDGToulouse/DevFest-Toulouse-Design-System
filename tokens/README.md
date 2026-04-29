# Tokens

Machine-readable design tokens, **derived from [`../DESIGN.md`](../DESIGN.md)** (the single source of truth).

## Status

🚧 **Empty for now.** When the export pipeline is wired up (`npx design-md export`), this folder will contain:

| File | Format | Consumer |
|------|--------|----------|
| `tokens.dtcg.json` | [W3C Design Tokens Community Group](https://www.designtokens.org/) | Style Dictionary, Token Studio, generic tooling |
| `tokens.tailwind.js` | Tailwind config fragment | Tailwind v4+ themes |
| `tokens.css` | CSS custom properties | Vanilla CSS, any framework |
| `tokens.scss` | SCSS variables | Sass-based projects |

## Generation (planned)

```bash
# From repo root, once design-md CLI is available
npx design-md export tokens.dtcg.json --format=dtcg
npx design-md export tokens.tailwind.js --format=tailwind
npx design-md export tokens.css --format=css
```

## ⚠️ Do not edit by hand

Once exports are generated, **do not edit files in this folder directly**. Edit `../DESIGN.md`, then regenerate. Any hand-edit will be overwritten by the next export.

While the pipeline is not yet wired, hand-maintained tokens may live here as a stopgap — clearly marked as such in their header.

## Linting

Run before committing token changes:

```bash
npx design-md lint ../DESIGN.md
```

Expected to pass: `broken-ref`, `missing-primary`, `contrast-ratio`, `orphaned-tokens`, `section-order`.
