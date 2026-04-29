# Assets

Brand binaries — the canonical location. Consumer apps reference this folder; do **not** duplicate these files into other repos.

## Status

🚧 **Empty for now.** Files are to be copied from the existing site repo `../../Site-Devfest-Toulouse-2026/docs/assets/`.

## Target structure

```
assets/
├── charte-graphique-2024.pdf       ← Reference PDF (216 KB)
├── logo/
│   ├── Principal/                   ← Full logo (DevFest + Toulouse wordmark)
│   │   ├── RVB/svg/                 ← Web-ready SVGs (5 variants)
│   │   ├── RVB/png/
│   │   └── CMJN/eps/                ← Print-ready EPS / PDF
│   ├── Secondaire/                  ← Minimal logo (favicon, avatar)
│   │   ├── RVB/svg/
│   │   └── …
│   ├── Avatar_400x400px.png         ← Square avatar for socials
│   └── favicon/                     ← favicon.ico, apple-touch-icon, …
├── illustrations/
│   ├── Bismarck/                    ← 30 PNG (#B94420)
│   ├── TerreCuite/                  ← 30 PNG (#EC6839)
│   └── Malachite/                   ← 30 PNG (#109E6E)
└── fonts/
    ├── GoogleSans-Regular.woff2
    ├── GoogleSans-Bold.woff2
    └── GoogleSans-Italic.woff2
```

## Logo declensions

5 variants × 5 file formats (SVG, PNG, JPG, EPS, PDF), in 2 color spaces (RVB / CMJN). See [`../brand/logo.md`](../brand/logo.md) for usage rules.

## Illustrations

30 hand-drawn illustrations × 3 colors = 90 PNG files. Catalogue in [`../brand/illustrations.md`](../brand/illustrations.md).

> 🔧 **Future task** — convert to SVG for web (lighter, scalable, recolorable via CSS).

## Fonts

**Google Sans** is the brand typeface. As of November 2025 it ships under SIL OFL. The `.woff2` files in [`fonts/`](fonts/) (once added) are bundled for self-hosting; the [Google Fonts CDN link](https://fonts.google.com/specimen/Google+Sans) is also acceptable.

**CCSignLanguage** is print/social only — its files are not bundled here.

## Copying assets from the existing site

Until the canonical migration is done, the source-of-truth files live in `../../Site-Devfest-Toulouse-2026/docs/assets/`. To populate this folder, copy from there:

```bash
# From this repo's root, on Windows (PowerShell):
robocopy ..\Site-Devfest-Toulouse-2026\docs\assets assets /E /XD .git
```

After copying, update this README to remove the "🚧 Empty for now" warning and check in the binaries.

## Licence

- Logo and illustrations: © DevFest Toulouse / GDG Toulouse — usage by partners and contributors of the event is granted within the rules described in [`../brand/`](../brand/).
- Google Sans: SIL OFL.
- Font Awesome (referenced for functional icons, not bundled): see [fontawesome.com/license/free](https://fontawesome.com/license/free).
