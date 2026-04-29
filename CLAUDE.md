# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project

Single source of truth for the **DevFest Toulouse** visual identity. The repo serves three audiences in parallel:

1. **Humans** (organizers, sponsors, partners, content creators) — read [`brand/`](brand/) (French prose).
2. **AI agents** (Claude Design, Stitch, code agents) — consume [`DESIGN.md`](DESIGN.md) at the root, written in the [Google Stitch DESIGN.md `alpha` format](https://github.com/google-labs-code/design.md).
3. **App developers** (DevFest Toulouse web/mobile/admin apps) — pull from [`tokens/`](tokens/), [`components/`](components/), [`assets/`](assets/).

The neighbouring repo `../Site-Devfest-Toulouse-2026/` is the first consumer; its `docs/design-system.md` was the source material for this dépôt and is being progressively replaced by references to it.

## Communication

- File contents, commits, branches, identifiers: **English**.
- Conversational replies to the maintainer: **French**.
- Exception: files in [`brand/`](brand/) are written in **French** (their primary audience is French-speaking organizers). Files in [`DESIGN.md`](DESIGN.md), [`tokens/`](tokens/), [`components/`](components/) stay in English (consumed by international tooling and agents).

## How this repo is structured

```
.
├── DESIGN.md             ← Machine-readable spec (Stitch alpha) — single source of truth for tokens
├── brand/                ← Human-facing brand book (FR)
├── tokens/               ← Exports of DESIGN.md tokens (DTCG JSON, Tailwind, CSS vars)
├── components/           ← Per-component specifications (anatomy, states, code refs)
├── assets/               ← Logo (5 declensions × 5 formats), 30 illustrations × 3 colors, fonts, charte PDF
├── examples/             ← Reference mockups (Site 2026 SVG exports)
└── docs/                 ← Integration guides (Claude Design usage, Tailwind setup, etc.)
```

**`DESIGN.md` is the single source of truth for tokens.** Files in `tokens/` are *generated* from it (or kept in sync manually until the export pipeline is wired). When palette / typo / spacing changes, edit `DESIGN.md` first, then propagate.

## DESIGN.md — what to know

- Format: YAML front matter (machine-readable tokens) + 8 markdown sections (human rationale).
- Required section order: **Overview, Colors, Typography, Layout, Elevation & Depth, Shapes, Components, Do's and Don'ts.** Sections may be omitted, but their order when present is enforced by `lint`.
- Token references use `{path.to.token}` (e.g. `{colors.primary}`).
- Component variants (hover, active, pressed) are *separate entries* with related key names — e.g. `button-primary` + `button-primary-hover`. Do not nest variants under a parent.
- Spec status is **`alpha`**; the format may change. Pin the version in front matter and follow upstream releases at [google-labs-code/design.md](https://github.com/google-labs-code/design.md).

## Tooling (planned)

- **`design-md` CLI** (Stitch-provided, run via `npx`): `lint`, `diff`, `export` (Tailwind / DTCG), `spec`. Use it before committing a `DESIGN.md` change.
- **Token export** to `tokens/` will use `design-md export` once the pipeline is set up.
- No build / framework code lives at the root yet — when component implementations land, they will get their own subfolder (e.g. `packages/react/`) with its own README and scripts.

## Common commands

> _To be filled in once the `design-md` CLI pipeline and any package tooling are wired up._

Until then, hand-edit `DESIGN.md` and keep `tokens/` aligned manually.

## Conventions specific to this repo

- **Identity colors are not interchangeable.** "Toulouse" is always terracotta `#EC6839`; "DevFest" is always malachite `#109E6E`; the **primary CTA color** is blue `#507BBD` and is *functional*, not identity. Reject changes that swap these roles.
- **Do not introduce a new hex value without adding a named token to `DESIGN.md`** — orphan colors will be flagged by `lint` and break downstream exports.
- **Do not edit files in `tokens/` by hand once the export pipeline is live.** They are derived from `DESIGN.md`.
- **Brand assets are versioned in this repo** (logo SVG/PNG/EPS, illustrations PNG, charte PDF). They are heavy but the canonical location — do not re-host them in consumer repos.
- **Illustrations are PNG-only today.** A future task is converting the 90 illustration files (30 × 3 colors) to SVG for web use.

## Maintenance note for future Claude instances

When asked to update tokens or add a component:

1. Edit `DESIGN.md` first — it is the source of truth.
2. Update the matching prose in `brand/` (French) so humans stay in sync.
3. Regenerate or update `tokens/` exports (manually until `design-md export` is wired).
4. If a component is added, write `components/<name>.md` with anatomy + states.
5. Run `npx design-md lint DESIGN.md` once the CLI is installed; fix warnings before committing.

When the spec moves from `alpha` to a stable version, bump `version:` in the front matter and review breaking changes from the [upstream changelog](https://github.com/google-labs-code/design.md/releases).
