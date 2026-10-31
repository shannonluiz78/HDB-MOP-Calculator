# Home Equity Studio V4.1 — Approved Landing Page Matching QA

## Design basis
The current homepage desktop presentation uses the exact user-uploaded 1448 × 1086 approved design image, converted to a high-quality embedded WebP so the Singapore skyline, portrait and BTO/SBF image always appear together. The positioned links are actual accessible HTML anchors. At widths below 1101px a mobile/tablet HTML layout is displayed using embedded image assets.

## Checks
- Chromium desktop and responsive previews rendered at widths: 1448, 1280, 1024, 768, 390, and 320px.
- All visible images successfully decoded in Chromium at all tested widths.
- No horizontal overflow or JavaScript page errors detected at tested widths.
- Desktop main CTA, desktop header navigation, BTO/SBF feature, three journey cards, and WhatsApp calls-to-action have working anchor destinations.
- Additional pages `sell-upgrade.html`, `bto-sbf.html`, and `privacy.html` are included in the package with `assets/`.
- **The financial calculator was not changed in this revision**, so the previous V4.1 calculation and PDF functionality remains as delivered. These functions were not independently rerun in this homepage-focused iteration.

## Important implementation tradeoff
To reproduce the approved image exactly and avoid missing skyline imagery again, the desktop layout is image-backed. Desktop headline and some small printed labels are within the approved artwork and are therefore **not individually editable webpage text**. The interactive elements are real HTML links, and mobile/tablet use live HTML text, but a full semantic/SEO-optimized HTML reconstruction is recommended before final public production if frequent copy editing or accessibility/SEO is a priority.

## Publishing
Upload `index.html`, `sell-upgrade.html`, `bto-sbf.html`, `privacy.html`, and the `assets/` folder together to the Vercel preview root. Do not replace production without client acceptance and testing on real iOS Safari.
