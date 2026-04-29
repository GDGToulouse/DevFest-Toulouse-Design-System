# UI kit — Site DevFest Toulouse

Recreation of the DevFest Toulouse 2025 marketing site, built from the Figma source (`/Site-web/home/`) and the brand spec.

Open `index.html` for a clickable single-page mockup that demonstrates the full visual vocabulary: header, hero, stats, partners, about, articles, footer.

## Sections present
- Header (sticky, 60 px, shadow-header, nav + socials + CTAs)
- Hero (split layout, wordmark pairing, photo image with hero radius, dual CTAs)
- Statistics encart (floating white card, La Grave illustration peeking)
- Partners (Platinum / Gold / Discovery / Soutien bands per the 2026 4-pack model, croix occitane top-right)
- About (#DevFestToulouse hash card, photo, white description card)
- Articles (4 cards, shadow-card, author caption Bismarck)
- Footer (malachite, radius-3xl, white bottom bar)

## Notes
- Hero photographic image is approximated with a colored gradient (placeholder) — drop in a real DevFest photo via the `.hero-img` background.
- Sponsor cards show "SPONSOR LOGO" placeholders — replace with actual SVG logos when available.
- Click handlers fire toast notifications to demonstrate the interactive surface.
