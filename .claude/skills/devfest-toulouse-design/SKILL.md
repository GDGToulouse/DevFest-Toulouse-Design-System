---
name: devfest-toulouse-design
description: Use this skill to generate well-branded interfaces and assets for DevFest Toulouse, either for production or throwaway prototypes/mocks. Contains essential design guidelines, colors, type, fonts, assets, and UI kit components for prototyping.
user-invocable: true
---

Read [`/README.md`](../../../README.md) and [`/DESIGN.md`](../../../DESIGN.md) at the repo root first — they are the entry points.

If creating visual artifacts (slides, mocks, throwaway prototypes), copy assets out and create static HTML files. Always link [`/tokens/colors_and_type.css`](../../../tokens/colors_and_type.css) — it exposes every DESIGN.md token as a CSS variable and includes an opt-in `@font-face` block for self-hosted Google Sans (default loading is the Google Fonts CDN). Use Font Awesome Free for functional icons. Pick illustrations from [`/assets/illustrations/{TerreCuite,Bismarck,Malachite}/`](../../../assets/illustrations/) — never redraw them.

If working on production code, copy what you need from [`/assets/`](../../../assets/), [`/tokens/`](../../../tokens/) and consult per-component specs in [`/components/`](../../../components/).

If the user invokes this skill without other guidance, ask what they want to build or design (audience / tone / FR vs EN / surface = site / slides / social), then act as an expert designer who outputs HTML artifacts *or* production code.

## Hard rules to enforce

- **Wordmark pairing.** "DevFest" is **always** Malachite `#109E6E`. "Toulouse" is **always** Terracotta `#EC6839`. Never swap.
- **Action vs identity.** Blue `#507BBD` is the **primary CTA** color — functional, not identity. Don't use it as section background or heading color.
- **Sponsor tiers (2026 model).** 4 packs with fixed banner colors: **Platinum** Malachite `#109E6E`, **Gold** Orange `#FFAB40`, **Discovery** Purple `#7E60C9` (reserved for new sponsors / startups / TPE / non-profits), **Soutien** Gray `#CCCCCC` (no stand). Banner labels are uppercase white; **except** Gold and Soutien which need ink-on-color labels for WCAG.
- **Typography.** Google Sans only on web — Regular 400, Medium 500, Bold 700, with italics. CCSignLanguage is print/social only.
- **Italic** is reserved for sponsor Platinum baselines. For emphasis in body text use **Bold** (or Medium when Bold is too strong).
- **No emoji** in formal/official copy. **No "TOULOUSE" in caps** inside body text (reserved to the logo).
- **Illustrations** only in Bismarck / Terracotta / Malachite. Never recolor outside this set.
- **Roundedness.** Interactive elements never use radius 0 — minimum is `radius-s` 12 px.
- **Shadows** always cast in ink `#1D1D1B` at low alpha — never gray, never colored.
- **Motion.** One easing curve `cubic-bezier(0.2, 0.6, 0.2, 1)`, durations 150 ms (hover) / 200 ms (lift) / 400 ms (rare). No bounce, no spring. Honor `prefers-reduced-motion`.
- **Social icons order**, everywhere: LinkedIn → YouTube → X → Bluesky.
